# Copyright 2018 Endless Mobile, Inc.

javascript_tests = [
	'ekncontent/testArticleObjectModel.js',
	'ekncontent/testContentObjectModel.js',
	'ekncontent/testDatadir.js',
	'ekncontent/testDomain.js',
	'ekncontent/testEngine.js',
	'ekncontent/testAudioObjectModel.js',
	'ekncontent/testDictionaryObjectModel.js',
	'ekncontent/testImageObjectModel.js',
	'ekncontent/testMediaObjectModel.js',
	'ekncontent/testObjectModel.js',
	'ekncontent/testQueryObject.js',
	'ekncontent/testQueryResults.js',
	'ekncontent/testSetObjectModel.js',
	'ekncontent/testUtils.js',
	'ekncontent/testVideoObjectModel.js',
]

jasmine = find_program('jasmine')
test_runner = find_program('./tap.py')
include_path = '@0@:@1@'.format(meson.source_root(), meson.build_root())
test_content_path = join_paths(meson.current_source_dir(), 'testcontent')
tests_environment = environment()
tests_environment.set('GJS_PATH', include_path)
tests_environment.prepend('GI_TYPELIB_PATH', meson.current_build_dir())
tests_environment.prepend('LD_LIBRARY_PATH', meson.current_build_dir())
tests_environment.set('G_TEST_SRCDIR', meson.current_source_dir())
tests_environment.set('G_TEST_BUILDDIR', meson.current_build_dir())
tests_environment.prepend('XDG_DATA_DIRS', test_content_path)
tests_environment.set('LC_ALL', 'C')

args = [jasmine.path(), '--no-config', '--tap']
if (jasmine_report_argument != '')
    args += [jasmine_report_argument]
endif

foreach test_file : javascript_tests
    srcdir_file = join_paths(meson.current_source_dir(), test_file)
    test(test_file, test_runner, env: tests_environment,
        args: args + [srcdir_file])
endforeach


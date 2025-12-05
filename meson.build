project('struct2json',
        ['c'],
        version:'1.0.0')

pkg = import('pkgconfig')

if get_option('buildtype') == 'debug'
  add_project_arguments(['-ggdb',
                         '-g3',
                         '-Og',
                        ], language: ['c'])
else
  add_project_arguments(['-Os'], language: ['c'])
endif

struct2json_srcs = [
  './cJSON/cJSON.c',
  './cJSON/cJSON_Utils.c',
  './struct2json/src/s2j.c',
]

struct2json_headers = [
  './cJSON/cJSON_Utils.h',
  './cJSON/cJSON.h',
  './struct2json/inc/s2j.h',
  './struct2json/inc/s2jdef.h',
]

struct2json_deps = []

incdir = include_directories('cJSON', 'struct2json/inc')

libstruct2json = static_library('struct2json',
                                struct2json_srcs,
                                include_directories: [incdir],
                                dependencies: struct2json_deps,
                                install: true)

install_headers(struct2json_headers, install_dir: 'include')

pkg.generate(libstruct2json,
             name:'struct2json',
             description: 'struct to json',
             version:'1.0.0')

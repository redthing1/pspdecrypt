project('pspdecrypt', ['c', 'cpp'],
  version : '1.0',
  default_options : ['warning_level=3', 'cpp_std=c++11']
)

# find dependencies
openssl_dep = dependency('openssl', version : '>=1.1.0', modules : ['crypto'])
zlib_dep = dependency('zlib')

# compiler flags
add_project_arguments('-O3', language : ['c', 'cpp'])

# source files
libkirk_sources = run_command('sh', '-c', 'ls libkirk/*.c').stdout().strip().split('\n')

pspdecrypt_sources = [
  'libLZR.c',
  'kl4e.c',
  'common.cpp',
  'syscon_ipl_keys.c',
  'ipl_decrypt.cpp',
  'pspdecrypt_lib.cpp',
  'PrxDecrypter.cpp',
  'pspdecrypt.cpp',
  'PsarDecrypter.cpp'
]
pspdecrypt_sources += libkirk_sources

executable(
  'pspdecrypt',
  pspdecrypt_sources,
  dependencies : [openssl_dep, zlib_dep],
)
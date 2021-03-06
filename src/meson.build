# libc src/ meson build

# Flags required by gdtoa
gdtoa_compiler_flags = [
	'-DNO_ERRNO',
	'-DIFNAN_CHECK',
	'-DGDTOA_NO_ASSERT',
	'-DNO_FENV_H'
]

ctype_files = [
	'ctype/isalnum.c',
	'ctype/isalpha.c',
	'ctype/isascii.c',
	'ctype/isblank.c',
	'ctype/iscntrl.c',
	'ctype/isdigit.c',
	'ctype/isgraph.c',
	'ctype/islower.c',
	'ctype/isprint.c',
	'ctype/ispunct.c',
	'ctype/isspace.c',
	'ctype/isupper.c',
	'ctype/isxdigit.c',
	'ctype/toascii.c',
	'ctype/tolower.c',
	'ctype/toupper.c'
]

gdtoa_files = [
	'gdtoa/src/dmisc.c',
	'gdtoa/src/dtoa.c',
	'gdtoa/src/g__fmt.c',
	'gdtoa/src/g_ddfmt.c',
	'gdtoa/src/g_dfmt.c',
	'gdtoa/src/g_ffmt.c',
	'gdtoa/src/g_Qfmt.c',
	'gdtoa/src/g_xfmt.c',
	'gdtoa/src/g_xLfmt.c',
	'gdtoa/src/gdtoa.c',
	'gdtoa/src/gethex.c',
	'gdtoa/src/gmisc.c',
	'gdtoa/src/hd_init.c',
	'gdtoa/src/hexnan.c',
	'gdtoa/src/misc.c',
	'gdtoa/src/smisc.c',
	'gdtoa/src/strtod.c',
	'gdtoa/src/strtodg.c',
	'gdtoa/src/strtodI.c',
	# Below is an alternative, we are not using it
	#'gdtoa/src/strtodnrp.c',
	'gdtoa/src/strtof.c',
	'gdtoa/src/strtoId.c',
	'gdtoa/src/strtoIdd.c',
	'gdtoa/src/strtoIf.c',
	'gdtoa/src/strtoIg.c',
	'gdtoa/src/strtoIQ.c',
	'gdtoa/src/strtoIx.c',
	'gdtoa/src/strtoIxL.c',
	'gdtoa/src/strtopd.c',
	'gdtoa/src/strtopdd.c',
	'gdtoa/src/strtopf.c',
	'gdtoa/src/strtopQ.c',
	'gdtoa/src/strtopx.c',
	'gdtoa/src/strtopxL.c',
	'gdtoa/src/strtord.c',
	'gdtoa/src/strtordd.c',
	'gdtoa/src/strtorf.c',
	'gdtoa/src/strtorQ.c',
	'gdtoa/src/strtorx.c',
	'gdtoa/src/strtorxL.c',
	'gdtoa/src/sum.c',
	'gdtoa/src/ulp.c'
]

stdlib_files = [
	'stdlib/abs.c',
	'stdlib/atof.c',
	'stdlib/atoi.c',
	'stdlib/atol.c',
	'stdlib/atoll.c',
	'stdlib/bsearch.c',
	'stdlib/calloc.c',
	'stdlib/div.c',
	'stdlib/heapsort_r.c',
	'stdlib/heapsort.c',
	'stdlib/imaxabs.c',
	'stdlib/imaxdiv.c',
	'stdlib/labs.c',
	'stdlib/ldiv.c',
	'stdlib/llabs.c',
	'stdlib/lldiv.c',
	'stdlib/qsort_r.c',
	'stdlib/qsort.c',
	'stdlib/rand.c',
	'stdlib/realloc.c',
	'stdlib/strtol.c',
	'stdlib/strtoll.c',
	'stdlib/strtoull.c',
]

string_files = [
	'string/memcmp.c',
	'string/memcpy.c',
	'string/memmem.c',
	'string/memmove.c',
	'string/memrchr.c',
	'string/memset.c',
	'string/strcat.c',
	'string/strchr.c',
	'string/strchrnul.c',
	'string/strcmp.c',
	'string/strcpy.c',
	'string/strdup.c',
	'string/strlen.c',
	'string/strncat.c',
	'string/strncmp.c',
	'string/strncpy.c',
	'string/strndup.c',
	'string/strnlen.c',
	'string/strnstr.c',
	'string/strrchr.c',
	'string/strstr.c',
	'string/strtok.c'
]

support_files = [
	'support/fls.c',
	'support/flsl.c',
	'support/flsll.c'
]

libc = static_library(
	'c',
	[ctype_files, gdtoa_files, stdlib_files, string_files, support_files],
	c_args: [stdlib_compiler_flags, gdtoa_compiler_flags],
	include_directories: [libc_includes, arch_include]
)

if meson.is_cross_build()
	libc_native = static_library(
		'c_native',
		[ctype_files, gdtoa_files, stdlib_files, string_files, support_files],
		c_args: [stdlib_compiler_flags, gdtoa_compiler_flags],
		include_directories: [libc_includes, arch_include],
		native: true
	)
endif

libc_dep = declare_dependency(
	link_with: libc,
	include_directories: [libc_includes, arch_include],
	compile_args: stdlib_compiler_flags,
)

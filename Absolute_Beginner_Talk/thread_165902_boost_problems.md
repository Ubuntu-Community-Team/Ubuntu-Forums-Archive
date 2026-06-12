---
title: "boost problems"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by shroffg on 2006-04-25
I am an Ubuntu/Debian n00b.

I installed libboost and bjam packages from the Synaptics Package Manager and tried to compile a new program which uses one of the boost libraries with it. But I get compile errors which indicate missing libstdc++ files. I checked my system and libstdc++ is indeed installed. 

After some searching on boost forums, I found out that boost needs 
glibc-headers and glibc-kernheaders installed. However I don't see them listed in the packages in Synaptic Package Manager.

Any help would be appreciated.

Here are the compile errors (truncated for brevity):

```
pshroff@pshroff-ubuntu:~/projects/try-boost$ g++-4.0 books.cpp
In file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++config.h:35,
                 from /usr/include/c++/4.0.2/string:44,
                 from ./books.hpp:10,
                 from books.cpp:6:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/os_defines.h:39:22: error: features.h: No such file or directory
In file included from /usr/include/c++/4.0.2/bits/char_traits.h:45,
                 from /usr/include/c++/4.0.2/string:46,
                 from ./books.hpp:10,
                 from books.cpp:6:
/usr/include/c++/4.0.2/cstring:51:20: error: string.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.0.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.2/include/limits.h:11,
                 from /usr/include/c++/4.0.2/climits:49,
                 from /usr/include/c++/4.0.2/bits/stl_algobase.h:66,
                 from /usr/include/c++/4.0.2/bits/char_traits.h:46,
                 from /usr/include/c++/4.0.2/string:46,
                 from ./books.hpp:10,
                 from books.cpp:6:
/usr/lib/gcc/i486-linux-gnu/4.0.2/include/limits.h:122:61: error: limits.h: No such file or directory
In file included from /usr/include/c++/4.0.2/bits/stl_algobase.h:67,
                 from /usr/include/c++/4.0.2/bits/char_traits.h:46,
                 from /usr/include/c++/4.0.2/string:46,
                 from ./books.hpp:10,
                 from books.cpp:6:
/usr/include/c++/4.0.2/cstdlib:57:20: error: stdlib.h: No such file or directory
In file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:42,
                 from /usr/include/c++/4.0.2/iosfwd:45,
                 from /usr/include/c++/4.0.2/bits/stl_algobase.h:69,
                 from /usr/include/c++/4.0.2/bits/char_traits.h:46,
                 from /usr/include/c++/4.0.2/string:46,
                 from ./books.hpp:10,
                 from books.cpp:6:
/usr/include/c++/4.0.2/cstdio:52:19: error: stdio.h: No such file or directory
In file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:43,
                 from /usr/include/c++/4.0.2/iosfwd:45,
                 from /usr/include/c++/4.0.2/bits/stl_algobase.h:69,
                 from /usr/include/c++/4.0.2/bits/char_traits.h:46,
                 from /usr/include/c++/4.0.2/string:46,
                 from ./books.hpp:10,
                 from books.cpp:6:
/usr/include/c++/4.0.2/clocale:49:20: error: locale.h: No such file or directory
In file included from /usr/include/c++/4.0.2/iosfwd:45,
                 from /usr/include/c++/4.0.2/bits/stl_algobase.h:69,
                 from /usr/include/c++/4.0.2/bits/char_traits.h:46,
                 from /usr/include/c++/4.0.2/string:46,
                 from ./books.hpp:10,
                 from books.cpp:6:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:44:38: error: langinfo.h: No such file or directory
/usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:45:56: error: iconv.h: No such file or directory
```


Also I see an endless list of "Not declared" errors:

```
/usr/include/c++/4.0.2/cstring:79: error: ‘::memcpy’ has not been declared
/usr/include/c++/4.0.2/cstring:80: error: ‘::memmove’ has not been declared
/usr/include/c++/4.0.2/cstring:81: error: ‘::strcpy’ has not been declared
/usr/include/c++/4.0.2/cstring:82: error: ‘::strncpy’ has not been declared
/usr/include/c++/4.0.2/cstring:83: error: ‘::strcat’ has not been declared
/usr/include/c++/4.0.2/cstring:84: error: ‘::strncat’ has not been declared
/usr/include/c++/4.0.2/cstring:85: error: ‘::memcmp’ has not been declared
/usr/include/c++/4.0.2/cstring:86: error: ‘::strcmp’ has not been declared
/usr/include/c++/4.0.2/cstring:87: error: ‘::strcoll’ has not been declared
/usr/include/c++/4.0.2/cstring:88: error: ‘::strncmp’ has not been declared
/usr/include/c++/4.0.2/cstring:89: error: ‘::strxfrm’ has not been declared
/usr/include/c++/4.0.2/cstring:90: error: ‘::strcspn’ has not been declared
/usr/include/c++/4.0.2/cstring:91: error: ‘::strspn’ has not been declared
/usr/include/c++/4.0.2/cstring:92: error: ‘::strtok’ has not been declared
/usr/include/c++/4.0.2/cstring:93: error: ‘::memset’ has not been declared
/usr/include/c++/4.0.2/cstring:94: error: ‘::strerror’ has not been declared
/usr/include/c++/4.0.2/cstring:95: error: ‘::strlen’ has not been declared
/usr/include/c++/4.0.2/cstring:97: error: ‘::memchr’ has not been declared
/usr/include/c++/4.0.2/cstring: In function ‘void* std::memchr(void*, int, size_t)’:
/usr/include/c++/4.0.2/cstring:101: error: invalid conversion from ‘const void*’ to ‘void*’
/usr/include/c++/4.0.2/cstring:101: error:   initializing argument 1 of ‘void* std::memchr(void*, int, size_t)’
/usr/include/c++/4.0.2/cstring: At global scope:
/usr/include/c++/4.0.2/cstring:103: error: ‘::strchr’ has not been declared
/usr/include/c++/4.0.2/cstring:109: error: ‘::strpbrk’ has not been declared
/usr/include/c++/4.0.2/cstring:115: error: ‘::strrchr’ has not been declared
/usr/include/c++/4.0.2/cstring:121: error: ‘::strstr’ has not been declared
/usr/include/c++/4.0.2/cstdlib:93: error: ‘::div_t’ has not been declared
/usr/include/c++/4.0.2/cstdlib:94: error: ‘::ldiv_t’ has not been declared
/usr/include/c++/4.0.2/cstdlib:96: error: ‘::abort’ has not been declared
/usr/include/c++/4.0.2/cstdlib:97: error: ‘::abs’ has not been declared
/usr/include/c++/4.0.2/cstdlib:98: error: ‘::atexit’ has not been declared
/usr/include/c++/4.0.2/cstdlib:99: error: ‘::atof’ has not been declared
/usr/include/c++/4.0.2/cstdlib:100: error: ‘::atoi’ has not been declared
/usr/include/c++/4.0.2/cstdlib:101: error: ‘::atol’ has not been declared
/usr/include/c++/4.0.2/cstdlib:102: error: ‘::bsearch’ has not been declared
/usr/include/c++/4.0.2/cstdlib:103: error: ‘::calloc’ has not been declared
/usr/include/c++/4.0.2/cstdlib:104: error: ‘::div’ has not been declared
/usr/include/c++/4.0.2/cstdlib:105: error: ‘::exit’ has not been declared
/usr/include/c++/4.0.2/cstdlib:106: error: ‘::free’ has not been declared
/usr/include/c++/4.0.2/cstdlib:107: error: ‘::getenv’ has not been declared
/usr/include/c++/4.0.2/cstdlib:108: error: ‘::labs’ has not been declared
/usr/include/c++/4.0.2/cstdlib:109: error: ‘::ldiv’ has not been declared
/usr/include/c++/4.0.2/cstdlib:110: error: ‘::malloc’ has not been declared
/usr/include/c++/4.0.2/cstdlib:112: error: ‘::mblen’ has not been declared
/usr/include/c++/4.0.2/cstdlib:113: error: ‘::mbstowcs’ has not been declared
/usr/include/c++/4.0.2/cstdlib:114: error: ‘::mbtowc’ has not been declared
/usr/include/c++/4.0.2/cstdlib:116: error: ‘::qsort’ has not been declared
/usr/include/c++/4.0.2/cstdlib:117: error: ‘::rand’ has not been declared
/usr/include/c++/4.0.2/cstdlib:118: error: ‘::realloc’ has not been declared
/usr/include/c++/4.0.2/cstdlib:119: error: ‘::srand’ has not been declared
/usr/include/c++/4.0.2/cstdlib:120: error: ‘::strtod’ has not been declared
/usr/include/c++/4.0.2/cstdlib:121: error: ‘::strtol’ has not been declared
/usr/include/c++/4.0.2/cstdlib:122: error: ‘::strtoul’ has not been declared
/usr/include/c++/4.0.2/cstdlib:123: error: ‘::system’ has not been declared
/usr/include/c++/4.0.2/cstdlib:125: error: ‘::wcstombs’ has not been declared
/usr/include/c++/4.0.2/cstdlib:126: error: ‘::wctomb’ has not been declared
/usr/include/c++/4.0.2/cstdlib: In function ‘long int std::abs(long int)’:
/usr/include/c++/4.0.2/cstdlib:130: error: ‘labs’ was not declared in this scope
/usr/include/c++/4.0.2/cstdlib: At global scope:
/usr/include/c++/4.0.2/cstdlib:132: error: ‘ldiv_t’ does not name a type
/usr/include/c++/4.0.2/cstdlib:159: error: ‘::lldiv_t’ has not been declared
/usr/include/c++/4.0.2/cstdlib:165: error: ‘::_Exit’ has not been declared
/usr/include/c++/4.0.2/cstdlib:175: error: ‘lldiv_t’ does not name a type
/usr/include/c++/4.0.2/cstdlib:179: error: ‘lldiv_t’ does not name a type
/usr/include/c++/4.0.2/cstdlib:192: error: ‘::atoll’ has not been declared
/usr/include/c++/4.0.2/cstdlib:193: error: ‘::strtoll’ has not been declared
/usr/include/c++/4.0.2/cstdlib:194: error: ‘::strtoull’ has not been declared
/usr/include/c++/4.0.2/cstdlib:196: error: ‘::strtof’ has not been declared
/usr/include/c++/4.0.2/cstdlib:197: error: ‘::strtold’ has not been declared
/usr/include/c++/4.0.2/cstdlib:203: error: ‘__gnu_cxx::lldiv_t’ has not been declared
/usr/include/c++/4.0.2/cstdlib:205: error: ‘__gnu_cxx::_Exit’ has not been declared
/usr/include/c++/4.0.2/cstdlib:209: error: ‘__gnu_cxx::div’ has not been declared
/usr/include/c++/4.0.2/cstdlib:210: error: ‘__gnu_cxx::lldiv’ has not been declared
/usr/include/c++/4.0.2/cstdlib:212: error: ‘__gnu_cxx::atoll’ has not been declared
/usr/include/c++/4.0.2/cstdlib:213: error: ‘__gnu_cxx::strtof’ has not been declared
/usr/include/c++/4.0.2/cstdlib:214: error: ‘__gnu_cxx::strtoll’ has not been declared
/usr/include/c++/4.0.2/cstdlib:215: error: ‘__gnu_cxx::strtoull’ has not been declared
/usr/include/c++/4.0.2/cstdlib:216: error: ‘__gnu_cx

```

---


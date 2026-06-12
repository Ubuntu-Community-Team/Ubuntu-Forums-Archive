---
title: "Upgrading to Rosegarden 1.6"
date: 2007-12-08
forum: Art &amp; Design
---

### Post by greyfox1 on 2007-12-08
Hi all, I'm having trouble upgrading to the new Rosegarden v1.6, which was released this week.  I'm running 1.5.1 now but there are some important fixes/updates I want to take advantage of in 1.6.

I can't find 1.6 in Synaptic or Update Manager (I presume because it's so new) and I haven't been able to find any .deb packages to use, so I'm left with compiling from the source code that I got from Rosegarden's SourceForge page.  The instructions provided with the binary recommend I use cmake which I found and installed but I am having trouble using it.  I've never compiled binary myself so I'm at a loss. I extracted the tarball to my desktop and here's what I get when I try to compile using "cmake ."

```
$ cmake .
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- broken
CMake Error: The C compiler "/usr/bin/gcc" is not able to compile a simple test program.
It fails with the following output:
 /usr/bin/make -f CMakeFiles/cmTryCompileExec.dir/build.make CMakeFiles/cmTryCompileExec.dir/build
make[1]: Entering directory `/home/rick/Desktop/rosegarden-1.6.0/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/rick/Desktop/rosegarden-1.6.0/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec.dir/testCCompiler.o
/usr/bin/gcc   -o CMakeFiles/cmTryCompileExec.dir/testCCompiler.o   -c /home/rick/Desktop/rosegarden-1.6.0/CMakeFiles/CMakeTmp/testCCompiler.c
/home/rick/Desktop/rosegarden-1.6.0/CMakeFiles/CMakeTmp/testCCompiler.c:4:19: error: stdio.h: No such file or directory
/home/rick/Desktop/rosegarden-1.6.0/CMakeFiles/CMakeTmp/testCCompiler.c: In function &#8216;main&#8217;:
/home/rick/Desktop/rosegarden-1.6.0/CMakeFiles/CMakeTmp/testCCompiler.c:12: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
make[1]: Leaving directory `/home/rick/Desktop/rosegarden-1.6.0/CMakeFiles/CMakeTmp'
make[1]: *** [CMakeFiles/cmTryCompileExec.dir/testCCompiler.o] Error 1
make: *** [cmTryCompileExec/fast] Error 2


CMake will not be able to correctly generate this project.
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring done
```

If there is an easier way to do this, then by all means please enlighten me!  Otherwise please let me know what I need to do.  I presume I need to do some configuring in cmake but I don't really know what I'm doing.

I am using Ubuntu Studio 7.10.

*Edit* I just realized I managed to post this in Art & Design when I meant for it to go into Support.  I will re-post there.  Could a mod lock/delete this please?

---


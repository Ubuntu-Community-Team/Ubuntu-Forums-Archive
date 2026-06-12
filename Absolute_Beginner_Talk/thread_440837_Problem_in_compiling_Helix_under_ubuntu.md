---
title: "Problem in compiling Helix under ubuntu"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by yinglcs2 on 2007-05-12
Hi,

I am trying to compile Helix under ubuntu, but I get the following compile error:

Can you please tell me what libraries i need to install so that it can find 'gettid'?


servertrace.cpp:70: error: ‘gettid’ has not been declared
servertrace.cpp:71: error: expected constructor, destructor, or type conversion before ‘pid_t’
servertrace.cpp: In static member function ‘static void ServerTrace::PrintThreadId()’:
servertrace.cpp:128: error: ‘gettid’ was not declared in this scope
make: *** [dbg/obj/servertrace.o] Error 1
Time used: 0.10 seconds
ERROR: UNIXCompile(common/dbgtool) ERROR: Make failed.

--- Build System Error ------------------------------------
Make failed.

---


---
title: "C++ Ide?"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by mharris5 on 2006-09-28
Hi,

I'm looking for a C++ IDE. So far I've tried using KDevelop, but for some reason I get a makefile/configuration error when I go to compile,

"There is no Makefile in this directory
and no configure script for this project.
Run automake & friends and configure first?"

I run the automake, friends and configure and then get this response,

"cd '/home/matt/cpp_test' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && cd '/home/matt/cpp_test' && CC="i586-mingw32msvc-c" CXX="i586-mingw32msvc-c++" LD="i586-mingw32msvc-ld" "/home/matt/cpp_test/configure" && cd '/home/matt/cpp_test' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make configure.lo
/bin/sh: make: command not found
*** Exited with status: 127 ***"

Does anybody now, either a simpler IDE to use or a solution to this problem.

Thanks,

Matt.

---

### Post by croak77 on 2006-09-28
Do you have make installed? How about the build-essential package?

---

### Post by mharris5 on 2006-09-28
I have kdevelop3, kdevelop3 data, and Kdevelop3 plugins. Is there another package I need?

---

### Post by RussianVodka on 2006-09-28
May I sujest using SciTE as your text editor and the terminal to compile. That's what I do, and I love it.

---

### Post by mharris5 on 2006-09-28
I already use emacs for that, the problem I have is when your creating a multi file project, it's easier to use an IDE than recompile all the seperate files. Unless you have a simple solution to that as well?

---

### Post by croak77 on 2006-09-28
> **mharris5 said:**
> I have kdevelop3, kdevelop3 data, and Kdevelop3 plugins. Is there another package I need?

Yes, make which you are missing hence the "make: command not found" error. None of those packages includes make. But you should install build-essential, if you haven't,  which will automatically install make and gcc.

---

### Post by mharris5 on 2006-09-28
Yeh, I installed those packages and still no luck.

---

### Post by croak77 on 2006-09-28
Is ti the same error message as before?

---

### Post by croak77 on 2006-09-28
If you want to try a different IDE, there is anjuta or eclipse.

---

### Post by mharris5 on 2006-09-28
Yeh it's the same error as before. And thanks I'll give those a try as well. Is there any other package I need or anything else I might be doing wrong?

---

### Post by mharris5 on 2006-09-28
Well either way anjuta is working perfectly.

Thanks a lot for the help,

Matt

---


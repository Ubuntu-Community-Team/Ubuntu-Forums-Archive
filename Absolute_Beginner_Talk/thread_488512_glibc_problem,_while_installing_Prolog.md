---
title: "glibc problem, while installing Prolog"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by cluelessCS on 2007-06-30
Hi

[posted this before, maybe someone has an idea]

Trying to install Sicstus Prolog, there are some problems when I run the installation file:

> 
Checking installation cache... install.cache
dummy.c:1:19: error: stdio.h: No such file or directory
dummy.c:2:30: error: gnu/libc-version.h: No such file or directory
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c:1:19: error: stdio.h: No such file or directory
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c:2:22: error: features.h: No such file or directory
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c: In function ‘main’:
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c:13: warning: incompatible implicit declaration of built-in function ‘printf’
Glibc header files and runtime system disagree on version.
Header files: x86-linux


That's somehow related to the glibc, right? Which version of glibc does ubuntu come with?  And am I able to compile with it?

Also: The Sicstus Prolog release note says it requires glibc 2.3. 
If ubuntu comes with a higher version, can I install it anyway?


Thanks for your help

- Michael

---


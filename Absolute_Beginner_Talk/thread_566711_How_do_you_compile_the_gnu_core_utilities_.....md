---
title: "How do you compile the gnu core utilities ...."
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-03
I would like to experiment by modifying the core utilities -- like say uniq.c.

I have downloaded the gnu core utilities from:
[http://ftp.gnu.org/gnu/coreutils/](http://ftp.gnu.org/gnu/coreutils/)

When I compile with gcc then I get a lot of errors.
I guess I don't have my environment set up properly.

So, my intent is to edit a command like uniq.c, make some changes to it, and then compile giving me an a.out that I can experiment with.

Any help on setting this up is appreciated.

Thanks

Carl

---

### Post by Hospadar on 2007-10-03
what errors?

---

### Post by cwmoser on 2007-10-03
When I compile uniq.c like this:  gcc  uniq.c

Then, I get the following errors:

uniq.c:20:20: error: config.h: No such file or directory
In file included from uniq.c:26:
system.h:57:21: error: pathmax.h: No such file or directory
system.h:59:24: error: configmake.h: No such file or directory
system.h:126:22: error: exitfail.h: No such file or directory
In file included from uniq.c:26:
system.h: In function ‘initialize_exit_failure’:
system.h:133: error: ‘exit_failure’ undeclared (first use in this function)
system.h:133: error: (Each undeclared identifier is reported only once
system.h:133: error: for each function it appears in.)
system.h:239:25: error: stat-macros.h: No such file or directory
system.h:241:22: error: timespec.h: No such file or directory
system.h:269:21: error: gettext.h: No such file or directory
In file included from uniq.c:26:
system.h: At top level:
system.h:298: error: conflicting types for ‘malloc’
system.h:302: error: conflicting types for ‘memchr’
/usr/include/string.h:67: error: previous declaration of ‘memchr’ was here
system.h:306: error: conflicting types for ‘realloc’
/usr/include/stdlib.h:601: error: previous declaration of ‘realloc’ was here
system.h:341:20: error: xalloc.h: No such file or directory
system.h:342:20: error: verify.h: No such file or directory
system.h:358:25: error: unlocked-io.h: No such file or directory
system.h:359:24: error: same-inode.h: No such file or directory
system.h:361:21: error: dirname.h: No such file or directory
system.h:421:22: error: closeout.h: No such file or directory
system.h:422:25: error: version-etc.h: No such file or directory
system.h:439:22: error: intprops.h: No such file or directory
system.h:513: error: static declaration of ‘ftello’ follows non-static declaration
/usr/include/stdio.h:677: error: previous declaration of ‘ftello’ was here
uniq.c:27:22: error: argmatch.h: No such file or directory
uniq.c:28:24: error: linebuffer.h: No such file or directory
uniq.c:30:25: error: hard-locale.h: No such file or directory
uniq.c:31:22: error: posixver.h: No such file or directory
uniq.c:32:19: error: quote.h: No such file or directory
uniq.c:33:22: error: xmemcoll.h: No such file or directory
uniq.c:34:21: error: xstrtol.h: No such file or directory
uniq.c:35:24: error: memcasecmp.h: No such file or directory
uniq.c: In function ‘usage’:
uniq.c:131: warning: incompatible implicit declaration of built-in function ‘gettext’
uniq.c:170: error: ‘PACKAGE_BUGREPORT’ undeclared (first use in this function)
uniq.c: In function ‘size_opt’:
uniq.c:186: error: ‘LONGINT_OK’ undeclared (first use in this function)
uniq.c:187: error: ‘LONGINT_OVERFLOW’ undeclared (first use in this function)
uniq.c:191: warning: incompatible implicit declaration of built-in function ‘gettext’
uniq.c: At top level:
uniq.c:201: warning: ‘struct linebuffer’ declared inside parameter list
uniq.c:201: warning: its scope is only this definition or declaration, which is probably not what you want
uniq.c: In function ‘find_field’:
uniq.c:204: error: dereferencing pointer to incomplete type
uniq.c:205: error: dereferencing pointer to incomplete type
uniq.c: At top level:
uniq.c:254: warning: ‘struct linebuffer’ declared inside parameter list
uniq.c: In function ‘writeline’:
uniq.c:264: error: dereferencing pointer to incomplete type
uniq.c:264: error: dereferencing pointer to incomplete type
uniq.c: In function ‘check_file’:
uniq.c:273: error: storage size of ‘lb1’ isn’t known
uniq.c:273: error: storage size of ‘lb2’ isn’t known
uniq.c:305: warning: passing argument 1 of ‘find_field’ from incompatible pointer type
uniq.c:306: error: dereferencing pointer to incomplete type
uniq.c:306: error: dereferencing pointer to incomplete type
uniq.c:307: error: dereferencing pointer to incomplete type
uniq.c:310: error: dereferencing pointer to incomplete type
uniq.c:311: error: dereferencing pointer to incomplete type
uniq.c:328: warning: passing argument 1 of ‘find_field’ from incompatible pointer type
uniq.c:329: error: dereferencing pointer to incomplete type
uniq.c:329: error: dereferencing pointer to incomplete type
uniq.c:342: warning: passing argument 1 of ‘find_field’ from incompatible pointer type
uniq.c:343: error: dereferencing pointer to incomplete type
uniq.c:343: error: dereferencing pointer to incomplete type
uniq.c:350: warning: incompatible implicit declaration of built-in function ‘gettext’
uniq.c:372: warning: passing argument 1 of ‘writeline’ from incompatible pointer type
uniq.c:381: warning: passing argument 1 of ‘writeline’ from incompatible pointer type
uniq.c:386: warning: incompatible implicit declaration of built-in function ‘gettext’
uniq.c: In function ‘main’:
uniq.c:418: error: ‘close_stdout’ undeclared (first use in this function)
uniq.c:444: warning: incompatible implicit declaration of built-in function ‘gettext’
uniq.c:456: error: ‘LONGINT_OK’ undeclared (first use in this function)
uniq.c:461: warning: incompatible implicit declaration of built-in function ‘gettext’
uniq.c:483: error: expected expression before ‘size_t’
uniq.c:535: error: ‘GNU_PACKAGE’ undeclared (first use in this function)
uniq.c:535: error: ‘VERSION’ undeclared (first use in this function)
uniq.c:545: warning: incompatible implicit declaration of built-in function ‘gettext’

---

### Post by cwmoser on 2007-10-04
I have header files at /usr/include and /usr/include/sys.

There is something that I don't understand about compiling these.


Carl

---

### Post by cwmoser on 2007-10-04
I found the answer .... 

export  CFLAGS="-static -02 -g"

./configure

cd src
gcc  -std=gnu99  -I../lib   -static  -O2   -g   -MT uniq.o  -MD  -MP  -MF .deps/uniq.Tpo  -c  -o  uniq.o  uniq.c

The executable is stored along with the source in ./src.

Carl

---


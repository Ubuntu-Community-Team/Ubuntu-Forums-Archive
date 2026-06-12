---
title: "Problems compiling mdadm"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Rob_Quads on 2007-03-23
I am trying to compile mdadm ver 2.6.1. I have already completed this on my test box which is a straight 6.10 Desktop install with the latest patches. [ I can't remember installing anything more]

Now that I am working on my main machine which has just been installed with 6.10 and patched. When I try and make the latest version of mdadm I get the following errors

gcc -Wall -Werror -Wstrict-prototypes -ggdb -DSendmail=\""/usr/sbin/sendmail -t"\" -DCONFFILE=\"/etc/mdadm.conf\" -DCONFFILE2=\"/etc/mdadm/mdadm.conf\"   -c -o mdadm.o mdadm.c
In file included from mdadm.c:33:
mdadm.h:31:20: error: unistd.h: No such file or directory
In file included from mdadm.c:33:
mdadm.h:33: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lseek64’
mdadm.h:40:23: error: sys/types.h: No such file or directory
mdadm.h:41:22: error: sys/stat.h: No such file or directory
mdadm.h:42:20: error: stdlib.h: No such file or directory
mdadm.h:43:18: error: time.h: No such file or directory
mdadm.h:44:22: error: sys/time.h: No such file or directory
mdadm.h:45:20: error: getopt.h: No such file or directory
mdadm.h:46:19: error: fcntl.h: No such file or directory
mdadm.h:47:19: error: stdio.h: No such file or directory
mdadm.h:48:19: error: errno.h: No such file or directory
mdadm.h:49:20: error: string.h: No such file or directory
mdadm.h:50:20: error: syslog.h: No such file or directory
mdadm.h:59:26: error: linux/kdev_t.h: No such file or directory
mdadm.h:61:23: error: sys/mount.h: No such file or directory
mdadm.h:62:23: error: asm/types.h: No such file or directory
mdadm.h:63:23: error: sys/ioctl.h: No such file or directory
In file included from mdadm.h:76,
                 from mdadm.c:33:
md_p.h:88: error: expected specifier-qualifier-list before ‘__u32’
md_p.h:110: error: expected specifier-qualifier-list before ‘__u32’
md_p.h:188: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘md_event’
In file included from mdadm.h:77,
                 from mdadm.c:33:
bitmap.h:147: error: expected specifier-qualifier-list before ‘__u32’


I know I have something missing but I can't work out what it is to give me all these header files.

Thanks in advance

---

### Post by Rob_Quads on 2007-03-23
To anyone else having this problem. The solution is run

sudo apt-get install build-essential

---


---
title: "differences  between ybin and mkofboot?"
date: 2006-06-11
forum: Apple PPC Users
---

### Post by kellogs on 2006-06-11
Hi, I was looking at some kernel compiling howtos on ppc, I found always the last step as ybin -v or makeofboot after you edit yaboot.conf.

Looking at the help of those commands, they tell you about the same thing :

Usage: ybin [OPTION]...
Update/install bootloader onto a bootstrap partition.

Usage: mkofboot [OPTION]...
Update/install bootloader onto a bootstrap partition.

So, I suppose are those the same?

and one last thing, does the last compiling step "dpkg -i kernel-source-xxxx.deb" put the correct image (vmlinuz) on its correct place, I compiled a kernel but it could not boot(even selecting its linux image with Tab key, not the old one). I fixed reinstalling dapper but it would be useful to know, thanks.

---

### Post by colinhayes on 2006-06-11
[QUOTE=kellogs]Hi, I was looking at some kernel compiling howtos on ppc, I found always the last step as ybin -v or makeofboot after you edit yaboot.conf.

Looking at the help of those commands, they tell you about the same thing :

Usage: ybin [OPTION]...
Update/install bootloader onto a bootstrap partition.

Usage: mkofboot [OPTION]...
Update/install bootloader onto a bootstrap partition.

So, I suppose are those the same?

and one last thing, does the last compiling step "dpkg -i kernel-source-xxxx.deb" put the correct image (vmlinuz) on its correct place, I compiled a kernel but it could not boot(even selecting its linux image with Tab key, not the old one). I fixed reinstalling dapper but it would be useful to know, thanks.[/QUOTE]

well, ybin is the one recommended by yaboot, and the one that comes with it, so I'd keep with that if I were you.  It's also what I've always used.

---


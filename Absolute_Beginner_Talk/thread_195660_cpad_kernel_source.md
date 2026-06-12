---
title: "cpad kernel source"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by airzer0 on 2006-06-13
every time i try to do something in terminal i get this error:
Setting up cpad-kernel-source (0.9-10) ...
Warning: kernel headers don't match running Linux version.
Building cpad module for Linux 2.6.16 (this may take a few minutes)...dpkg: error processing cpad-kernel-source (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 cpad-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

i;m running dapper which is 2.6.15 so why is it saying 2.6.16 i think i messed up somewhere any help would be appriciated

---

### Post by airzer0 on 2006-06-13
i figured it out i had to sudo apt-get remove cpad-kernel-sources. turns out that was for a c pad driver for a notebook and it only worked with 2.6.16 so that was why it was looking for 2.6.16

---


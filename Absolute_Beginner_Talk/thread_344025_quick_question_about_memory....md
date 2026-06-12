---
title: "quick question about memory..."
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by je1117 on 2007-01-22
I just read an article on the internet about how RAM is displayed and determined, but it seems that contrary to most, I have a little something different. Here's a pmap printout of my firefox:

00002aaaab412000 348 r-x-- 0000000000000000 003:00001 libtoolkitcomps.so
00002aaaab469000 1020 ----- 0000000000057000 003:00001 libtoolkitcomps.so
00002aaaab568000 24 rw--- 0000000000056000 003:00001 libtoolkitcomps.so
00002aaaab56e000 216 r-x-- 0000000000000000 003:00001 libembedcomponents.so
00002aaaab5a4000 1020 ----- 0000000000036000 003:00001 libembedcomponents.so
00002aaaab6a3000 16 rw--- 0000000000035000 003:00001 libembedcomponents.so
00002aaaab6a7000 96 r-x-- 0000000000000000 003:00001 libcaps.so
00002aaaab6bf000 1020 ----- 0000000000018000 003:00001 libcaps.so
00002aaaab7be000 8 rw--- 0000000000017000 003:00001 libcaps.so
00002aaaab7c0000 200 r-x-- 0000000000000000 003:00001 librdf.so
00002aaaab7f2000 1020 ----- 0000000000032000 003:00001 librdf.so
00002aaaab8f1000 16 rw--- 0000000000031000 003:00001 librdf.so
00002aaaab8f5000 396 r-x-- 0000000000000000 003:00001 libdocshell.so
00002aaaab958000 1024 ----- 0000000000063000 003:00001 libdocshell.so
00002aaaaba58000 32 rw--- 0000000000063000 003:00001 libdocshell.so
00002aaaaba60000 24 r-x-- 0000000000000000 003:00001 libsystem-pref.so
00002aaaaba66000 1024 ----- 0000000000006000 003:00001 libsystem-pref.so
00002aaaabb66000 4 rw--- 0000000000006000 003:00001 libsystem-pref.so

I read that it was normal to have two of the same "looking" libs. One has the rw and one has the r-x modes, but I am wondering what this other one is? It ranges in size from 1020-1024kb as you can see and it ends up adding to a lot of mb.

Anyone know/have this problem?

---

### Post by je1117 on 2007-01-22
also, currently i'm running rhythmbox and firefox and it says that 31% of my mem is in use by programs and 62% of it is in use by the cache...

Almost my full gig of RAM is being used?

---

### Post by je1117 on 2007-01-22
bumpity.

---

### Post by tomBorgia on 2007-01-22
Yes, the system is "using" most of your RAM, this is normal -

"To make the most efficient use of real memory, Linux automatically uses all free RAM for buffer cache, but also automatically makes the cache smaller when programs need more memory." - [http://www.faqs.org/docs/linux_admin/buffer-cache.html](http://www.faqs.org/docs/linux_admin/buffer-cache.html)

:D

---

### Post by je1117 on 2007-01-22
Yeah, I already read that article and I understand about how it is used; my original question was what the third line of code for each lib and program was.

---


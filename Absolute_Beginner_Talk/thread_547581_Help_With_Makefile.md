---
title: "Help With Makefile"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by pspman3 on 2007-09-10
Hi all im pretty new to Ubuntu/GNU stuff and I am tring to compile PSP Programs (for my Playstation) so far I installed the toolchain but now im stuck because I have to add the folowing to my PATH but dont know how please help 

set path=%path%;C:/cygwin/usr/local/pspdev/bin
set PSPSDK=C:/cygwin/usr/local/pspdev

of course this is for cygwin but im under Ubuntu thanks

---

### Post by svalding on 2007-09-10
Google is your friend. Try searching for exporting PATH's in Ubuntu. 

It's fairly straightforward I believe. Even I should look it up, as it's been quite a while since I put Java in mine! If I recall it's something like 
```
 export PATH=
```
and then you can do an 
```
echo PATH
``` to see if it took. It will require you to log off and back on to your system before the changes will take effect.

---


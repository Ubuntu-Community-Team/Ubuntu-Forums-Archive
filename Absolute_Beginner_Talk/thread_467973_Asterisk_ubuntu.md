---
title: "Asterisk ubuntu"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by hernandezz on 2007-06-08
Hi, i got Ubuntu 6.06 installed and theres a problem with asterisk.

I've sucessfully installed it with the command:
#apt-get install asterisk

Then after installing FreePBX i get this error when restarting asterisk:
root@hernandezz-laptop:/home/hernandezz# asterisk -rvvvvvvvvvv
Unable to connect to remote asterisk (does
/var/run/asterisk/asterisk.ctl exist?)

After looking at the logs i noticed the problem could be the module format_mp3.so not being loaded because not exists in my PC.  in modules.conf i comment the line load => format_mp3.so and now it's works.This module is necessary?

Can anyone give me some hints?


my logs: /var/log/asterisk /full
***************************************************
***************************************************
***************************************************
Jun  8 12:18:58 NOTICE[5201] cdr.c: CDR simple logging enabled.
Jun  8 12:18:58 WARNING[5201] loader.c: /usr/lib/asterisk/modules/format_mp3.so: cannot open shared object file: No such file or directory
Jun  8 12:18:58 WARNING[5201] loader.c: Loading module format_mp3.so failed!
Jun  8 12:19:07 NOTICE[5215] cdr.c: CDR simple logging enabled.
Jun  8 12:19:07 WARNING[5215] loader.c: /usr/lib/asterisk/modules/format_mp3.so: cannot open shared object file: No such file or directory
Jun  8 12:19:07 WARNING[5215] loader.c: Loading module format_mp3.so failed!
Jun  8 12:21:55 NOTICE[5306] cdr.c: CDR simple logging enabled.
Jun  8 12:21:55 WARNING[5306] loader.c: /usr/lib/asterisk/modules/format_mp3.so: cannot open shared object file: No such file or directory
Jun  8 12:21:55 WARNING[5306] loader.c: Loading module format_mp3.so failed!
Jun  8 12:22:50 NOTICE[5340] cdr.c: CDR simple logging enabled.
Jun  8 12:22:50 WARNING[5340] loader.c: /usr/lib/asterisk/modules/format_mp3.so: cannot open shared object file: No such file or directory
Jun  8 12:22:50 WARNING[5340] loader.c: Loading module format_mp3.so failed!
Jun  8 12:24:00 NOTICE[5385] cdr.c: CDR simple logging enabled.
Jun  8 12:24:00 WARNING[5385] loader.c: /usr/lib/asterisk/modules/format_mp3.so: cannot open shared object file: No such file or directory
Jun  8 12:24:00 WARNING[5385] loader.c: Loading module format_mp3.so failed!
Jun  8 12:24:32 NOTICE[5436] cdr.c: CDR simple logging enabled.
Jun  8 12:24:32 WARNING[5436] loader.c: /usr/lib/asterisk/modules/format_mp3.so: cannot open shared object file: No such file or directory
Jun  8 12:24:32 WARNING[5436] loader.c: Loading module format_mp3.so failed!
***************************************************
***************************************************
***************************************************

ok works. I need the module format_mp3.so????????????????????
how i resolv this?

---


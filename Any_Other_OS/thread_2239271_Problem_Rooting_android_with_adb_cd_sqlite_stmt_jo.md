---
title: "Problem Rooting android with adb: cd /sqlite_stmt_journals no such file or directory"
date: 2014-08-12
forum: Any Other OS
---

### Post by scott60 on 2014-08-12
Hello,

I'm new to both linux and the ubuntu forums, although I'm trying the rather complex task of manually rooting my antiquated droid razr.

I'm currently running Jelly Bean 4.1.2 and ubuntu GNOME 14.04 LTS. I downloaded the entire Android ADT bundle (don't ask why), installed SDK Tools, Platform for 4.1.2, Platform Tools, and have followed the steps at [http://ubuntuforums.org/showthread.php?t=1958438](http://ubuntuforums.org/showthread.php?t=1958438). The OP links to this confusing wordpress blog [http://blog.mx17.net/2011/08/03/howto-root-your-xperia-x10-mini-pro-2-1-1-a-0/](http://blog.mx17.net/2011/08/03/howto-root-your-xperia-x10-mini-pro-2-1-1-a-0/) which asks to change to a directory not present

```
$ adb shell
$ cd /sqlite_stmt_journals
/system/bin/sh: cd: /sqlite_stmt_journals: No such file or directory
```

I'm not sure where to go from here. I'm thinking that the directory names have changed to something else, since the thread is so old. I've found other threads that deal with the same problem, but most of the responses are basically "you should probably try this easier method". I also added "su" and "psneuter" to the platform-tools folder in SDK, and made sure that my phone is on debugger. I don't have an SD card to back up my programs, I hope that's ok. Is there anyone that could guide me through the rest of the steps, or link me to a thread that can? Thank you for your patience.

---


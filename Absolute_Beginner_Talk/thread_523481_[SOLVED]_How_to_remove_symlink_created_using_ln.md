---
title: "[SOLVED] How to remove symlink created using ln ?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by trumps2k7 on 2007-08-11
Hi there,

When reading on this thread [http://ubuntuforums.org/showthread.php?p=2511814](http://ubuntuforums.org/showthread.php?p=2511814) ,  I followed the instructions to create a symlink, but now I need to remove it and dont know how. Below are the commands I used to create the symlink:

in /usr/src/linux-headers-2.6.20-16-generic/include/linux:
> 
ln -s autoconf.h config.h


Thank you very much!  :)

---

### Post by SOULRiDER on 2007-08-12
You can remove files/links witht he rm command. I dont think it follows links, but you can backup the original file and in case it gets deleted just move the backup.

---

### Post by p_quarles on 2007-08-12
I'm not really sure why you "need" to remove the symlink, but it's easy to do so. Go to the directory in which the symlink lives and type:
```
sudo rm config.h
```

---

### Post by trumps2k7 on 2007-08-12
Thanks it worked!

Why I wanted to remove the symlink: it seems since kernel 2.6.19 config.h is not supplied anymore, but I was trying to compile madwifi-old (still trying) which needs this config.h, so as per the suggestion of frosch6669 I created that symlink to "simulate" the presence of config.h, which turned to be unsuccessful. A lot of erros arised, and so I decided I would not want other programs to do the same mistake and think I actually have config.h.  However no big deal besides that.

---


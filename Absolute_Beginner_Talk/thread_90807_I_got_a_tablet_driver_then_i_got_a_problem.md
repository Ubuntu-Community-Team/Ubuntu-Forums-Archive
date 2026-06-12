---
title: "I got a tablet driver then i got a problem?"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by ecto on 2005-11-15
Hello! After months of toiling away i finally got some help from `23meg on the ubuntuforums channel on IRC and found a driver for my tablet... However the driver came in source and inorder to compile it i have to run a command called  xmkmf. However whenever i run it i get this error:
mv -f Makefile Makefile.bak
imake -DUseInstalled -I/etc/X11/config/cf
In file included from /etc/X11/config/cf/Imake.tmpl:2241,
                 from Imakefile.c:35:
./Imakefile:5: error: /usr/X11R6/lib/X11/config/Server.tmpl: No such file or directory
imake: Exit code 1.
  Stop.
When i posted on the forum that supplied the driver i was asked if i had xutils installed... I checked and i did have xutils... I tried ln -s /etc/X11/config/cf /usr/X11R6/lib/X11/config while rooted using sudo -s and that still doesnt fix the problem... Anyone have any idea of what is wrong?

---


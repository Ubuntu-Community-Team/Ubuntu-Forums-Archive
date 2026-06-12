---
title: "Hosed my Xserver-Xorg config"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by deaster2 on 2007-09-05
I have an old pc that I am running Gutsy on...the other night
I screwed around with the video drivers. Now it won't boot.
I get the error 'No Screens Found'.
I can get to a command line (root@deaster-desktop:~#).
I can stop the gnome display manager with '/etc/init.d/gdm stop'
When I run 'dpkg-reconfigure xserver-xorg' I get 'command not found'.
How, if possible,  do I run the reconfigure xserver-xorg interface from 
this command line?
I tried this from the X.Org.Wiki page:
xorgcfg, the graphical tool shipped with Xorg. You can also let the server generate a config file: as root just run X -configure. 
No success.

---

### Post by yabbadabbadont on 2007-09-05
```
/home/daffy $ which dpkg-reconfigure 
/usr/sbin/dpkg-reconfigure
/home/daffy $ /usr/sbin/dpkg-reconfigure -p high xserver-xorg

```
:D

Edit: If it isn't on your system, then you have bigger issues.  Reinstall from your Gutsy Tribe 5 (?) CD.  Welcome to the wonderful world of beta testing.  ;)

---


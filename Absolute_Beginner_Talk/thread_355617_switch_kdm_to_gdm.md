---
title: "switch kdm to gdm ?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by sankarv on 2007-02-07
Now im running kdm as display manager. How can i switch this back tp gdm again. 



Also if i try clicking System->Administration->Login Window it asks for rot password and does not do anything. I tried then in command line



```
sankarv@sankarv-desktop:~$ gksu gdmsetup

(gksu:6377): Gdk-WARNING **: locale not supported by Xlib

(gksu:6377): Gdk-WARNING **: cannot set locale modifiers
  Failed to connect to socket, sleep 1 second and retry

(gdmsetup:6378): Gdk-WARNING **: locale not supported by Xlib

(gdmsetup:6378): Gdk-WARNING **: cannot set locale modifiers
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.
sankarv@sankarv-desktop:~$
```


Please help me getting this back since every time kdm comes it gives "/usr/local/kdm/themes/kubuntu" not found.

Im pressing Ok for that and then proceeding.

---

### Post by etank on 2007-02-07
Try this```
sudo dpkg-reconfigure gdm
```Found it on [http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/)

---

### Post by SunnyRabbiera on 2007-02-07
KDM has always been troublesome to me, I think GDM is much smoother.

---


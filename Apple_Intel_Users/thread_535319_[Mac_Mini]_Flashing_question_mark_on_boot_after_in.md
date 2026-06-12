---
title: "[Mac Mini] Flashing question mark on boot after installation."
date: 2007-08-26
forum: Apple Intel Users
---

### Post by phibxr on 2007-08-26
I'm trying to install Xubuntu 7.04 on my Mac Mini Intel, and the installation works great; though after rebooting I'm greeted by a grey screen with a flashing question mark - and it won't go away. I've tried leaving it in this state for several minutes.

Installing OS X works perfectly, and I've had Xubuntu 7.04 up and running on the same system before, so I can't figure out where the problem lies.

My partition setup is:

Total 80GB
- / (ext3) 15GB
- /home (reiserfs) 64GB
- swap (1GB)

I'm currently reinstalling to check for the bootable flag, but I'm pretty sure I never did that last time I did a successful installation.

SOLVED:

By some reason, my /home was selected as bootable. With using parted to change / to bootable, it worked just fine.

---

### Post by zach12 on 2007-08-26
A Mac Mini will ubuntu way fast you don'n need xubuntu but you can if you like it more

---


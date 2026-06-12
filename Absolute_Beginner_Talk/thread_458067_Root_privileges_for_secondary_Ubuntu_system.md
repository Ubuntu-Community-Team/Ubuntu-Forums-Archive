---
title: "Root privileges for secondary Ubuntu system"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by linuxnooby on 2007-05-29
Being a newcomer to Linux, I don't know exactly how to put this question but  here goes.

I have 2 hard drives. The master drive originally had on it Windows 2000 and the slave had on it a cloned backup. I  installed Ubuntu  on free space  on the slave and then proceeded to experiment by adding and deleting applications, editing menus etc, the result being a bit of a jumble. It still works but I am not entirely happy with it.  I decided to install a second version onto free space on the master HD and just added th applications I really want.

Am I right in assuming that it is not possible to obtain root privileges for BOTH systems, whilst working in one or other of the two. ? For instance, I may want to copy an archive package from one system to the other but is this achievable ?

---

### Post by lazyart on 2007-05-29
The drive with the first installation should automount and you should be able to get in.  If you can see the drive but not the files you'll have to give yourself ownership via chown, but that's easy enough.

Go ahead and start your new installation and see where it takes you.  It's quick and easy to make it work once you're in.

---

### Post by linuxnooby on 2007-05-29
Sorry, don't quite follow you. I can access both file systems but only write to the one I have  booted into. I can boot to both of the 2 ubuntu file systems and also to both of the windows systems.

---


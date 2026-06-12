---
title: "boot problem"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by medic8ted on 2008-01-03
Hi, I'm very new to Ubuntu, 2 weeks and almost windoze free.  I'm dual booting Win XP and Gutsy, but now Gutsy hangs at black screen just before login screen with little spinning wheel.  Other posts similar to this talk of xorg, but if I try to view partition in XP it says not formatted (Ext2 driver is installed on XP).  Is this an xorg issue or something bigger?  If its xorg, I know I need to reconfigure, but with no login, how to get terminal?  Boot to recovery mode doesn't work, reinstalled grub, and tried repair from live cd (text version).  Help!  My home folder is in there (I know, don't say it).  It won't be there for long after this gets fixed:)

---

### Post by ~LoKe on 2008-01-03
Have you tried waiting for 30 seconds to a minute or two?  Mine blacks out then comes on shortly after.

---

### Post by RC Howe on 2008-01-03
Well, if you booted from the LiveCD and are able to access a terminal, you may try:
```
$ sudo chroot *your_disk_mount_location*
```
Then you can run whatever code you need to on your current install.

---

### Post by medic8ted on 2008-01-03
I tried waiting a while, HDD stops working (light goes off).  What will this do? ```
$ sudo chroot your_disk_mount_location
```

---

### Post by medic8ted on 2008-01-04
Ok, progress.  At black spinny wheel screen if I ctrl-alt-bkspc I get a login text prompt.  Login, started cp -a files to windows partition, screen flashed, back to spinny wheel.  Files kept copying, ctrl-alt-bkspc again, back to text.  Every couple seconds same thing.  If I type ```
 dpkg-reconfigure xorg-server 
``` it says its not installed.  If I try to apt-get it it says it can't find it?  Please, anyone?

---

### Post by medic8ted on 2008-01-04
bump

---


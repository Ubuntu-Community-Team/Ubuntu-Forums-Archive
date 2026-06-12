---
title: "Problems dual booting"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by axocean on 2008-03-23
First time user here
I followed all the instructions to setup my system to dual boot however when I went to reboot it automatically goes into XP. The only way I can get back into ubuntu is to use the live CD session. Help

---

### Post by Sef on 2008-03-23
With the live cd, let's check the partitions:

Applications > Accessories > Terminal

then type or copy and paste this code in the Terminal:

```
sudo fdisk -l
``` small L

---

### Post by axocean on 2008-03-24
REsults of requested- guessing I need to be booting from hda3
If thats right how do i d o that. 
Thanks in advance

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40037760000 bytes
255 heads, 63 sectors/track, 4867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4dfe4df

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           3        1914    15358140    7  HPFS/NTFS
/dev/hda2            1915        2041     1020127+  82  Linux swap / Solaris
/dev/hda3            2042        4867    22699845   83  Linux

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x329cb91f

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4865    39078081    7  HPFS/NTFS

---

### Post by Orrill on 2008-03-24
Can't you access the start-up and recovery options in XP and tick the box like in this screenshot?

[http://images.jakeludington.com/xp/xp_startuprecovery.png](http://images.jakeludington.com/xp/xp_startuprecovery.png)

---

### Post by axocean on 2008-03-24
not seen that screen before- where do i find it

---

### Post by housam on 2008-03-24
Did you installed windows after ubuntu ? if so , restore grub using [[COLOR="Red"]_this guide_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?")

---

### Post by Orrill on 2008-03-24
Haven't' used XP for a while but I think you right-click on My Computer > Properties > Advanced Tab and it's somewhere in there.

---

### Post by axocean on 2008-03-24
Found it it was already checked - with 15 seconds available

---

### Post by axocean on 2008-03-24
installed windows then installed ubuntu so have not yet tried reinstating grub as had not thought it was needed that way round

---

### Post by axocean on 2008-03-26
Thanks for all the advice tried all your suggestions none seemed to work - eventually deleted partition I had just installed ubuntu in to and ran the install process from the start- it worked just fine

---


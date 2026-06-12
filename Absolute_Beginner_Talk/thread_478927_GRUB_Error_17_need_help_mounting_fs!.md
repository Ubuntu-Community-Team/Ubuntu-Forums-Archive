---
title: "GRUB Error 17 need help mounting fs!"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by vegetable on 2007-06-19
I can't get passed the GRUB loading screen. i get Error 17.

right now i'm on the livecd reading this how-to [article]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28recoveringubuntu%29")

my fdisk output is:

[php]Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot         Start         End      Blocks       Id  System
/dev/hda1               1         244      1959898+  82  Linux swap / Solaris
/dev/hda2             245         9964    78075900   83  Linux[/php]

..but when i try mount /dev/hda2 /dir/in/article I get the error: mount: special device /dev/hd2/ does not exist

could anyone help? :(

---

### Post by Happy_Man on 2007-06-19
Just one more time (sorry) try this code:
```
sudo mkdir /media/ubuntu
sudo mount /dev/hda2 /media/ubuntu
```

Oh, and just to make sure.... you are in Edgy or Feisty?

And also, check the /dev folder for anything labeled hda2. If it's not there, post back.

---

### Post by vegetable on 2007-06-19
thanks for looking happy_man

i'm on 6.06 Dapper

i followed your suggestion and got: mount: you must specify the filesystem type

i then tried: [PHP]mount -t ext3 /dev/hda2 /media/ubuntu[/PHP] and got an error:  wrong fs type, bad option, bad superblock on /dev/hda2(..).  but i can't be 100% sure if that's the fs i'm using.. any way to find out?

Edit: hda2 does exist in /dev

---

### Post by logos34 on 2007-06-20
> mount -t ext3 /dev/hda2 /media/ubuntu 

Unless you did "sudo -i" before this command for admin priviledges, then try

**sudo mount -t ext3 /dev/hda2 /media/ubuntu **

OR

**sudo mount -t auto /dev/hda2 /media/ubuntu **

maybe there's something wrong with your grub config files or the mount options.

You might want to post **/boot/grub/menu.lst** and **/etc/fstab** files

Also, from the live cd you could do a filesystem check:

**sudo fsck /dev/hda2**

---

### Post by vegetable on 2007-06-20
actually, the last thing i tried last night was fsck /dev/hda2. and it actually got rid of the grub error 17. But during the fsck i was getting endless amounts of multiple inode errors, i was holding down the Y key for 5 minutes trying to fix them all, seriously. But when i rebooted, and after ubuntu did its normal boot process i got some fatal errors on some .so files. and the screen was just flashing these errors every second. it's probably a gui issue but I'm not even going to attempt to fix that. I just want to boot to shell and try to recover as much as i can. start fresh.

anyone know how to interupt the boot process to get the shell?

---

### Post by Happy_Man on 2007-06-20
Boot recovery mode, instead of regular.

---

### Post by vegetable on 2007-06-20
happy_Man, i get the same modprobe error flashing in the shell. and this whether i use recovery mode or ctrl-alt to bring up the shell. is there anything else i could do?

it seems hopeless. :(

---

### Post by johntkucz on 2007-06-21
YEs! Happy_man thanks so much, I was in similar bind! had to mount my dev/hda1 and then sudo chmod the permissiosn to access my home folder!! your tricks worked! Thank you.  I'm happy man, now!:)

---

### Post by vegetable on 2007-06-21
anyone know if i could recover this drive? without having to use another drive and slave this messed up one..

the fatal errors that fill the screen make it impossible to type commands.

---


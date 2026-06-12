---
title: "Reinstalling GRUB"
date: 2005-08-03
forum: Absolute Beginner Talk
---

### Post by Nanaki on 2005-08-03
I reinstalled Windows yesterday, and it formatted my MBR, meaning: no more GRUB. How can I reinstall it? I searched the fora, but I didn't really understand the answers. :p Any easy way on doing this?

---

### Post by poofyhairguy on 2005-08-03
[QUOTE=Nanaki]I reinstalled Windows yesterday, and it formatted my MBR, meaning: no more GRUB. How can I reinstall it? I searched the fora, but I didn't really understand the answers. :p Any easy way on doing this?[/QUOTE]

There isn't a really easy way. This is why most people would recommend installing Windows than Ubuntu. I personally fixed this problem by putting in the Ubuntu install cd, unplugging my network cable, hitting cancel at the networking part so it shows me the entire install process in order, then I jumped way ahead (past partitioning) and told the install cd to install the grub menu.

Fixed it.

---

### Post by Nanaki on 2005-08-03
Tnx for your help,

already tried that tho. It gives me an error about "/target not accessible".

Not that I gave a target yet...

---

### Post by TravisNewman on 2005-08-03
what I do when that happens is use the System Rescue CD, though the Ubuntu livecd and many others will allow this, and do the following in a terminal after booting up the CD:
[b]
mkdir /ubuntu[/b]
**mount /dev/hda2 /ubuntu** #you should substitute hda2 for the partition your base system is installed on.
If you have a separate /boot partition, you'll then need to
**mount /dev/hda1 /ubuntu/boot** #but again, only if you have a boot partition
**chroot /ubuntu /bin/bash** #now you're inside your ubuntu system
**grub** #this will bring up the grub shell
(inside the grub shell, do the following)
**root (hd0,0)** #hd0,0 corresponds to hda1. hd1,1 would be hdb2. They're weird. whatever comes in the parentheses should be the partition your boot files are on, whether it be the main ubuntu partition, or your /boot partition, if you have one.
**setup (hd0)** #this installs grub to the hard drive
**quit** #this should get you back to the command line. If not, try exit, I can't remember which
now at the command line, hit ctrl+d to log out of the ubuntu system and back to the livecd system.
If you have a /boot partition, type
**umount /ubuntu/boot**
the following will then unmount the root partition
[b]umount /ubuntu
[/b]

now you can reboot, and hopefully be back to the lovely grubbiness.

---

### Post by Nanaki on 2005-08-06
[QUOTE=panickedthumb]what I do when that happens is use the System Rescue CD, though the Ubuntu livecd and many others will allow this, and do the following in a terminal after booting up the CD:
[b]
mkdir /ubuntu[/b]
**mount /dev/hda2 /ubuntu** #you should substitute hda2 for the partition your base system is installed on.
If you have a separate /boot partition, you'll then need to
**mount /dev/hda1 /ubuntu/boot** #but again, only if you have a boot partition
**chroot /ubuntu /bin/bash** #now you're inside your ubuntu system
**grub** #this will bring up the grub shell
(inside the grub shell, do the following)
**root (hd0,0)** #hd0,0 corresponds to hda1. hd1,1 would be hdb2. They're weird. whatever comes in the parentheses should be the partition your boot files are on, whether it be the main ubuntu partition, or your /boot partition, if you have one.
**setup (hd0)** #this installs grub to the hard drive
**quit** #this should get you back to the command line. If not, try exit, I can't remember which
now at the command line, hit ctrl+d to log out of the ubuntu system and back to the livecd system.
If you have a /boot partition, type
**umount /ubuntu/boot**
the following will then unmount the root partition
[b]umount /ubuntu
[/b]

now you can reboot, and hopefully be back to the lovely grubbiness.[/QUOTE]
 Didn't work. :(

It's with the "root hd(0,0)" where I have problems. What do I type here when I want to use the MBR?

Imho, this should be made way more easy. :/

---

### Post by manicka on 2005-08-06
I kept this from another thread somewhere.
> 
Boot up from the Ubuntu cd. Mount the partitions, but make
sure you DO NOT FORMAT them. After you've mounted the partitions click
on Continue. The screen will get a red background and a warning appears
saying you are trying to install to an unclean target. Click Continue.
The next screen that appears is a list of stages. Jump straight to the
Install GRUB stage. Once that's done, eject the CD and use Ctrl Alt Del
to restart.

---

### Post by idokus on 2005-08-07
[QUOTE=Nanaki]Didn't work. :(

It's with the "root hd(0,0)" where I have problems. What do I type here when I want to use the MBR?

Imho, this should be made way more easy. :/[/QUOTE]

do you have a small partition for boot? fedora does, and it supplied the command grub-install

get linux running with a rescue of live disk
mount all your partitions.

[list]
[*]chroot "mount-point for /"
[*]grub-install "where your grub was installed" [for me it is the partition mounted on /boot, so that was /dev/hdax (x is a boot partition] (don't know if ubuntu creates a seperate boot partition by default or not.)
[*]reboot
[/list]

instead if this grub-install you might consider this: 
from "info grub-install"
> 
`--root-directory=DIR'
     Install GRUB images under the directory DIR instead of the root
     directory. This option is useful when you want to install GRUB
     into a separate partition or a removable disk. Here is an example
     in which you have a separate "boot" partition which is mounted on
     `/boot':
                                                                                
          grub-install --root-directory=/boot hd0


this is from the manual, (I didn't used it before but it seems to be doing the job quite alright. you might want to backup your boot partion, since it isn't the biggest of partistions :) )

grub-install is to be found in /sbin (then again in fedora that is, I don't know about ubuntu, I am planning on switching, but i'll take some work in backing up stuff)

---

### Post by GTar on 2005-08-07
Same problem here, been searching/posting for a bit now and tried all the solutions here. So far nothing seems to work for me.

I have 2 SATA drives though so some of these methods might not work. Not too sure.

---


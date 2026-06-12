---
title: "HOWTO:  USB thumb drive ext3"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by robertmcox on 2006-02-05
Figured this one out on my own, thought I'd share.

I have a USB thumb drive, formatted with vfat, works fine, plug it in and Nautilus sees it and puts an icon on the desktop.  This wasn't good enough for me because vfat cannot store permissions or symlinks.  I wanted to use this thumb drive in linux to store linux files only, but still have it automagically show up and be writable for only me!  So here's how:

First, plug in the drive.
'mount' will show you which drives are mounted. 
I observe that my thumb drive is mounted at /media/KINGSTON from /dev/sda1
'umount /media/KINGSTON' - this dismounts the drive so we can reformat it
'sudo mke2fs -j /dev/sda1'  - this reformats the drive with new filesystem
'sudo e2label /dev/sda1 KINGSTON' - this gives the drive a volume label
now unplug and replug your drive
you will observe that the drive is automounted in the same place
you will also observe that you do not have permissions!
'cd /media'
'sudo chgrp username KINGSTON'
'sudo chmod 770 KINGSTON'
now unplug and replug for Nautilus to see the new permissions
Yippee!

Note that you can change the label to anything you want.  If you have multiple thumbdrives like me, you'll want to give each one a different label.  This not only controls the mount point, but also helps you remember which drive you are working with.  You should probably label your drive physically too.  I wrote 'ext3' on my 'KINGSTON' so I would know not to use it with Windoze.

Note that root must own the mount point.

Note that you must chgrp/chmod the mount point while it is mounted.

Note that the 770 permissions give only 'username' full permission to the drive, not other users.

Enjoy and I hope this helps someone else.

---

### Post by bartbes on 2006-02-05
and **WHY** would you want to make your usb thumb drive windows incompatible, and what is the profit of making it ext3?

---

### Post by robertmcox on 2006-02-05
One more tip.

I didn't want to lose the contents of my thumb drive when I reformatted it with ext3, so I made a backup first:

'cd /media/KINGSTON'
'tar cvf ~/kingston.tar .' 

this creates a tar archive of the contents of the usb drive in your home folder.
now reformat your drive and adjust the permissions.

'cd /media/KINGSTON'
'tar xvf ~/kingston.tar'

this restores the files to your usb drive!

---

### Post by robertmcox on 2006-02-05
[QUOTE=bartbes]and **WHY** would you want to make your usb thumb drive windows incompatible, and what is the profit of making it ext3?[/QUOTE]

I have multiple thumb drives and I don't intend on using this one with any Windoze computers (I labelled it).  

By making the drive use ext3, I can copy permissions and symlinks.  I know I could just create a tarball on the device, but a tarball takes extra cpu cycles (read time).  Also, as I explore the *nix, it is usefull to be able to plug in my thumb drive and have immediate access to the information without have to decompress.

---


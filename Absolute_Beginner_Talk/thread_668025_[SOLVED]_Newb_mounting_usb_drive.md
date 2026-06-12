---
title: "[SOLVED] Newb mounting usb drive"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by ckennow on 2008-01-14
This should be an easy one for you all

I have 500 GB usb drive NTFS filesystem and i am trying to share it with my xp laptop using samba

I would like to know how to mount my usb drive from the command line since I am using ubuntu gutsy server edition. I know it will mount cuz it does it just fine when using the desktop version.  So how do i do this from the commandline.

---

### Post by xelapond on 2008-01-15
Try the mount command.

It would look something like
```
mount /dev/hda4<insert real drive path here>
```

---

### Post by ckennow on 2008-01-15
how do i find the "real drive path"?

---

### Post by Rocket2DMn on 2008-01-15
First you will need to make a directory for it (this only has to be done once).  You can call it whatever you like, I will call it usbdisk and use sdb1 for the dev.  I'm assuming you have ntfs-3g installed and working.
```
sudo mkdir /media/usbdisk
```
Then you can add an fstab entry for it to make it easy to mount every time
```
sudo nano /etc/fstab
```
Add the line:
```
/dev/sdb1 /media/usbdisk ntfs-3g defaults,locale=en_US.utf8 0 0
```
Then you can mount and unmount the drive when it's plugged in
```
sudo mount /media/usbdisk
sudo umount /media/usbdisk
```

The real path is found by using fdisk -l (a lowercase L):
```
sudo fdisk -l
```

---

### Post by ckennow on 2008-01-15
ok i added the line to fstab and then did ```
sudo mount /media/usbdisk
```
but i got this:

```

WARNING: Couldn't set locale to 'en_US.utf' thus some file names may not
         be correct or visible. Please see the potential solution at
         http://ntfs-3g.org/support.html#locale
fuse: failed to access mountpoint /media/usbdisk: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdb1 (Backup)

```

---

### Post by Rocket2DMn on 2008-01-15
There is a 8 at the end of utf.  It's not a typo :)

---

### Post by ckennow on 2008-01-15
lol oops...upon referencing the site and doing a locale -a i figured that one out and then i had used the wrong folder name in the fstab...I picked the foldername "Backup" to mount it to and i told fstab to use "usbdisk".  changed fstab to say /media/Backup and put the 8 on the end of that line and ran the mount command again and it is now working.  BTW is there a simple way of auto mounting this just in case i have to restart or anything

---

### Post by Rocket2DMn on 2008-01-15
If you restart the computer with the drive plugged in, it should be automounted on boot.  Otherwise when you plug the drive in, you just run that mount command.  It's just as easy to memorize that simple mount command as to write a script to do it for you then have to manually execute the script and still type in your password.

---

### Post by ckennow on 2008-01-15
I should make a webpage of "need to remember linux commands"  cuz there's a lot of them

---


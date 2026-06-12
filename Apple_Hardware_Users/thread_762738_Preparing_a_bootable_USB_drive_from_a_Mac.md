---
title: "Preparing a bootable USB drive from a Mac"
date: 2008-04-22
forum: Apple Hardware Users
---

### Post by jake74 on 2008-04-22
Hello all,

Firstly, I apologise if this is in the wrong forum. I did have a look around, but a) couldn't find my answer and b) couldn't decide where to put this thread! Please move if req'd

Anyway...

I've dabbled with Ubuntu occasionally, but am usually an OS X inhabitant. I've recently purchased an Asus EEE, and want to put eeeBuntu on it. I have the eeeBuntu 7.10 .iso file, and a 2GB fat16 USB pen drive... and that's where I draw a blank.

How do I get the .iso on to the USB pen drive using the tools available (or downloadable) to me in OS X (10.5.2)?

I've followed a lot of tutorials, but they're linux or PC based. I've tried using Disk Utility to restore the image, but that fails.

Any guidance gratefully accepted.

jake

---

### Post by stream303 on 2008-04-22
Does anything here help?  Looks like it has been updated for Hardy and maybe all you need is a live installer:

[http://ubuntuforums.org/showthread.php?t=761817](http://ubuntuforums.org/showthread.php?t=761817)

---

### Post by mrsteveman1 on 2008-04-22
Format the stick as an MBR partition table disk in disk utility, then double click the ISO file to mount it on the desktop.

Copy all the files from the ISO on to your stick.

From there you can follow the guides available.

When you get to the part about syslinux you will have to get it from one of the ports collections (fink or macports).

It may be easier to simply boot an ubuntu livecd on something and do it from there.

---

### Post by slacka-vt on 2008-04-22
Couldn't you use Mac's "Disk Utility" to "restore" the ISO image to the thumb drive ?
That's the root I would pursue .
I'm not sure just copying the files to the thumb drive would yield a boot-able system.

Just noticed you tried that already. DOH !

> I've followed a lot of tutorials, but they're linux or PC based. I've tried using Disk Utility to restore the image, but that fails.

What exactly fails? You may need to format the thumb drive "just right".

~s

---

### Post by mrsteveman1 on 2008-04-23
The files just need to be on the drive, but then you have to install syslinux to the device, which is probably easier from linux or windows because there are packages available for those systems.

Restoring an ISO with disk utility only works if the filesystem inside the ISO is something other than iso9660, because you can't put those on a block device like a USB stick. It works for the OS X disk because the OS X disk is an HFS+ filesystem.

---

### Post by jake74 on 2008-04-23
Thanks for all the help.

I ended up trying the Hardy Heron live cd, and installing it under VMWare. I followed all the steps in the Pendrive tutorial ([http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)) but I'm unsure of the steps near the end;

cd /cdrom

Type cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz /media/ubuntu710/

What would I change in that line to reflect the fact I'm using a disk image called eeebunu7.10.iso? Can I just mount the iso and cd into the iso dir?

I ended up copying all the files in the Mac Finder, then dropping into Heron to syslinux the USB

syslinux -sf /dev/sdx1

Not tried booting yet, but am off to work. I have two fully fledged linux nerds at work who'll help me get further (while trying not to laugh at the Mac boy!)

Again, thanks for all your help, as always.

---

### Post by sabrinaluv1 on 2010-04-19
Wow that was some great information, that just really helped me with my problem. [[color=#FFFFFF]_Insanity Workout_[/color]](http://www.ultimatefitnessgear.com/insanity-with-shaun-t.html)

---

### Post by Neds Moar Salt on 2010-04-19
You won't be able to boot your mac with that.  I wrote a tutorial on this but it got buried.  Basically download rEFIt, partition your USB with MBR/GPT scheme, only GPT if you are going to sync it, then have a partition for grub, rEFIt, and your live system.  Install rEFIt to your rEFIt partition, then copy all the files in the live cd (including .disk, it's hidden) to the live partition (make sure it is fat).  Then you will need linux to run grub-install and format the grub partition as ext3.  then you can boot your mac or your pc from the usb stick after blessing/"installing" rEFIt and holding down the option key at startup.

---

### Post by dfacto on 2011-09-21
Just so there is a good answer to this thread (as it is still definitely relevant!), here is my work-around which I used on the 2011 MacBook Air.  It should work for any Mactel.
[http://ubuntuforums.org/showpost.php?p=11093491&postcount=43](http://ubuntuforums.org/showpost.php?p=11093491&postcount=43)

---


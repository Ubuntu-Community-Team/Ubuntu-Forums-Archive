---
title: "Trying to create a usb boot cd."
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Timboleo on 2007-08-26
Hello to all and please be kind I am a newbie to linux.

I have a 80g USB2 drive that I did a an install of Feisty 7.04 on. All went fine I did the install from a install disk not a live cd. My bios say that I have the option to boot usb items. But after some digging on the ASUS website it seems that is not the case. So I have no ability to boot to the usb drive. My other 2 hard drives are sata drives that also can't be seen by GRUB. So hence the need to make a boot CD with USB modules on to boot system.

I looked at the ubuntu community docs and found a very good lesson on making a USB boot CD. I can boot up with the Live CD and access my drives fine. Following the tutorial I have edited the required files that need to be on the CD. It is now telling me to mount and reconfigure the linux image. Here is the problem!!!!

sudo mount  --bind /dev /mountpoint for system/dev
sudo chroot /mountpoint for system

At this point I get the no permission to enter root error so I can't continue.:confused:

What do I need to do to have permission since I am running off of the cd as user ubuntu.
Would I be better off entering through the rescue mode on the install disk, and if so what do I need to do?
I have tried to see if there was a simmular problem here but no luck so far.
Lots of tutorials but all involve another system with linux on already or booting with the bios. I'm sitting at 2 strikes

---

### Post by Timboleo on 2007-08-29
Ok since I'm hearing the sounds of crickets here I have started to experiment on my own.
Progress has been made!!

I booted with the install cd that was used to load the system on the USB drive in rescue mode.

It took a little experimenting as /dev/sda1 was listed as the drive when I loaded.

But in the rescue mode /dev/sdb1 was the correct disk that had all the files on. Go figure?

I then opened a shell and was able to reconfigure the linux kernel with files that had been edited. YES!!

Time to copy the files to the folders that are to be on the CD. Oops no permission again:confused:

Ok think hard what to do. (More cricket sounds)

UH Windoze maybe?  Can't see files, or can I!  How about a little program called EXT2 IFS.  What a nice proggy. It lets you see the files in Windoze, and you can read and write to them.  I don't need no stinkin permission to copy files. WOOT!!

Files are now copied and renamed to the correct folders. Now I still have to correct the menu.lst , but no time right now.

Any one with better suggestions Please SQUASH a Cricket and pipe in here.

---


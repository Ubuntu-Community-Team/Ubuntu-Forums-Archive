---
title: "Grub error 21"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by tadiv on 2007-02-19
Okay, so yesterday I spent a ton of time trying to get 6.10 loaded onto an external drive for my laptop - after much fighting, I got it to go and made the mistake I was attempting to avoid with the external drive in the first place...

My intent was to leave the hard drive internal to the laptop untouched by the install and, when wanting to work with Ubuntu, simply plug in the external drive and boot from that drive. Well, it seems that in my happiness over getting the install to work (I had issues, I think w/ the usb 1.1 ports) I allowed grub to be written to hd0 (yes, the very drive I did not want to touch).

So, now I have to have this external drive hooked up to successfully boot any OS. If the external drive is not connected I get a grub error 21 and all indications are that the boot sequence has stopped.

What I would really like to do is get my hd0 back the way it was (so it will boot that other OS if nothing is connected) so I can set up the external to boot Ubuntu only if that external drive is attached - OR at least get the hd0 to boot that other OS if the external drive is not connected...

Any recommendations? 


Thanks in advance,
Tom

---

### Post by Duck2006 on 2007-02-19
Boot from your windoze xp cd and enter the recovery mode, at the promt type

fixmbr

reboot and you sould be able to boot into windoze. 

You can install grub on to the mbr of the usb hard drive by booting in to the live cd and telling it where you want to install grub.

---

### Post by tadiv on 2007-02-19
Do I have to go through the whole install again, or is there a way to just install GRUB?

---

### Post by Duck2006 on 2007-02-19
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

This may be of help

no you don,t have to go through the hole install again.

---

### Post by tadiv on 2007-02-19
Okay -- "fixmbr" worked without any problems... :) 

I'm having trouble with grub...  so on my laptop I have "Boot from" order in the BIOS as follows:

Removable Media
CD Rom
Internal Hard Drives
LAN

The usbdrive is "hd1" and the grub geometry command displays /dev/sda, though the menu.lst file seemed to list it as "/dev/sda1" 

ANYWAY, I did the grub "root (hd1,0)" command and the "setup (hd1)" command as well -- it looked like that was all I had to do since it seems that all the required files are on the usbdisk.  I have fooled with the menu.lst file a bit, but every time I boot, the machine passes by the usbdrive as if it is not a valid boot device.

Any more suggestions?

---

### Post by tadiv on 2007-02-19
Okay -- I'm now on my laptop, so I can include stuff like the command outputs and such...

Here is the geometry command output for the usbdrive...

grub> geometry (hd1)
drive 0x81: C/H/S = 7296/255/63, The number of sectors = 117210240, /dev/sda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> 

so it does not look like there is another partition to load to...

Let me know what you think -- I'll watch for a reply...

I can include the text of the menu.lst file if you think it will help...

Tom

---

### Post by confused57 on 2007-02-19
See reply #49(& #52) in this thread:
[http://www.ubuntuforums.org/showthread.php?t=363306&page=5](http://www.ubuntuforums.org/showthread.php?t=363306&page=5)

The link for reinstalling grub with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Your setup sounds similar to the OP in the first thread.

---

### Post by Duck2006 on 2007-02-20
I would go with Confused 57 post it sounds very much like your setup

---


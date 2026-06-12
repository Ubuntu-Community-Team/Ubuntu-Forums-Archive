---
title: "grub install"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by hrd12 on 2007-05-29
Hi!
I checked the forums for this answer but I didn't find exactly what I was looking for.  I have Windows installed on one drive and Ubuntu on another.  I made the mistake of installing Windows after installing Ubuntu, so Grub got wiped out.  I am now booting from the live cd to try and reinstall Grub.  I tried the following commands to reinstall it, but to no avail thus far:

$ sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> exit

I then rebooted the system and Windows still came up with no Grub menu.  I just want to make sure I am trying to install this in the right place:

Here is what fdisk -l shows after I mounted the hard drive to /storage/device

ubuntu@ubuntu:/storage/device$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4665    37471581   83  Linux
/dev/hdb2            4666        4866     1614532+   5  Extended
/dev/hdb5            4666        4866     1614501   82  Linux swap / Solaris
ubuntu@ubuntu:/storage/device$ 

What I have tried so far hasn't worked.  Any suggestions on how I can get Grub working again?  Thanks a lot!

---

### Post by confused57 on 2007-05-29
If you can boot first to your Ubuntu drive, you should get a grub boot menu...if you do, highlight your Ubuntu entry, press "e", then change root from (hd1,0) to (hd0,0), then press "b" to boot...this change is temporary, but if you want to leave your system set up this way, it can be made permanent.

You can also install grub to your Window's drive mbr by "setup (hd0)"...this will overwrite your Window's IPL code that is installed on your hd0 drive.  
You'd then need to add an entry to boot Windows, if you don't already have one, in your menu.lst.

It's your choice as to how you want to set up your system.

---

### Post by hrd12 on 2007-05-31
Thanks for your help.  Unfortunately, no grub menu when I try to boot up Ubuntu.  Just a black screen with the cursor and then i get an error that says "no boot signature in partition".  

I was going to try your second suggestion, but before I do that I had a question.  Do I need to mount the Windows drive in order to install grub to it?  I have an idea how to do that if it is infact needed.  Thanks again!

---

### Post by alienexplorers on 2007-05-31
Boot from the live CD.
enter terminal
enter
> sudo grub
enter
> find /boot/grub/stage1
enter
> root (hd#,#)
enter
> setup (hd#)

the # will be the result of what comes up from the find command.
If you are booting from the MBR you would have something like (hd0,0).

---

### Post by hrd12 on 2007-05-31
No love :-/ All the commands you gave me seemed to work just fine.  It told me hd1,0, so that is what I used.  When I rebooted it went right into windows with no grub menu or prompt.  Any other ideas?

---

### Post by hrd12 on 2007-05-31
I tried some other stuff.  First I just plugged in the Ubuntu drive to see what would happen.  I eventually got to a prompt that said "Primary hard disk drive 1 not found, press f1 to continue and f2 to setup.  I pressed f1.  That brought me to the Grub menu.  I tried to boot any of the OS's listed and each one gave me a Error 23: Error while parsing number.  I see that I can use e to edit this, but I don't really know what to edit.  Suggestions from here?

---

### Post by confused57 on 2007-05-31
> **hrd12 said:**
> I tried some other stuff.  First I just plugged in the Ubuntu drive to see what would happen.  I eventually got to a prompt that said "Primary hard disk drive 1 not found, press f1 to continue and f2 to setup.  I pressed f1.  That brought me to the Grub menu.  I tried to boot any of the OS's listed and each one gave me a Error 23: Error while parsing number.  I see that I can use e to edit this, but I don't really know what to edit.  Suggestions from here?
You could try the method alienexplorers suggested(with both drives connected), but enter "setup (hd0)".

Before you do this, I would make a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD can be used to boot Windows or Ubuntu Linux or restore either IPL to the mbr.

here's a list of SGD download mirrors:
[http://ubuntuforums.org/showthread.php?t=419598](http://ubuntuforums.org/showthread.php?t=419598)

---


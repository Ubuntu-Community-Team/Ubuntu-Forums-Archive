---
title: "XP and Ubuntu dual boot trouble"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Kreuzfeuer on 2007-07-30
I guess i messed this up but maybe someone can help me.

I installed ubuntu on a ext3 partition on my primary HD but since i had trouble with the nvidia drivers and i like to play games i decided to install XP.

i used an fat32 partition on the same drive for windows, so ubuntu and XP are on the same drive, on different partitions. but whenever i boot, it boots XP, how can i fix it so i can decide what to boot?

---

### Post by ugm6hr on 2007-07-30
[http://ubuntuforums.org/showpost.php?p=3103687&postcount=2](http://ubuntuforums.org/showpost.php?p=3103687&postcount=2)

---

### Post by mattmole on 2007-07-30
Hi,

The main key to this is to install XP first, and then install Ubuntu. Ubuntu will detect both OS's and let you choose which one to load. Unfortunately XP takes over and ignore anything else installed.

Have a search on the forums for GRUB. Basically, I think you need to install GRUB to the MBR of your harddrive, which XP has overwritten.

Sorry I cant help anymore.

Mattmole

---

### Post by MQMike on 2007-07-30
You need to re-install GRUB.

First, you need to get a grub prompt (grub>) somehow.  Your two choices are: (1) Use a rescue disk, like Super Grub Disk, from which you can boot into your OS, or press the “c” key to get a GRUB prompt.  Or, (2) Use your Live Kubuntu CD.  Let's assume (2) here.  

Put your Live CD in the CD tray, re-boot your PC, startup your Live Kubuntu.  
Now get a terminal and proceed as follows:

Get a GRUB prompt as root by typing sudo grub  (then press Enter), and type the following (press Enter after each command):
grub>  root (hdx,y)          # (hdx,y) is the partition of your "main" Linux OS--SEE NOTE BELOW
grub>  setup (hd0)          # This assumes (hd0) is your “main” booting hard drive MBR
grub>  quit
$ exit

Close out all windows.
Re-boot to test it.

NOTE:  
From what you said, Ubuntu was there first, probably on (hd0, 0) – the first hard drive hd0, the first partition (partition 0).  (Note that the bootloader GRUB starts numbering drives and partitions from zero).

So, root (hdx, y) should be root (hd0, 0)

- - - - -
After doing all this, you may still have to edit the boot menu for GRUB, which is contained in Ubuntu at /boot/grub/menu.lst.  (.lst is an “l” as in “list.”)
You must edit it as root, and don’t forget to save your changes when you are done (File-Save, File-Quit).
The part you need to check/edit is the boot menu for Windows, which should look like:

title Windows XP or whatever you wish to call it
rootnoverify (hdx, y)
makeactive
chainloader +1

where:
(hdx, y) is your Windows partition.
It’s on the first HD, right?  So x = 0.   What partition y is it on?  If the second partition, then y = 1, if the third then y =2, etc.  (GRUB, the bootloader starts counting from zero.)


For details:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by Kreuzfeuer on 2007-07-30
worked perfectly, thanks a lot!

btw: there is an "i" missing in chainloader, took me some time to figure out.

---

### Post by MQMike on 2007-07-30
"worked perfectly, thanks a lot!
btw: there is an "i" missing in chainloader, took me some time to figure out."

Ha!  That was just a test . . .

Yep, you're right, I corrected it in case someone else follows us down this path.
I typed that fresh rather than copy-and-paste, so that's a reminder to me to get better organized on my helping end here.  :)

Glad it worked for you!  Way to go there!

--Mike

---


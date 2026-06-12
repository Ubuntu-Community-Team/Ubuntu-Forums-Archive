---
title: "[SOLVED] 7.10 on MacBook Install Help"
date: 2007-10-17
forum: Apple Intel Users
---

### Post by DGortze380 on 2007-10-17
Hey guys, new to Ubuntu here, I've been running edgy on a PC in a lab at school but want to install Ubuntu 7.10 on my MacBook so I can get some practice using it and see what it's really capable of.  I read the Wiki and it looks pretty straight forward my only question at this point is about partitioning my hard drive. 

Do I have to use Boot Camp?  Frankly I don't have the money to go buy it, but I'm not sure how to resize the one default partition on my MacBook.  Ubuntu should still install GRUB and let me select which OS to boot even if I don't use Boot Camp, right?  How do I go about getting this drive partitioned w/o boot camp so I can try an install? Or, where can I download boot camp beta (if it's still available that is).

Thanks in advance,

Dan

EDIT: It's a Gen 2 - Core 2 Duo - MacBook

---

### Post by cyberdork33 on 2007-10-17
> **DGortze380 said:**
> Hey guys, new to Ubuntu here, I've been running edgy on a PC in a lab at school but want to install Ubuntu 7.10 on my MacBook so I can get some practice using it and see what it's really capable of.  I read the Wiki and it looks pretty straight forward my only question at this point is about partitioning my hard drive. 

Do I have to use Boot Camp?  Frankly I don't have the money to go buy it, but I'm not sure how to resize the one default partition on my MacBook.  Ubuntu should still install GRUB and let me select which OS to boot even if I don't use Boot Camp, right?  How do I go about getting this drive partitioned w/o boot camp so I can try an install? Or, where can I download boot camp beta (if it's still available that is).

Thanks in advance,

Dan

EDIT: It's a Gen 2 - Core 2 Duo - MacBook

The boot camp beta is available until the end of October on Apple's website. [http://www.apple.com/downloads/macosx/apple/application_updates/bootcamp.html](http://www.apple.com/downloads/macosx/apple/application_updates/bootcamp.html)

Boot Camp is just a graphical front end to a terminal command that can be used by itself. (See [http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes](http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes))

Gparted can also shrink your OSX partition down. [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by DGortze380 on 2007-10-17
Thanks, I ended up just trying GParted and it worked fine. Up and running!

---

### Post by heebus on 2007-10-17
Gparted seemed slow for me, which is why I ended up partitioning with Boot Camp.

---

### Post by cyberdork33 on 2007-10-18
Please mark as solved

---

### Post by DGortze380 on 2007-10-18
Except, now it's not solved... I was up and running yesterday but I booted this morning and now OS X will not boot. I can Boot into Ubuntu fine though. Any ideas?

---

### Post by cyberdork33 on 2007-10-18
> **DGortze380 said:**
> Except, now it's not solved... I was up and running yesterday but I booted this morning and now OS X will not boot. I can Boot into Ubuntu fine though. Any ideas?
Well, maybe a more descriptive statement of the issue would help... Do you not have the option to choose OSX? Are you using rEFIt? how are you choosing the OS if not?

If you are actually getting to the point where you can attempt to boot OSX, are there any error messages? Have you tried Single-User Mode?

You might just try booting the OSX DVD and using disk utility to check the partition if OSX is having errors.

---

### Post by DGortze380 on 2007-10-18
> **cyberdork33 said:**
> Well, maybe a more descriptive statement of the issue would help... Do you not have the option to choose OSX? Are you using rEFIt? how are you choosing the OS if not?

If you are actually getting to the point where you can attempt to boot OSX, are there any error messages? Have you tried Single-User Mode?

You might just try booting the OSX DVD and using disk utility to check the partition if OSX is having errors.

I can do one of two things. Power on and let the machine attempt to boot OS X. I get a gray sceen with an Apple and a pinwheel then it powers down. Won't boot.  Or I can hold option as the machine starts and I get the option to boot Mac OS X or Ubuntu. If I chose Ubuntu it boots, if I chose OS X, the same thing happens as above.  

I'm not sure what rEEIt is? I'm guessing the built in boot loader for OS X? My recovery disks aren't with me, I'm going to pick them up tonight and try checking OS X for errors, or just do a clean install.  I'm confused because it worked fine last night both OSs would boot, and now OS X won't boot.

---

### Post by cyberdork33 on 2007-10-18
> **DGortze380 said:**
> I can do one of two things. Power on and let the machine attempt to boot OS X. I get a gray sceen with an Apple and a pinwheel then it powers down. Won't boot.  Or I can hold option as the machine starts and I get the option to boot Mac OS X or Ubuntu. If I chose Ubuntu it boots, if I chose OS X, the same thing happens as above.  

I'm not sure what rEEIt is? I'm guessing the built in boot loader for OS X? My recovery disks aren't with me, I'm going to pick them up tonight and try checking OS X for errors, or just do a clean install.  I'm confused because it worked fine last night both OSs would boot, and now OS X won't boot.

Sometimes you just get filesystem errors after you resize a partition. Try booting while holding CMD+S, that should start single user mode, and you can run the commandline filesystem check if you make it to the prompt (or you can maybe see an error).

rEFIt (that's an F )is a 3rd party OS selector menu. You don't NEED it, but it might be helpful if you like it. [http://refit.sourceforge.net/](http://refit.sourceforge.net/)

---

### Post by DGortze380 on 2007-10-18
Ok, booted in verbose. two things looked like possible issue. there was on pause at-

IOBluetoothACIControler:: Start Idle Timer Stopped Invalid Sibling Link
(4, 5751)

Boot continued and stopped at-

Checking Catalog File
Invalid Sibling Link
(4,5751)
Syncing disks...killing all processes

and it shuts down from there.

I'll try single user mode and get back to you.

---

### Post by ward83 on 2007-10-18
Try holding the option (alt) key when booting, and selecting OSX from the menu. Somewhere in the system preferences is a "select startup disk" option. I think it's System Prefs > Disks or something like that. I had to do this after using Boot Camp to resize my partition.

---

### Post by DGortze380 on 2007-10-18
ok, I was able to start Single user mode. How do run a file system check. Sorry, bit of a newbie when it comes to working with terminals and command lines.

---

### Post by DGortze380 on 2007-10-18
file system check returned the same as above-

EDIT: File system check returned same as above-

** /dev/rdisk0s2
** Root File System
** Checking HFS Plus Volume
** Checking Extents Overflow file
** Checking Catalog File
Invalid Sibling Link
(4, 5751)
Volume Check Failed

---

### Post by hackworth on 2007-10-18
google search for "Invalid sibling link" reveals: [http://www.macosxhints.com/article.php?story=20070204093925888](http://www.macosxhints.com/article.php?story=20070204093925888)

---

### Post by DGortze380 on 2007-10-18
duh.. sorry, should have search more...

Thanks for the idea, I'll try it when I get my system disks tomorrow.

Any other options in the mean time would be appreciated.

---

### Post by cyberdork33 on 2007-10-19
Yea I had a similar problem once. I got it to the point where it would boot, but would break again after awhile, plus disk verification would fail when I attempted to use it still. Disk Warrior was the only thing that I got to fix it.

---

### Post by DGortze380 on 2007-10-20
Ok, problem resolved thanks a bunch for all the help, would have had to reformat the hard drive without you guys.  Here's the run down.

Macbook Gen2 Core 2 Duo
After repartitioning my Hard Drive and installing Ubuntu 7.10 I was unable to boot OS X from the default boot loader.  Steps outlines above indicated a catalog error.  I fixed this error by booting with the recovery CD, entering the terminal and running fsck_hfs -r /dev/disk...

Anyone with similar issues feel free to PM me on this board for more detail.

Thanks again all!

---


---
title: "how to copy files from corrupted drive?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by pdonner on 2007-09-19
Some files in the root system were corrupted.
System boots into maintenance mode.
I am NOT using FAT-32, NTFS or anything to do with Windows.
Ubuntu 6.06 LTS
Drive is ext3 (both corrupted and destination USB)
Broken drive is boot drive in laptop

I boot Live CD and can see file system but want to:

1. Copy my files to an external USB drive which:
     - Shows up in the MTAB as RW (I can look at SB drive but not write to it)
     - System does not permit me to copy files from broken drive to USB drive 
        (says I do not have right permissions)
    
2. Repair the broken drive once I have backed up my files.

Can anyone one help out with this?

I have not been able to find th eright thread to explain how to do this simply.

Thanks.

---

### Post by Vadi on 2007-09-19
To have permissions to copy stuff using the LiveCD, you should start nautilus with root priveleges - so type "sudo nautilus" in the terminal, and then you'll be able to copy stuff from it (makes sense - you do'n't want anyone just loading your system with a livecd and getting access to all your files).

As for the repairing, I believe the e2fcsk tool is the one you want, but I can't check right now.

---

### Post by Irony on 2007-09-19
Type;

[PHP]gksudo nautilus[/PHP]

not sudo nautilus.

---

### Post by Vadi on 2007-09-19
Oops, yes.

---

### Post by MinstrelBoy on 2007-09-19
I used  TESTDISK  when I had partition problems, recovered everything with it. 
Download it with Synaptic Package Manager and run through terminal with  sudo testdisk

---

### Post by pdonner on 2007-09-19
OK.  I forgot about sudo so I mounted the usb drive as rw and then used sudo and cp to do the copying.  Is using nautilus better than this for some reason (e.g. permission state, copying hidden files or some other reason)? 

Also I got a few (not more than to fill the screen) messages such as:

p: will not create hard link `/mnt/usbDisk/home/pdonner/.gimp-2.2/fonts/chat.NET' to directory `/mnt/usbDisk/home/pdonner/.mozilla-thunderbird/xchbcgze.default/extensions/{e2fda1a4-762b-4020-b5ad-a41df1933103}/js/calAttendee.js/DARPA/chat.NET'

Do you think these would cause any serious problems or is this just telling me that a symbolic link was not copied?

Thanks (for the help btw)

---

### Post by pdonner on 2007-09-19
I also notice that all my files on the copied files have root as owner and group.  Is there a way to avoid this?

---


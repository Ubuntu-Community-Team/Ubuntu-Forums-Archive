---
title: "Swap installations around."
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by DonBucknall on 2007-08-28
Hello,

I used ubuntu alot more then my winXP but I just started my study and I need to use windows more often. My windows is installed on 80GB and linux on 500GB but I'd like to swap that around.
I've got the 500GB with ubuntu and 80GB with XP and another usb one.
If it is possible I'd like to create an backup image of ubuntu onto the usb one then overwrite the 500GB one with the winXP and put the ubuntu backup on the 80GB.

I hope you understand, if not you can ask.

Thanks,

Don

p.s. My ubuntu homefolder is I think 450Gb or around that, how do I shrink it to make this possible?

---

### Post by justleen on 2007-08-28
to create a backup image, i'd use dd to create a diskdump of the drive, onto your USB drive.
After thats done, you can use the live cd to do the same for the XP to the 500GB drive.
Beware that you will have to reinstall GRUB AND! adjust the boot.ini file off your windows install! (personly, id say create backup and do a fresh windows install?)

To shrink the /home, you'll just have to cut into it with the Delete button i think :)
use the disk space analyzer to find whats clogging things up
or, 
# du -h /home |sort -n 
that will give you a list of which dirs/files are biggest..


why do you want to swap?
Why not shrink the ubuntu partition, and create an extra data partition which both OSses can access?
Myself, i have 10 gb for XP, and 4GB for ubuntu.. and about 800GB of data discs (all ext3, XP uses the EXT2/3 driver to read/write

---

### Post by DonBucknall on 2007-08-28
Ok, my home folder wasnt that filled up so that won't be a problem.
How do I do the diksdump onto the usb drive? I´ve used linux quite a bit but more graphical so I don't know much about command line.
Can I do this within ubuntu or do I have to boot from knoppix of other live cd to do this?

Thanks,

Don

---


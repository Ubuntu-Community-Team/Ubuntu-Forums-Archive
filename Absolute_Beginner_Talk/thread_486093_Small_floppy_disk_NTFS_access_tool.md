---
title: "Small floppy disk NTFS access tool?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-06-27
I guess this isn't specifically Ubuntu-related so I hope it isn't too out of place to ask here, but I wondered if anyone knew of a tiny linux distro that would let me do the following:

- boot from 1.44Mb floppy
- give me full read / write access to any NTFS partitions on local hard drives.

No need for X, command-line operation would be fine

---

### Post by smoker on 2007-06-27
this isn't a linux app, so may be of no use to you, but it can read ntfs from a floppy:
ntfs4dos : [http://www.bootdisk.com/ntfs.htm](http://www.bootdisk.com/ntfs.htm)

hope it helps

---

### Post by ecs_pf5 on 2007-06-27
It's a great tool, that, and almost does exactly what I want. The only problem is that the write access to NTFS seems a tiny bit flakey - only seems to work with short filenames, and occasionally locks up solid when copying files to an NTFS partition. Usually with larger files.

It's the best match for my requirements so far though.

I came across a floppy-sized Linux distro called 'tomsrtbt' :

[http://www.toms.net/rb/](http://www.toms.net/rb/)
[http://www.toms.net/rb/tomsrtbt.FAQ](http://www.toms.net/rb/tomsrtbt.FAQ)

that claimed full read-write NTFS access, but I also read warnings that NTFS write access using Linux drivers was experimental / dangerous. I don't know whether that warning applied only in the past, to an earlier version of the bootdisk, or whether it's an enduring position

Unfortunately although my Linux-knowledge is increasing rapidly thanks to Ubuntu, I'm still not really up to knowing the difference as regards the above. Is it safe (ish) ?

How possible would it be to take a severe chainsaw to Ubuntu & fit it on a floppy.. just literally enough to boot it with a command line, and some NTFS tool?

---

### Post by smoker on 2007-06-27
hi, i tend to veer on the cautious side where data is concerned, so if something says 'experimental', i make sure i have an up to date backup, just in case!

not knowing why you need a bootable floppy, would a usb distro be any good?
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

also, if you cannot boot from usb, puppylinux will install to usb, and also make a boot floppy that will seek out the usb and load it from there:
[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)

i don't know anything about fitting ubuntu on a floppy, but i would think it very unlikely.

best of luck

---

### Post by BHelts on 2007-06-27
i'm not too sure what you are trying to do, but [DOS 6.22]("http://bootdisk.com/bootdisk.htm") is a bootable floppy with NTFS support.

---

### Post by ecs_pf5 on 2007-06-27
I basically have a dusty pile of hundreds of old floppies, and have been going through them to save the good ones. (only keeping the absolute perfect ones, keep 1, bin 20 sort of thing)

With the 20-odd remaining good ones, I'm rebuilding myself a little set of floppy-based repair tools. So I thought a few boot disks to read & write NTFS on ailing Windows machines was a good idea. Immediately thought of Linux NTFS tool in Ubuntu but then started discovering how thin on the ground, NTFS access tools really are when you start throwing a couple of requirements into the mix like free, small, etc..

> 
[DOS 6.22]("http://bootdisk.com/bootdisk.htm") is a bootable floppy with NTFS support.


is it? never knew..! that's deffo an option then.

With the Linux based tools, seems I get many hd** items in /dev/ but then I have to mount them using an NTFS driver manually. Here I meet the learning curve again! :p

---

### Post by smoker on 2007-06-28
> **ecs_pf5 said:**
> I basically have a dusty pile of hundreds of old floppies, and have been going through them to save the good ones. (only keeping the absolute perfect ones, keep 1, bin 20 sort of thing)

With the 20-odd remaining good ones, I'm rebuilding myself a little set of floppy-based repair tools. So I thought a few boot disks to read & write NTFS on ailing Windows machines was a good idea. Immediately thought of Linux NTFS tool in Ubuntu but then started discovering how thin on the ground, NTFS access tools really are when you start throwing a couple of requirements into the mix like free, small, etc..


hi, here are two apps that i can recommend, one is a bootable bunch of floppy images on a cd, the UBCD, and the other is a bootable live-cd version of windows you legally make yourself, the UBCD4WIN. as more and more pc's don't have floppies, i find them invaluable, the details of both can be found here:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

hope this helps

---


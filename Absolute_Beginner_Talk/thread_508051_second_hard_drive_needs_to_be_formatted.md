---
title: "second hard drive needs to be formatted"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by oconnor on 2007-07-23
Hello, I just installed ubuntu (7.04) on a computer that used to have Windows XP on it.  I had two internal hard drives and I just wanted to install ubuntu over everything and reformat both disks.  Well, after the install I still have one disk that still has my old Windows XP files on it but now I can't delete them.  My question is just this:  How do I partition this other internal hard drive so it's a part of the ubuntu OS and I can read and write from it like usual?  
(thanks!!)

---

### Post by w4ett on 2007-07-23
I keep a copy of the GParted Live CD...it's great for rescuing "broken" systems and is a great addition to your toolbox.

P.S. It will format and partition just about anything.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by PilotJLR on 2007-07-23
The fdisk utility will do this for you... it's important, though, to make sure you format the right device!

Is the windows partition already mounted? If so, this command will tell you what drive it is:
```

mount

```

I would imagine that your windows disk is /dev/sdb, but it's important that you know for sure.

Once you know, then:
```

sudo fdisk /dev/sdb

```
will let you delete existing partitions and make a new one.

the mkfs command then formats it... again, be sure you pass it the right device.

So start with the mount command to identify which disk needs to be partitioned, then post back here is any of the rest is unclear.

---

### Post by oconnor on 2007-07-25
Thanks for your help so far.  This is how far I got...

On my desktop is an icon that says "New Volume" and this is the drive I want to reformat.  Ok, so when I run the "mount" command as you suggest I get quite a list, but one of the choices is this:
"/dev/sbd1 on /media/New Volume type ntfs (rw, nosuid, nodev, umask=222, utf8)"

So I'm assuming that the drive in question is "sdb1". 

Carrying on - I then do "sudo fdisk /dev/sbd1"  and then I get this:
"The number of cylinders for this disk is set to 9657.  There is nothing wrong with this but it is larter than 1024..." and goes on to give a warning about booting.  (I have no idea what ubuntu is talking about here but I would like know.)

So then I did the same command again and I got this "select type (? for auto, 0 for custom)"

And I have the following drive (I got this from the Properties menu):  Vendor =  ATA, Model = WDC WD800JB-00JJ

This was not listed among the selections so I picked "0" for custom and then it said:
"Heads (1-1024, default 255):"

And at this point I don't know what I'm doing so I'm posting back. as you suggested I probably should.

Thanks again!

---


---
title: "Second Ubuntu On Same Hard-drive (Linux-EMC)"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Epic Plecostomus on 2008-04-16
I have Gutsty, in fact I'm posting from it RIGHT NOW.   

I need to install Linux-EMC (Enhanced Machine Controller) to demo for my bosses.  It's based on Dapper.   

Can two different versions of Linux share a hard-drive?  What I'm really asking I guess is it possible to install the other one on here without it over-writing this one?

---

### Post by Meskarune on 2008-04-16
yep. Its called a "dual boot"

google it and I'm sure you'll find what you want. :)

---

### Post by Jon Monreal on 2008-04-16
> **Epic Plecostomus said:**
> I have Gutsty, in fact I'm posting from it RIGHT NOW.   

I need to install Linux-EMC (Enhanced Machine Controller) to demo for my bosses.  It's based on Dapper.   

Can two different versions of Linux share a hard-drive?  What I'm really asking I guess is it possible to install the other one on here without it over-writing this one?
Should be possible as long as you shrink your Gutsy partition to make room for Dapper and then install dapper on that new partition.

If you need more help, just ask.

---

### Post by Epic Plecostomus on 2008-04-16
Ok, currently I have 9.9 gig in use and 25.1 gig free.  If I shrink that to about 10 gig free for the current system (9.9 in use + additional 10) leaving 15.1 will that be enough for the Dapper install?

---

### Post by Epic Plecostomus on 2008-04-16
Ok I freed up two more gig by getting rid of all those Simpsons episodes I had.  :p

Will the partitioning program on the Live CD I'm making resize the partions without killing my system or do I need additional software?

---

### Post by MajinCline on 2008-04-16
The utility you're probably looking for is called GParted. I'm not familiar with Linux-EMC to tell you whether it comes with GParted. Since it's based on dapper, I assume it comes as a livecd. You can always try opening a terminal window and typing "gparted" on the livecd.

If that fails, your options are:
1) Try doing "sudo apt-get install gparted" from the livecd (will require that you have a network connection)
2) Download the gparted livecd ( [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) ) Even if you don't use it here, that is a very useful utility to keep on hand.

---

### Post by Epic Plecostomus on 2008-04-16
Ah ok.

I have Gparted on the laptop I want to install EMC on but when I run, the program stalls out and crashes with the message that my filesystem is "read only".   That's odd because I read and write to that hard drive daily.   Clearly something somewhere is messed up.

Hopefully that won't affect my installation.

---

### Post by Jon Monreal on 2008-04-16
> **Epic Plecostomus said:**
> Ah ok.

I have Gparted on the laptop I want to install EMC on but when I run, the program stalls out and crashes with the message that my filesystem is "read only".   That's odd because I read and write to that hard drive daily.   Clearly something somewhere is messed up.

Hopefully that won't affect my installation.
You could try doing the resizing and the formatting using your already-existing installation.

---

### Post by Epic Plecostomus on 2008-04-17
Tried that.   Same problem.   For some reason I cannot edit or resize this partion using gparted.

---

### Post by joshrobinson on 2008-04-17
> **Epic Plecostomus said:**
> Tried that.   Same problem.   For some reason I cannot edit or resize this partion using gparted.

do it from a live cd, when the drive your trying to resize isnt mounted

---

### Post by Epic Plecostomus on 2008-04-17
> 

root@brian-laptop:/home/brian# sudo gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.



...the hell does this mean?  As I said I read and write to this disk ALL THE TIME.   I was able to install this on my other computer with no problem.   In theory this installation is identical to the one on the desktop so there shouldn't be any differences like this.

So, how do I get permission to alter my partition?

---

### Post by joshrobinson on 2008-04-17
> **Epic Plecostomus said:**
> ...the hell does this mean?  As I said I read and write to this disk ALL THE TIME.   I was able to install this on my other computer with no problem.   In theory this installation is identical to the one on the desktop so there shouldn't be any differences like this.

So, how do I get permission to alter my partition?

did you read my post at the bottom of page 1?

---

### Post by Epic Plecostomus on 2008-04-17
Tried it from two different live CDs, the EMC live CD and the Gutsy live CD.   Same thing.  


Alright it's after midnight, I have to be up in six hours.   :mrgreen:

---

### Post by Epic Plecostomus on 2008-04-17
Last bit of info:  I tried clicking on COMPUTER and sure enough my filesystem icon has a red checkbok it is indeed write protected.   Attempting to unwrite protect it from Naut just gives me a permission denied window. 

...boggle.

---

### Post by joshrobinson on 2008-04-17
> **Epic Plecostomus said:**
> Last bit of info:  I tried clicking on COMPUTER and sure enough my filesystem icon has a red checkbok it is indeed write protected.   Attempting to unwrite protect it from Naut just gives me a permission denied window. 

...boggle.

maybe use a root nautilus to try write protecting it?

```
sudo nautilus
```

---

### Post by Epic Plecostomus on 2008-04-17
> ** (nautilus:8379): WARNING **: Hit unhandled case 24 (Operation not permitted) in fm_report_error_setting_permissions


That's the output in Terminal when I attempt to change the permissions using Naut.  

Ok it's really bedtime now.

Somehow I need to remove the write-protect from my laptop hard-drive so I can edit this partition...

---

### Post by Epic Plecostomus on 2008-04-17
Bump to top.   Any help changing the permissions on this file system?

---


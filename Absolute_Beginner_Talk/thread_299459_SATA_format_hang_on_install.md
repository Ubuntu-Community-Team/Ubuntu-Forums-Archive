---
title: "SATA format hang on install"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Nomadic Logic on 2006-11-14
I saw a lot of SATA troubles when I performed a search, but none matched my issue.

Machine specs:
- AMD64 3200+
- 1 GB RAM
- Boot drive = unformatted SATA (VIA chipset) 120GB
- Secondary drive = unformatted IDE 120GB
- Installing EDGY

I can run the live CD just fine.  When I go to install, it sees both the SATA and IDE drives just fine.  I tell it to install on the SATA and it begins to format and partition, but hangs at 5%.

I have tried it three times, the last time allowing it to run overnight.  No success.  When I left for work this morning, I re-ran the install, telling it to use the IDE, and it seems to be working.  When I left, it was at 15%.

Problem is, I don't know that it's going to boot from the IDE drives.  I believe the BIOS is set to look to the SATA first.  Switching that would be easy, but I think it caused problems the last time I did.

I'd really like to run off the SATA.  Any ideas?

Thanks!

---

### Post by taurus on 2006-11-14
Well, I have a SATA and an EIDE on my machine and I could install Ubuntu on the SATA drive just fine.  However, I didn't use the LiveCD; instead, I used the alternate CD since it gave me more control of what I wanted to do with the partitioning and mounting.  Therefore, I think you should try the alternate CD to see if Edgy would install on your system.  And I assume there is nothing on both SATA and IDE drives, right!

---

### Post by Nomadic Logic on 2006-11-14
There *was* a SuSE 10.1 install spanning both drives, but I wiped all of that out on the first Ubuntu install attempt.  Now both 120GB drives sit empty.

This is the first I've heard of an "alternate CD".  I feel like I didn't do my homework!

Although I had SuSE at one time, I'm still a Linux beginner - I just jumped off SuSE soon after trying it...right around the time they paired up with the devil.

---

### Post by taurus on 2006-11-14
If you have fast network connection (DSL or broadband), it wouldn't take too long to download the alternate CD.  Remember to check to make sure the ISO image is good.  Then, burn it at 4x because fast burning can cause trouble later.  Here's a link for the alternate CD...

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

p.s.  I trashed SUSE from my computer a while back so that thing is not going back on my computers again, ever...

---

### Post by Nomadic Logic on 2006-11-14
Thanks very much.  I'm going to download and burn here at work and see if it installs when I get home.

Thanks again!

---

### Post by taurus on 2006-11-14
You're welcome.  And remember to burn it at 4x...  ;)

---

### Post by anaconda on 2006-11-14
I also had some problems with the liveCD installer (6.10). I solved the problem by partitioning and formatting the hd before starting the installer.

---

### Post by Nomadic Logic on 2006-11-14
Okay here is what I have done:

-  Boot up Live CD
-  Delete all partitions (IDE and SATA)
-  In one case, I left all space unallocated; in another I made a primary unformatted partition
-  Reboot, run the alternate install CD
-  Installed in OEM mode

The install still hangs (at 33% on this one) when trying to work with the SATA drive.

I just had SuSE 10.1 on this two days ago.  Any other suggestions?

Thanks!

---

### Post by SZorg on 2006-11-14
I'm not entirely sure this would work, but you could probaby install it to the IDE drive, then use GParted to copy the install. Reinstall GRUB or change your boot drive and you should be set.

---

### Post by Nomadic Logic on 2006-11-14
I believe the BIOS is set to boot off the SATA.  I wouldn't normally think it would be a problem to change this, but I think I remember having issues when I first built it.

I shouldn't have to go through all that anyway; what if I only had SATA?

---

### Post by taurus on 2006-11-14
I thought we have agreed that you would try out the alternate CD instead of the LiveCD!!!

---

### Post by Nomadic Logic on 2006-11-15
> **taurus said:**
> I thought we have agreed that you would try out the alternate CD instead of the LiveCD!!!

> **Nomadic Logic said:**
> Okay here is what I have done:

-  Boot up Live CD
-  Delete all partitions (IDE and SATA)
-  In one case, I left all space unallocated; in another I made a primary unformatted partition
[b]-  Reboot, run the alternate install CD
-  Installed in OEM mode[/b]

The install still hangs (at 33% on this one) when trying to work with the SATA drive.

I just had SuSE 10.1 on this two days ago.  Any other suggestions?

Thanks!

I did!

---

### Post by Nomadic Logic on 2006-11-15
Well, I've now burned OpenSuSE 10.2 and Fedora Core 6 at work.  I guess I'll load one of them up when I get home.

---


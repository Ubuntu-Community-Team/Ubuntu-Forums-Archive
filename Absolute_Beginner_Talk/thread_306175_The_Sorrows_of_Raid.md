---
title: "The Sorrows of Raid"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by vgrisham on 2006-11-24
Hi,

I really want to switch to Ubuntu (currently using XP-64). I gave it a trial run last night, backed everything up and then attempted to install edgy-64 using the alternative distro. After battling the ubuntu raid configuration utility for a couple of hours, I gave up.

I have an Asus A8N-SLI deluxe mobo. It comes with two bios level raid controllers (a four SATA port Sil3114 and an Nvidia Raid controller that has two IDE ports and four SATA ports). I tried the Sil3114 controller because I read in this forum that nvRaid and Dapper don't play nicely together. 

I've searched the forum, and I keep finding instances of these things not working (or working on install and then not recognizing the array on reboot).

Is Ubuntu (Dapper or Edgy) just not ready for prime-time yet regarding RAID? Has anyone out there gotten this stuff to work? Additionally, would I be better off installing to one disk and then configuring RAID later (or is that even possible)? 

I'm trying hard to jump off the m$ ship. Ubuntu looks great. I just can't get past the raid gatekeeper.

Thanks,
Vaughn

---

### Post by deadgobby on 2006-11-24
Ubie 64 bit is not all that stable yet. 64 bit linux kernal is still a work in progress.  You may want to try the other one. See how it does.
Gobby

---

### Post by vgrisham on 2006-11-24
Thanks for the encouragement. I'm going to try 32-bit Edgy this weekend.

I'm a bit confused about a couple of things, though. Do I delete my bios-based raid array before trying to configure via ubuntu? I'm thinking I shouldn't disable the raid controllers altogether. My only plugs for my sata drives are via these two controllers. If I turn them off, my sata drives are not visible at all.

Also, is there any way to load a raid driver during installation? In XP, you hit F6 during the installer's bootup to indicate that you have a raid driver. Is there a similar procedure in Ubuntu, or does the mobo based controller irrelevant once Ubuntu's software raid takes over?

To recap, I've got four sata drives, and I'm aiming to span and mirror (in xp, that's a raid 0+1 array). I'm guessing, since ubuntu didn't offer that array, Raid 0 or 5 are my only options for data protection. 

Thanks for your help!
Vaughn

---


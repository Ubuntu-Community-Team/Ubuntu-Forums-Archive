---
title: "&quot;Error loading operating system&quot; RAID 1 SATA drives...."
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by slutbinwalla on 2007-08-12
I've looked at the other threads with this issue and mine seems to be unique.

I've got two WD 320 gb drives setup in a RAID 1 config. I installed the latest 64 bit version of Ubuntu I could find (7.04 I think) and it went through the install process just fine.
I took the cd out when I booted back up and it gave me  "Error loading operating system".

I have a gigabyte K8N Ultra SLI mobo with an FX-55, the two WD SATA drives and a 7600 GT.
The drives were clean prior to install, and I'm not dual booting with XP.

Help?

---

### Post by dozch on 2007-08-13
You are saying that you installed Ubuntu on a RAID 1 and I presume that you turned on RAID support in the BIOS. However, the Ubuntu Live cd does not support installing on a 'hardware' RAID (most often called FakeRAID). So Ubuntu was probably installed on one of the drives but there is some problem booting it.

It is possible to install Feisty on a FakeRAID but most forum users will advise you to consider installing Ubuntu on a software RAID. (I ignored this advise in the past, but am now ready to admit that they were right - my hardware is very similar to yours).

The Software RAID Howto is here:
[http://ubuntuforums.org/showthread.php?t=408461]("http://ubuntuforums.org/showthread.php?t=408461")

---

### Post by slutbinwalla on 2007-08-13
Sounds like that is what I'll be needing to do, but it's well over my head.
I'll keep at it though, and if there is something I cannot understand for the life of me I'll head back here.

---

### Post by WebSiteGuru on 2007-08-13
> **slutbinwalla said:**
> I've looked at the other threads with this issue and mine seems to be unique.

I've got two WD 320 gb drives setup in a RAID 1 config. I installed the latest 64 bit version of Ubuntu I could find (7.04 I think) and it went through the install process just fine.
I took the cd out when I booted back up and it gave me  "Error loading operating system".

I have a gigabyte K8N Ultra SLI mobo with an FX-55, the two WD SATA drives and a 7600 GT.
The drives were clean prior to install, and I'm not dual booting with XP.

Help?

I think I know what your problem is. Sound like what I had ran into when I was installing OS(Windows) on a SATA Drive. It is basically the same concept with all SATA Drive.

You had loaded OS using your CD, everything went find and dandy. Then you took out the CD and boot to harddrive, and it comes up with error and said "Error loading operating system".

What you 'll need to do is login to BIOS and change your setting from SATA ON to BOTH (backward compatible mode).  Then that should solved you problem.

---


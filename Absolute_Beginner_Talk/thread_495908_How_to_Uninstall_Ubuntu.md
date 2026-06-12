---
title: "How to Uninstall Ubuntu"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by jjmu15 on 2007-07-08
I have Feisty Fawn installed on my pc using a dual boot system.

Windows is installed on my first hard drive and Ubuntu on the other. I want to completely remove Ubuntu but without losing any information on my Windows hard drive.

I have been looking around and I have found that I can format the Ubuntu hard drive using computer management but the dual boot will still try to load. I do not have a windows disk because stupid pc salesmen stopped including the disk in PC Packages.

I have found a boot disk as that is the way I have been told to remove the dual boot, but I am unsure what this will do. Will it just re-instate Windows as the main OS and boot it automatically or will it revert Windows back to its original state meaning I lose information.

Help needed A.S.A.P please.

Thanks in advance

---

### Post by p_quarles on 2007-07-08
Is this a Windows system recovery disk? If so, yes, that will completely reload your original installation of Windows.

The better bet is just to get the gparted live CD (or you can even use the Ubuntu live CD, it has gparted) and format the second hard drive as NTFS (or FAT32). Windows should recognize it, at that point. 

As far as removing the boot screen ... maybe someone else knows.

---

### Post by jjmu15 on 2007-07-08
no its not a recovery disk just a boot disk. I downloaded it from Microsoft and its only 4.4mb.

Ive found that the MBR (multi boot record) can be reset but I have no idea how to do it. apparantly that would remove the dual boot also :S

---

### Post by p_quarles on 2007-07-08
Yeah, that disk should be perfectly safe, discounting the fact that it's from Microsoft. :-)

Still, I would suggest using Gparted -- it's just a better piece of software. 

Resetting the MBR is indeed what you need to do, but I'm not sure how to do that.

---

### Post by jjmu15 on 2007-07-08
OK thanks. Ill keep looking how to rest the MBR

---

### Post by Vajra Vrtti on 2007-07-08
You can use the [Microsoft Recovery Console]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/recovery_console_overview.mspx?mfr=true") to restore your MBR.
Use the **fixboot** and **fixmbr** commands.

---


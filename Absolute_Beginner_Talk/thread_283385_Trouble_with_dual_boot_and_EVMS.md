---
title: "Trouble with dual boot and EVMS"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by greycity on 2006-10-24
Hey all,

I recently set up a dual boot with an existing XP installation on a SATA HDD and a new Ubuntu installation on a newly installed SATA HDD. For a while, it worked, but not perfectly. The GRUB menu would not start up and windows would boot every time. I had to boot into Ubuntu with the Live CD. For unknown reasons, in trying to get grub to load first, I tried to change the boot order of my SATA disks... and the linux HDD disappeared from BIOS right before my eyes. Fortunately, Ubuntu still recognized the disk and worked fine. At that point, the grub menu started coming up at boot, but when I choose to boot to XP, the XP boot screen comes up, and then the computer restarts, leading back to grub.

Now, when I try to install or start up with the ubuntu live CD, I get an EVMS error on dm-1 (which I have NO idea how to identify, despite hours of research). I suspect dm-1 is the Windows Hdd, but I am reluctant to try fixboot... 

Can anyone diagnose this? If I use Fixboot or Fixmbr, are those changes reversible?

Thanks much

---

### Post by greycity on 2006-10-24
Oh yes,
And I did finally get Bios to recognize the Linux HDD again, but the problems with the Windows HDD and EVMS still remain...

---

### Post by gn2 on 2006-10-24
This thread might help you: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by greycity on 2006-10-31
:D After many hours of ](*,) I finally was able to resolve the evms issue. I disconnected the windows HDD and was able to re-install ubuntu with the live CD. The windows drive will still not boot, even after FIXMBR and FIXBOOT, so I will have to reinstall... which I had hoped to avoid. I'm going to try the seperate disk installs, using BIOS boot device option to pick OS instead of grub.

---

### Post by greycity on 2006-11-03
I found several other posts that cited problems with EVMS and certain HDDs. I finally found my biggest issue was that my motherboard did not support the 3Gbps data rate of my newer SATA drive. I had to install a jumper to slow the drive to 1.5Gbps data rate and the EVMS issue disappeared... as well as an issue with the drive not being listed in BIOS (although it still worked under Ubuntu....)

---


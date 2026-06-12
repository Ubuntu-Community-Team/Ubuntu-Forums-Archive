---
title: "Cannot boot from CD"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by donovan604 on 2007-02-15
Hello all! I just downloaded a copy of Ubuntu for desktop for x86 which is what Im running on,   and I burned the iso image to a disk and set my bios to "Boot From Disk". It still dosnt boot to ubuntu, the system boots to windows immediatly. What am I doing wrong? Thanks for any input.

---

### Post by PPAAUULL on 2007-02-15
How old is the computer? I had a friend that had the same problem and for some reason the CD would not spin up and it would just load windows.

---

### Post by donovan604 on 2007-02-15
Its about a year old. Its a gateway laptop running an AMD Sempron. I have a boot cd for SLAX that does work on this system, so why wouldnt Ubuntu? Its wierd.

---

### Post by PPAAUULL on 2007-02-15
To me it seems like you might have burned it wrong or something got screwed up when you burned the CD. Did you check the MD5 Sum when you downloaded the image?

---

### Post by rsambuca on 2007-02-15
You need to burn the CD as an iso image, not as a data disk.  Open the cd directory in windows and how many files/folders do you see?

---

### Post by PPAAUULL on 2007-02-15
lol common mistake!!!

---

### Post by donovan604 on 2007-02-15
Well Ive tried burning it several times already. Both as ISO image and as standard files disk. As far as that md5sum its there if that means anything. I wouldnt know what to check for. I'm TOTALLY new to Linux, so plz forgive the ignorance.

---

### Post by bikeboy on 2007-02-15
> **donovan604 said:**
> Hello all! I just downloaded a copy of Ubuntu for desktop for x86 which is what Im running on,   and I burned the iso image to a disk and set my bios to "Boot From Disk". It still dosnt boot to ubuntu, the system boots to windows immediatly. What am I doing wrong? Thanks for any input.

Do you mean Boot from disk or boot from cdrom? It needs to be cd.

The other common mistake is when burning the iso, you just burn the file to the disk rather than burning *as* an image. Not sure whether you did that or not but it's worth checking.

Have a look at the iso burning guide and md5 checking guide on one of these sites:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Hope that helps.

---

### Post by PPAAUULL on 2007-02-15
The MD5 Sum is a number to check the ISO against to make sure that it is complete. I would check that before burning another copy, I have a feeling that you might have a corrupt image.

---

### Post by donovan604 on 2007-02-15
11 folders and 9 files in the first window that pops up.

---

### Post by donovan604 on 2007-02-15
Yes I meant boot from CD-Rom.

---

### Post by donovan604 on 2007-02-15
Bikeboy said> The other common mistake is when burning the iso, you just burn the file to the disk rather than burning as an image.

I think that might be the case. Thanks to all. I appreciate your guys immediate responses. Thats amazing!

---

### Post by rsambuca on 2007-02-15
You burned it correctly if you have 11 folders and 9 files.  Your PC is recent enough to boot from the CD drive, which means your BIOS isn't set correctly to boot from the CD drive before the Hard Drive.

---


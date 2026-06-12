---
title: "FAT32 Question..."
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Ubun2User on 2007-11-23
So I want to make my external hard drive FAT32 from NTFS but I have a question, I read that it can't handle files larger than 4GB.  Does that mean that I would not be able to take the files off of my 8GB camera card onto the drive or does that mean I can not put a SINGLE file larger than 4GB on the drive?

Thanks, my all knowing friends on Ubuntu!:guitar:

---

### Post by Pumalite on 2007-11-23
The latter.

---

### Post by Ubun2User on 2007-11-23
Ok cool!  Now I need help reformatting the drive to FAT32.  It is a FreeAgent drive.

---

### Post by bluepowder7 on 2007-11-23
FAT32 isn't efficient with partitions bigger than 8 gigs, so be aware of that.  if you store mostly large files, you'll be ok, but for small files you're going to waste a lot of space (the blocks are huge, so a small file that takes up half a block still uses up a full block, wasting the other half)

---

### Post by Pumalite on 2007-11-23
+1

---

### Post by rsambuca on 2007-11-23
There is virtually NO reason to use FAT32 on a hard drive anymore.  It is an outdated filesystem, which is inefficient, and requires a lot of maintenance.  I strongly suggest using either ntfs or ext3.  Both can be made to read/write with both Windows and linux.

---

### Post by Ubun2User on 2007-11-23
Okay well I have NTFS so how can I use that in Linux?

---

### Post by rsambuca on 2007-11-23
The ntfs-3g drivers allow read and write to ntfs drives in linux.  They are installed by default in Gutsy 7.10.

---

### Post by FuturePilot on 2007-11-23
You may need to install ntfs-config also

---

### Post by Ubun2User on 2007-11-23
Okay well I can't remove or add anything to my NTFS external drive and I have Gutsy...help.

---

### Post by Ubun2User on 2007-11-23
FYI, the external hard drive mounts but like I said, I can't remove or add anything to the drive.

---

### Post by FuturePilot on 2007-11-23
> **Ubun2User said:**
> Okay well I can't remove or add anything to my NTFS external drive and I have Gutsy...help.

> **FuturePilot said:**
> You may need to install ntfs-config also
That will let you configure read and write access to the drive.
```
sudo apt-get install ntfs-config
```

---

### Post by Ubun2User on 2007-11-23
Wow, it worked perfectly.  I just did a test document that didn't work a minute ago and now it works...I am beginning to really love Ubuntu!  lol

---

### Post by Dr Small on 2007-11-23
> **Ubun2User said:**
> Wow, it worked perfectly.  I just did a test document that didn't work a minute ago and now it works...I am beginning to really love Ubuntu!  lol
Ubuntu really simplifies things when it works :)

---

### Post by Ubun2User on 2007-11-23
Man, I can't wait to remove Windows...I am just soooo scared to upgrade to 64 bit...removing everything I have done scares the crap out of me...wanna call me and walk me through it?  lol

---


---
title: "FOSS Disk Cloning Live CD?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Xarok on 2008-03-18
Basically I just want to stick in a Live CD, (Have two HDD's hooked into the computer at the same time) and have one HDD be cloned onto the other. Whether it be Windows or Linux. No backing up and compressing onto DVDs or anything crazy like that.

Does this software exist?

---

### Post by srt4play on 2008-03-18
> **Xarok said:**
> Does this software exist?

Sure it does, there are many options for doing what you want.  Personally I use partimage while booted from the system rescue cd.  [http://www.sysresccd.org]("http://www.sysresccd.org")

---

### Post by Xarok on 2008-03-18
> **srt4play said:**
> Sure it does, there are many options for doing what you want.  Personally I use partimage while booted from the system rescue cd.  [http://www.sysresccd.org]("http://www.sysresccd.org")

Sweet, thanks

How do I go about using partimage?

Can I put in a Windows XP or Ubuntu Linux HDD as a master, then put in a larger blank HDD as a slave and just tell it to clone?

Then use Gparted to resize the partition to fill up the larger HDD?

---

### Post by dsauxier on 2008-03-18
The "dd" command is another option.  Use it with great care, though, because it will wipe your disk if you get the source (if) and destination (of) mixed up.

if the source disk is /dev/hda and the destination disk is /dev/sdb then : 
```
sudo dd if=/dev/hda of=/dev/hdb
```

(if means "input file" and of means "output file")

---


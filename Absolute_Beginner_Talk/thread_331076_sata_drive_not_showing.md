---
title: "sata drive not showing"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by monchot on 2007-01-04
my sata hard disc is not showing. my sata hard disc has all my data. the other hard disc has the operating system.what should i do.

---

### Post by Ecthelion on 2007-01-04
Please post the output of
```
sudo fdisk -l
```
and
```
cat /etc/fstab
```

---

### Post by aberry5555 on 2007-01-04
More than likely it is because linux doesn't have the drivers for your sata or raid controller. If your mobo is presenting your HDD with a raid controller see if there is an option in your bios to switch the SATA controller from "RAID" to either "IDE" or "SATA". It might sound confusing to select IDE but all it means is that the OS will read the sata disk in the same way as an IDE disk but will still be sata speed. I've only really seen this on my mobo and one other so I don't know if this is an option on yours.

If you're not sure how to get in to bios there should be a message at startup telling you the button, though if you know what sata is I'm sure you know anyhow :p

---


---
title: "External hard drives not mounting at boot-up"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by ja06360 on 2007-11-21
Hi
 
I have recently installed Ubuntu 7.04 on to my PC (dual boot with Win2K)
 
I have had no problems with the install and have been able to get everything working okay. I have a couple of external hardrives attached to the machine (formatted to NTFS) and these were being recongnised and mounted at boot-up with no problems for access (shortcuts on desktop and in the 'my computer' directory, etc). I was even able to access and read a number of files from the disks.
 
However, I booted the machine last night, went into Ubuntu and the disks are not there. I have checked the hardware manager and the disks are showing as SCSI devices but are not appearing in the 'my computer directory' or as shortcuts on the desktop.
 
Is there a quick way of getting these mounted and having this automatically occur at boot-up?
 
Cheers

---

### Post by kpkeerthi on 2007-11-21
Can you post the output of 
```

sudo fdisk -l

```

and

```

cat /etc/fstab

```

---


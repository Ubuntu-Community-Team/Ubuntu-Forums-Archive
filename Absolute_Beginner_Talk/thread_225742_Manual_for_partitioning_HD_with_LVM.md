---
title: "Manual for partitioning HD with LVM"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by satimis on 2006-07-30
Hi folks,

I have been googling a while searching for document to partition HD with LVM.  I found many of them on Internet.  However I'm looking for a step-by-step manual for Ubuntu-6.06.

During installation I found the guide-partition there but unfortunately I could not control it to partition HD according to following config


HD - 40G

/dev/hda1 20G approx
VolGroups00
Primary LogVol / ext3 8G
Primary LogVol /home ext3 10G
Primary LogVol swap ext3 1G

/dev/hda2 Free space 20G approx.

So finally I install the OS on the whole HD


# fdisk -l```

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4665    37471581   83  Linux
/dev/hda2            4666        4866     1614532+   5  Extended
/dev/hda5            4666        4866     1614501   82  Linux swap / Solaris
```

# df -h```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  2.1G   32G   7% /
varrun                503M   88K  503M   1% /var/run
varlock               503M  4.0K  503M   1% /var/lock
udev                  503M   92K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
lrm                   503M   22M  482M   5% /lib/modules/2.6.15-23-amd64-k8/vola
```


I'm prepared to start again.  Please advise.  TIA

Remark:  The HD shall be used for dual boot, Linux/Linux

B.R.
SL

---

### Post by keithweddell on 2006-07-30
I don't think you can set up LVM with the standard Desktop Install CD.  Try downloading the Alternate Install CD which does support LVM.  I had to use the Alternate CD when installing onto a system that already had LVM on it.


Keith

---

### Post by satimis on 2006-07-30
Hi keithweddell,

Tks for your advice.

> Try downloading the Alternate Install CD which does support LVM
Whether you meant this package;

ubuntu-6.06-alternate-amd64.iso.torrent 

TIA

B.R.
satimis

---

### Post by keithweddell on 2006-07-30
Assuming you have an AMD64 type processor and you download by torrent - yes.

Keith

---

### Post by satimis on 2006-07-30
Hi keithweddell,

> Assuming you have an AMD64 type processor and you download by torrent - yes.
Yes Ubuntu is now running on a AMD64 PC.  I tried to follow the "guide-partition" without result.

B.R.
satimis

---


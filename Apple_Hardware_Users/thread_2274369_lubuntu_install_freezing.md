---
title: "lubuntu install freezing"
date: 2015-04-19
forum: Apple Hardware Users
---

### Post by allan15 on 2015-04-19
i have an ibook G4, late 2004 that i want to install Lubuntu on.

I downloaded the most recent Lubuntu (14.04) and checked the md5. it's good.

i burned it to a dvd, and booted from it without problem. when i double click to install on the hard drive, it starts the install, and the first time it froze just after asking about partitioning. this time it made it until it asked about my name and a password, but then froze with just part of a window on the screen with the question 'Who are you?'. i can still move the mouse pointer around, but the spinning progress indicator has stopped spinning, and the dvd drive stopped making noise like it's reading the disk.

not sure where to start troubleshooting. any recommendations? can i boot and install from a USB to see if it's the dvd drive that's acting up?

---

### Post by ubfan1 on 2015-04-20
Try the "media check" choice on the DVD.  That might indicate a problem.  Burn the DVD as slowly as possible, unlike a media file, every bit counts.

---

### Post by Rex Bouwense on 2015-04-20
Yes you can boot and install from a flash drive.

---

### Post by bapoumba on 2015-04-21
*Thread moved to **Apple Hardware Users**.*

---

### Post by rican-linux on 2015-04-21
in yaboot you need to set these parameters 

```
live radeon.modeset=1 video=offb:off video=1024x768-32 video=radeonfb:off radeon.agpmode=-1
```

---

### Post by Jos_Antonio_agro on 2015-04-22
Hello, i have the same issue in G5.

---

### Post by luigiburdo on 2015-04-22
Jos antonio do you burn the dvd with the distro at max lower speed and from your mac burner?
another thing ... for not make problems with the partitioner the best is have a blank hd attached as the primary master sata or ata
another thing dont forget to make a 100mb NewWorld partition and the Swap partition

---

### Post by dand1972 on 2015-04-22
> **luigiburdo said:**
> ...another thing dont forget to make a 100mb NewWorld partition and the Swap partition

A 100 MB NewWorld boot partition?  Why 100 when Yaboot only needs 1 MB?

---

### Post by luigiburdo on 2015-04-22
yes but better make more ;-)

---


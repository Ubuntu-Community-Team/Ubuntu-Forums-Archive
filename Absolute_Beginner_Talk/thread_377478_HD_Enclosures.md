---
title: "HD Enclosures"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-03-06
Cheers,

I am planning to buy an HD multimedia USB Enclosure, this device will allow me to play divx files on my TV at the same time can act as my backup disk.

However I was told that it only supports Fat32 and NTFS format for the HD.  I know that ntfs-3g will allow me to read/write into NTFS partitions, I have tried it before, but I dont want to install ntfs-3g on my system as I dont want to maintain a NTFS formatted HD.

My question now is that can I just use Fat32 to format the HD, and will I have read/write access to this device without ever needing to install any special drivers? also can I format the HD to Fat32 within Ubuntu?  And will Ubuntu automount this device when I plug it in the USB port, in the same manner as it automounts my USB Stick?

I am using Kubuntu Edgy Eft.

TIA
Randy.

---

### Post by 3rdalbum on 2007-03-06
> **delphiguy said:**
> Cheers,

I am planning to buy an HD multimedia USB Enclosure, this device will allow me to play divx files on my TV at the same time can act as my backup disk.

However I was told that it only supports Fat32 and NTFS format for the HD.  I know that ntfs-3g will allow me to read/write into NTFS partitions, I have tried it before, but I dont want to install ntfs-3g on my system as I dont want to maintain a NTFS formatted HD.

My question now is that can I just use Fat32 to format the HD, and will I have read/write access to this device without ever needing to install any special drivers? also can I format the HD to Fat32 within Ubuntu?  And will Ubuntu automount this device when I plug it in the USB port, in the same manner as it automounts my USB Stick?

The good news is, you can get read/write access to the Fat32 HD without installing drivers. You can format it to Fat32 using GParted or Qtparted, and Ubuntu and Kubuntu should automount it. All this is as long as it uses the standard mass storage driver.

If it requires special software to be installed on Windows XP, then it probably won't work. If it's "plug'n'play" with XP, then it will work.

Ask the salesperson - I've found that people who work in computer stores have a good idea about Linux. When I bought my external USB hard disk, the salesperson told me that it would work plug'n' play with Linux 2.4 and above; and what filesystem to partition it as (and yep, it works perfectly). Ask the question; if he can't answer it, ask him to call a rep.

---

### Post by delphiguy on 2007-03-06
Thanks for the help.  Ill ask salesrep those details.

---

### Post by indytim on 2007-03-06
If you go the FAT32 route, be aware of the filesize limitations associated with FAT32 (~4G max).

IndyTim

---

### Post by delphiguy on 2007-03-06
Wow, I didnt know that, thanks for the info.

---


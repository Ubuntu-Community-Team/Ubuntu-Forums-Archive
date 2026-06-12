---
title: "Unistall Ubuntu?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by rbsis on 2007-12-27
I want to take the 80 gigs and give it back to Windows, any one know how?

---

### Post by jken146 on 2007-12-27
Use the Ubuntu live CD to format the partition in NTFS, then use it as storage.

---

### Post by CCNA_student on 2007-12-27
Go to [gparted.com]("http://www.gparted.com") and download the Live CD of gparted and burn the image to a CD. Then boot off of that and use it to delete the partition with Ubuntu. 

     Sin Cere,

     CCNA

---

### Post by rbsis on 2007-12-27
Will it re-join the space with Ubuntu?

---

### Post by jken146 on 2007-12-27
You mean expand the partition that windows is on into the freed-up space?  What has so far been suggested won't do it.  Perhaps windows has a tool to expand its partition, I don't know.

---

### Post by LaRoza on 2007-12-27
> **rbsis said:**
> Will it re-join the space with Ubuntu?

Get the Super Grub Disk. See the link in my sig.

Restore the Windows MBR, Advanced->Windows(Advanced) And the first option I believe

Reboot, and Windows should boot without Grub

Go into the Windows "Computer Managment" utility, and go to Disk Management and delete the Ubuntu partitions, and grow the Windows partition to fill the space.

---


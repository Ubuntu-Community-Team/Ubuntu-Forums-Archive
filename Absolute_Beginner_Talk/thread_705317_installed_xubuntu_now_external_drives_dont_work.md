---
title: "installed xubuntu now external drives dont work"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by belovedmonster on 2008-02-23
I installed Xubuntu on another partition last night, then changed Windows to be the default booting OS.

Now I find that neither XP nor Xubuntu will work my 500GB external drive or my 1GB pendrive. They were both working on Xubuntu earlier, and both worked on XP before I installed Xubuntu.

Windows sometimes recognises that I've plugged them in but does not allow me to view any of the contents. Xubuntu is showing no signs of them what so ever, even after using sudo fdisk -l

I've got lots of important stuff on these drives so I'm stressed out.

As I say, they both worked with Xubuntu earlier, so I dont know if it was changing Windows to be the default OS that has made the difference. :(

---

### Post by dstew on 2008-02-23
> I installed Xubuntu on another partition last nightDo you mean you created a new partition on your system? Did you have Xubuntu installed before? Do you have two Xubuntu partitions? Did you have single-boot Xubuntu, and then installed WIndows?

Check your BIOS and see if you can disable Legacy USB support. Neither WIndows nor Ubuntu uses that. Maybe that will help.

Changing Windows to the default OS in grub should not cause this problem.

---

### Post by belovedmonster on 2008-02-23
I had Windows and two other partitions which I used for media files, I formatted one of those partitions and used it for the Xubuntu root and Swap partitions.

I have a USB keyboard so I switched on legacy USB support a few months back because the keyboard wasn't working prior to booting into windows. But my external drives have worked fine all that time.

---

### Post by belovedmonster on 2008-02-23
It seems to have fixed it self. It is mounting them OK now after I tried connecting them with different USB ports (which worked) and then moving them back to the original ones. Weird! :guitar:

---


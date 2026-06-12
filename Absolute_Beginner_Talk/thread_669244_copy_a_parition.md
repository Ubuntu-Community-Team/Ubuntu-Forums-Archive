---
title: "copy a parition?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-01-16
I need to copy my home partition so i can install vista again :(  I only have my factory restore disks and so I need to make my computer back to how it was when i bought it and then copy my /home back to the disk and reinstall gusty. How would i do this?

thanks :)

---

### Post by ByteJuggler on 2008-01-16
Where do you want to copy your /home folder to?  Have you got an external disk to copy/backup to or perhaps a DVD writer on that machine?  How big is your home?  ("du -sH /home/user" where "user" is your username will tell you)

---

### Post by rockinlinux on 2008-01-16
I should also add. I have a usb hard drive to copy to but my system wont boot from USB so i need to know if something like partimage has USB supprt.

---

### Post by rockinlinux on 2008-01-16
Right now my /home partition is 20GB but only 5GB is used. I have both a external USB drive and a DVD writer. Do you know if i can burn a DVD-9 in partimage from the system rescue disk?

---

### Post by rockinlinux on 2008-01-16
Anyone else have experience with this?

---

### Post by Golem XIV on 2008-01-16
If I understood you correctly, you want to install Vista first (from the recovery DVDs) and then install Ubuntu again?  On the same computer?

As for copying, if you have an external USB drive, just plug it in - Ubuntu will automatically mount it - and copy everything over.

---

### Post by rockinlinux on 2008-01-16
Yeah i understand this. And yes to the same computer becuase the recovery disks dont give an option of what partition to install to. I want to copy my *partition* not just the files unless there is a way i can copy them back to a new /home partition and then use that. I want at the end Vista, ubuntu with the SAME home partition i have now. 

Thanks :)

---

### Post by kpkeerthi on 2008-01-16
> the recovery disks dont give an option of what partition to install toAre your sure?

Anyway, use partimage (from [system rescue cd]("http://sysresccd.org/")) to 'image' both  root and home partitions. Reinstall vista. Use vista's disk manager to shrink NTFS partion. 
Use gparted (from sys resc cd) to create partions for root, home and swap. And then restore the images back to respective partitions using partimage. Reinstall grub.

---

### Post by rockinlinux on 2008-01-16
well even if they do ask what partitions i already have 3 primarys and if i remember right vista uses two...i could be wrong.

so dose partimage allow me to plug my USB drive? and also will i be able to copy those paritions to a extended?

thanks very much :)

---


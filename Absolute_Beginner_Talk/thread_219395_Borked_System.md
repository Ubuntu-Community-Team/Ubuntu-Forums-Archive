---
title: "Borked System"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by cyricthemad on 2006-07-19
Ok, this has been a really friggin long day ](*,) .  At this point I just want to get my files from my linux partition and start over.

I have two physical hard drives.  Right now, hda is my Windows drive.  hdb is my ubuntu drive.  It is formated as 1 -> ext3, 2 -> extended, 5 -> logical lvm.  I have tried installing ubuntu again onto hda and mounting hdb into that and pulling my files, reloading grub, gag, and live cds (xubuntu, ubuntu, dsl) to no avail.  The closest I have gotten is from the 5.10 install cd rescue boot option.  From there I can at least see my files and I know they are there.  Unfortunately, I don't know how to... rescue them.

Any assistance at all would be greatly appreciated.

---

### Post by OU812 on 2006-07-20
Have you tried adding your hdb partitions to your fstab on hda? As an experiment, you could try adding one partition then doing a mkdir /path/partition. Then reboot and try it out. (I prefer rebooting to mounting via command line).

john

---

### Post by nalmeth on 2006-07-20
1. What is 'borked' with your system? Do you have links to other threads you made for assistance with this?
2. Did you say you removed windows and tried installing ubuntu on hda? Is this system usable?
3. Are your files stored simply in your home folder in the borked installation?

---


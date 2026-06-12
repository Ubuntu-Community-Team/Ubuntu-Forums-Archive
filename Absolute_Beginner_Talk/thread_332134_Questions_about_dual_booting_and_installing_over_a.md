---
title: "Questions about dual booting and installing over another Linux distro"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by infernon on 2007-01-05
Hello everyone, 

I currently run Windows XP Professional and Fedora Core 6 on my machine.  What I'd like to do is to install Ubuntu over Fedora Core 6, but I am unsure of how to partition the drive.

After inserting the Ubuntu CD and choosing the option to partition manually, I am presented with the following:

partition          filesystem          flag

/dev/sda1       ntfs                   boot
/dev/sda2       ext3                  
/dev/sda3       unknown            lvm


I don't know what /dev/sda2 is.  This is a Dell laptop, but I removed the little partition that comes factory installed when I rebuilt the thing after first receiving it, so I'm positive that it isn't that.  I didn't know if Grub (that's what Fedora was using) actually took up a small part of the hard drive when it is installed.

I am also pretty sure that /dev/sda3 is the partition that I installed Fedora Core 6 on.  

My questions are:

1. Does anyone know what /dev/sda2 might be?  It's relatively small (roughly 70 megs).
2. Which partitions can be safely deleted while allowing me to still boot into Windows?
3. Is there anything else that I need to know before carrying out this operations?

I have ensured that all of my data is backed up as well-- just in case something goes wrong:)

---

### Post by taurus on 2007-01-05
Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here!

```
sudo fdisk -l
```

---

### Post by Sasa_Ivanovic on 2007-01-05
sda2 is a swap partrition, i don't know what it's used for, but it's needed.
just format the sda3, and click next. gparted will automaticly allocate apropriate OS's to partrtions.

---

### Post by Bachstelze on 2007-01-05
It seems the other distro was installed using the Logical Volume Manager, /dev/sda2 being the /boot partition and /dev/sda3 the actual LVM volume. You can safely delete the two of them if you want to do a standard Ubuntu install - LVM might be a little confusing if you're new to Linux.

EDIT : No, /dev/sda2 is not a swap partition since it's ext3...

---

### Post by infernon on 2007-01-05
So is it safe to assume that I can just delete the two partitions, HymnToLife, and click the next button to have Ubuntu automagically set itself up or do I need to manually configure partitions?  Also, will Grub be reinstalled so that I can set Windows to boot and will I be able to set Windows up as the default OS to boot?

Thanks!

---

### Post by manutdfan2850 on 2007-01-05
> **taurus said:**
> Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here!

```
sudo fdisk -l
```

do what he says :)

---

### Post by Bachstelze on 2007-01-05
I've ner used the Ubuntu installation from within the Live CD but I guess it will offer the possibility to "Use the largest continuous free space". So yes, just delete those two partition, choose that option in the next screen and it should install without further configuration.

EDIT : What would be the use of a *fdisk -l* ? Didn't he post his partition table already ?

---

### Post by Sasa_Ivanovic on 2007-01-05
> **HymnToLife said:**
> 
EDIT : What would be the use of a *fdisk -l* ? Didn't he post his partition table already ?
maybe he made typos.

---

### Post by infernon on 2007-01-05
No typos:)  I was just procrastinating and waiting before I booted my machine with the live cd again!  Here goes:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device       Boot   Start       End      Blocks       Id   S ystem
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650        7662      104422+  83  Linux
/dev/sda3            7663        9729    16603177+  8e  Linux LVM

Sorry about the display there, I can't get it to line up right...

---

### Post by infernon on 2007-01-05
is no one responding because they're not able to read the pasted text?

---

### Post by infernon on 2007-01-05
OK.  I rebooted.  Installed from the Live CD.  Here is what I did.

I deleted sda2 and sda3.  I created a 256 mb swap partition and used the rest of the free space to create an ext3 partition.  I installed and grub boots both Windows and Ubuntu.  Now, I just need to figure out how to change the default OS that boots....

---

### Post by Bachstelze on 2007-01-05
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

### Post by infernon on 2007-01-08
Thank you.  I was able to get it running with that document.  Thanks again for your help.

---


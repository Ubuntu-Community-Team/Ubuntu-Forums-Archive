---
title: "Changing ubuntu partition."
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by varun on 2006-03-16
I have two HDD's one of 8.4 GB and the other of 160GB. I had ubuntu 5.10installed on the 8.4GB HDD, later I created a partition on the 160GB HDD,installed ubuntu on it and deleted the 8.4GB partition from windows. The problem is that everytime I remove the 8.4GB HDD from my PC I get a GRUB error even though this HDD has been formatted and is completely blank. Everything works fine if I keep the 8.4GB HDD connected. I want the grub to load without the 8.4GB HDD connected to my PC. Please help.

---

### Post by mlind on 2006-03-16
You will need to wipe out the MBR of the old HDD.
GRUB is still there, but it needs to be removed.

I'll see if I can find *dd* a command for you that does the job.

---

### Post by mlind on 2006-03-16
You have to _extemely_ careful with this command. It will completely erase the MBR
of the specified HDD. You have to use *sudo fdisk -l* to
find out what device is your **old** HDD. then replace the ??? with the device.

```

dd if=/dev/zero  of=/dev/??? bs=446 count=1

```

other option is to use dos bootdisk with fdisk utility, and excecute *fdisk /mbr*.
If you choose this one, you should fist disable the primary HDD from bios,
so it won't wipe out the wrong MBR.

---

### Post by varun on 2006-03-16
I tried the first solution and still the same problem exists. I am getting GRUB error 21.

---

### Post by mlind on 2006-03-16
what does the output of
*sudo fdisk -l* look like?

what command did you execute?

---

### Post by kaffeine on 2006-03-16
look in /boot/grub/menu.lst - OS list would be at the end. each grub option would have disk/partition info like so (hda0,0) which means disk #1, partition 1 (numbered 0). if your 160GB is your primary hard drive, then it should say (hda0,X) for Ubuntu where X is some number. if it says (hda1,X) then change it to hda0 (you may have to do it for the windows option as well if it says hda1), and reboot without the 8.5GB (and of course with the 160 GB connected as the primary drive).

---

### Post by TrendyDark on 2006-03-16
Okay, there's a simple way to fix this. Remove the 8gig drive. Boot up using the Ubuntu Installation CD. When you  get to the screen where it says "hit enter to boot" (or something to that effect) first type "rescue" then press enter. Follow the instructions on the screen until you come to a list of partitions on your hard drive. Select the partition that contains Ubuntu.

This will now bring you to a command line. type:

```
grub-install /dev/hda
```

 this will write grub to your hard drive's MBR.

---

### Post by mlind on 2006-03-16
If he has GRUB on the MBR of the both drives, does grub-install remove the old one?

---

### Post by varun on 2006-03-16
[QUOTE=mlind]what does the output of
*sudo fdisk -l* look like?

what command did you execute?[/QUOTE]

The output was
```
  Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1092     8255488+   c  W95 FAT32 (LBA)
```
along with other HDD's

I executed  ```
dd if=/dev/zero  of=/dev/hdb1 bs=446 count=1 
```
The drive was shown as unformatted when I logged into windows.

@TrendyDark
Should I also back up my data before executing this command?

---

### Post by mlind on 2006-03-16
ah, I got it.

The GRUB is now on your old HDD's MBR right? Even thought there are no visible
partitions, the MBR exists. You need to do boot in ubuntu and execute the grub-install script like TrendyDark said. Just make sure that destination is your new HDD.

Then you should remove your old HDD from Bios' boot order list, so It won't use
the old drive as default boot device.

---

### Post by varun on 2006-03-17
Thank you guys for your help. I finally resolved the problem by following TrendyDark's advice and changing boot priority. :)

---


---
title: "mount: wrong fs type"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by tuatha1337 on 2007-12-11
Hello folks, I've tried my damndest to find the solution to this on the various internet forums to no luck. My appreciations and gratefulness if you can help me on this. =)

I recently purchased a Western Digital Raptor X SATA 150GB 1.5Gbps Hard Drive (1500AHFD).
My problem is getting this drive installed in my Kubuntu 7.10.
I've partitioned the disk by typing sudo fdisk /dev/sda and creating a single partition on the drive.
fdisk -l gives me:
```
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93afb520

```I have two other IDE drives which i can print the data if needed.

When I type in 
sudo mount -t ext3 /dev/sda1 /mnt/rapthd
I get this error
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I'm fully aware that I'm a complete n00b at linux in general (I've had this system less than a year).

Help?

---

### Post by The Cog on 2007-12-11
That doesn't look like it has any partitions to me. Can you double-check with this command:
**sudo sfdisk -l**
 or use gparted to double-check?

P.S.
After creating a partition with fdisk, you need to format it with the command:
**sudo mkfs.ext3 /dev/sda1**
Gparted formats the partition as it creates it so you don't need mkfs after gparted.

---

### Post by skymera on 2007-12-11
if its new it wont have a filesystem, so need to format.

also ive bought a raptor, havent recieved yet, my mummy is holding till Xmas, but whats the performance like of it?

i wanna install ubu on it and just curious.

sorry for OT btw.

---

### Post by tuatha1337 on 2007-12-13
Well, the performance would be great if I could get it to run... 

sudo sfdisk -l gives me this
```
Disk /dev/sda: 18241 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+  15804   15805- 126953631   83  Linux
/dev/sda2      15805   18240    2436   19567170   82  Linux swap / Solaris
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
```

I tried something new and directly installed my kubuntu 7.10 on the Raptor drive. Install goes great, but when I try to restart and boot from the drive itself, it goes no farther than a blinking line on a black screen after the BIOS options....

---

### Post by kpkeerthi on 2007-12-13
Are you not getting the GRUB menu?

Try reinstalling GRUB with the Live CD:
1. Boot with the Live CD
2. Open a terminal window
3. Type "grub"
4. Type "root (hd0,0)"
5. Type "setup (hd0)"
6. Quit grub by typing "quit".
7. Reboot.
(Remove Live CD)

---

### Post by mcduck on 2007-12-13
> **tuatha1337 said:**
> Well, the performance would be great if I could get it to run... 

sudo sfdisk -l gives me this
```
Disk /dev/sda: 18241 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+  15804   15805- 126953631   83  Linux
/dev/sda2      15805   18240    2436   19567170   82  Linux swap / Solaris
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
```

I tried something new and directly installed my kubuntu 7.10 on the Raptor drive. Install goes great, but when I try to restart and boot from the drive itself, it goes no farther than a blinking line on a black screen after the BIOS options....
None of those partitions is marked as bootable..

---

### Post by tuatha1337 on 2007-12-13
Hmmm, on step 4, it says "Error 21: Selected disk does not exist"
Tried various combinations (sda, hda, hd1, hd2, etc) to no avail.

---

### Post by tuatha1337 on 2007-12-13
How do I make it bootable?

---

### Post by tuatha1337 on 2007-12-13
Would it matter greatly if I had connected the drive into the second SATA Port? (out of the two SATA ports I have) And that I have two IDE drives, one master and one slave?

---

### Post by mcduck on 2007-12-13
> **tuatha1337 said:**
> How do I make it bootable?

With fdisk ot Gparted.

---

### Post by tuatha1337 on 2007-12-13
```
Disk /dev/sda: 18241 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  17507   17508- 140632978+  83  Linux
/dev/sda2      17508   18240     733    5887822+   5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      17508+  18240     733-   5887791   82  Linux swap / Solaris
tuatha@tuatha-desktop:~$          

```

How's that? I opened it up with fdisk and toggled the bootability on partition 1.

EDIT: Updated with proper info

---

### Post by mcduck on 2007-12-13
looks better. I wonder why the fdisk output doesn't show the other drives you mentioned that you have. Did you just leave the information out when posting the output here?

Anyway, try this instruction for installing Grub: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

edit. I just read through the thread again and it seems we are a bit lost from the original track now.. So you already have a working Ubuntu install, and you just wanted to get that drive mounted there? Then it's not really useful to play around with Grub. All you need to do is to partition the disk the way you want, and format the partitions with your file system you want to use (like Ext3). After that you should be able to mount the drive, and then add entry for it in your /etc/fstab to get it mounted automatically on every boot.

---

### Post by tuatha1337 on 2007-12-13
I simply left the other drives out of my fdisk output, didn't think it was important.

The reason grub may have come up is because I also attempted to install kubuntu from my live cd to the raptor drive, however, when I try to boot from the raptor drive after the install (which apparently runs fine), all that shows up is a blinking line (command prompt type, but takes no input).

I would like to have my primary OS on the raptor drive, if possible.

---

### Post by tuatha1337 on 2007-12-13
Woohoo! I've managed to mount the drive onto my system, and can access it through my original Kubuntu OS. However, does anyone have input at this point as to how to move my current OS onto the drive or install a new one and boot from it?

---

### Post by mcduck on 2007-12-13
> **tuatha1337 said:**
> Woohoo! I've managed to mount the drive onto my system, and can access it through my original Kubuntu OS. However, does anyone have input at this point as to how to move my current OS onto the drive or install a new one and boot from it?

While it should be possible to copy the OS from the old drive into new on with 'dd', and then edit both /etc/fstab and /boot/grub/menu.lst, I think it's most likely easier to make a new install to the new disk and then just copy contents of your home directory to the new home.

If you want to play it safe you could just remove the old disk and put the new one in it's place, then do the install, put the old disk in and add it into /etc/fstab. This way you could be sure that even if you have troubles getting the new install to work you could just plug the old drive back and at least have a working system..

Of course it _should_ just work by putting the Ubuntu CD in  with both disks attached and select the new disk as destination when doing the install. But I think that way the installer might actually put Grub in the MBR of the old disk, so if you'd remove the old disk at later time your system wouldn't boot any more. I'd rather keep the system disk as the first disk..

---


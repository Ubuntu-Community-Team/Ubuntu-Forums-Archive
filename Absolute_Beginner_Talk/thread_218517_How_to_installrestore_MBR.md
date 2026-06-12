---
title: "How to install/restore MBR ?"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by DThurman on 2006-07-18
Gah,

I blew away my MBR due to attempts to setup MultiBoots.

What are the instructions to install the MBR to the Ubuntu
drive from within the Rescue CD?  I tried to grub-install
thinking that the MBR would be installed but perhaps that
is is a seperaste step?

Thanks!

---

### Post by Jagot on 2006-07-18
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by DThurman on 2006-07-18
Unfortunately, the instructions provided in the link does not work because every time you try to "Save" it returns with no error message at all, so you are forced to "<Go Back>". I tried to "Finish the installation" only to be returned back into the "paritioner" menu.

Is there a manual way to do this instead?

---

### Post by starscalling on 2006-07-18
the key bits in the process:
1. manually partiton
2. select partitions and to the mount points
3. make sure all are set do not format // keep data
4. select and allow formatting on swap partition
5. push teh continue

---

### Post by codejunkie on 2006-07-18
boot with an ubuntu live cd if you have one when you get to the desktop open the terminal and chroot the ubuntu partition like this 
```
sudo fdisk -l
```this will list your partition info mine looks like this

```

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         122      979933+  82  Linux swap / Solaris
/dev/hdb2   *         123        4998    39166470   83  Linux

```

you need to find your root partition, you can usually identify your root partition by the id on a standard install it should be 83 and the system type will be Linux, now you need to mount the partition like this.

```
sudo mkdir /ubuntu
```
this will create a mount point, now mount it  like this im going to use mine as the example but replace the /dev/hdxx with your actual drive location.  

```
sudo mount /dev/hdb2 /ubuntu
```
and chroot into the drive like this 
```
sudo chroot /ubuntu
```

now run the command 
```
grub-install /dev/hda
```
this should reinstall grub to the mbr if you have any trouble with this let me know and i'll try my best to help.

---

### Post by DThurman on 2006-07-18
First, thanks to all who replied!

I restorted to using the following:

1. Install Live CD
2. Start a terminal window, become superuser
3. Find the linux drive and partition w/ fdisk -l
4. Start Grub
5. Type: root(hd0,0) - or wherever your /root parition is located
6. Setup (hd0)       - or whichever drive your linux is located
7. Reboot or reset system.

This seems to be much faster and easier.

Now...  back to my ORIGINAL issue before I broke it :-) ....

================================================================

I am trying to get my System Commander to boot this Ubuntu that is located on my SECOND drive... (My first (primary) drive is all windoes and System Commander is in the first partition)

System Commander actually recognized Ubuntu immediately before and provided the selection list for it but chosing it failed to boot it.  It keeps saying: "You may have a corrupted MBR" but obviously if I disable the first (primary) drive, I can boot Ubuntu but the minute that I include the first (primary) drive back in - it fails.

Sigh....  I called Vlan (System Commander) and they tell me NOT to install Grub as the MBR on the second drive 1st partition but instead to install Grub in the 2nd drivem 2nd partition (/root).

So - what I did, was to create TWO partitions in the 2nd drive: (D2:P1): /boot = 100MB and (D2:P2): / = 10GB and so when I installed Ubuntu, I did this while disabling the 1st drive so as not to whack it out of commision - and obviously when I followed the complete install procedure for Ubuntu, it puts the Grub MBR on the 1st parition of the 2nd drive, or (D2:P1) /boot" which is what Vlan says NOT to do.

So - I guess I am trying to do is to figure out how to install Grub and put the MBR on (D2:P2) /root.

I am wondering if I should issue:

grub-install /dev/hdc2 ???  I will probably blow away the MBR but now that I can restore it, I should probably give it a whirl... :-p

Any advice?
Dan

---

### Post by DThurman on 2006-07-18
OK!  I am COMPLETELY FINISHED!!!  YAAAA!!!!

Solution:

1) Boot up Ubutu in standalone 2nd drive w/ 1st drive disabled
2) Log in the system the normal way.
3) Open terminal window, become superuser
4) Edit grub config file: /boot/grub/menu.list
   Change all root(0,0) to root(1,0) because
    that is where grub's files are.
5) Type: grub-install /dev/hdc2
   Note: 2nd drive has: hdc1="/boot", 100MB, hdc2="/", 10GB
6) Reboot system.

System Commander now works.

---


---
title: "A new Grub  problem with SATA+IDE"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2007-12-26
I have Ubuntu 7.10 installed on my SATA HD. I have just added another HD, an IDE drive onto the same box, Windows XPPro is on it. 
Now I'm having trouble getting Grub to sort it all out. I have the Super Grub CD and have tried most of the combinations it has suggested. My research tells me that an IDE and a SATA on the same system causes Grub problems -BUT- there are work arounds.
Can someone help out here?

---

### Post by chewearn on 2007-12-27
First, are you still able to boot to ubuntu HD, or XP HD (when both HDs are installed)?
Is grub menu appearing?  Or you got grub error 17 or something?

---

### Post by kindafunnylookin on 2007-12-27
When they are both plugged in I can get the old Grub to appear using Super grub. Neither OS will open then. that is the only message grub gives me. I'll plug everything back in now to be sure. I can get either to open only by upluging the other.

---

### Post by kindafunnylookin on 2007-12-27
OK. I was wrong. Now grub will open the SATA drive with Gutsy 7.10 but when asked to open IDE with windows it gives > Error 17

---

### Post by chewearn on 2007-12-27
Ok, just to understand the current situation:
1. you have both HDs in the system now
2. you can boot to ubuntu
3. you cannot boot to Windows

Does this sum up the problem now?

---

### Post by kindafunnylookin on 2007-12-27
> **AstalaVista said:**
> Ok, just to understand the current situation:
1. you have both HDs in the system now
2. you can boot to ubuntu
3. you cannot boot to Windows

Does this sum up the problem now?
That's right, and that is using grub.

---

### Post by chewearn on 2007-12-27
Then you need to check that menu.lst has the correct entry for XP.

Boot into Ubuntu post the output of:
```
cat /boot/grub/menu.lst
```

and 
```
sudo fdisk -l
```

---

### Post by kindafunnylookin on 2007-12-27
> **AstalaVista said:**
> Then you need to check that menu.lst has the correct entry for XP.

title           Ubuntu 7.10, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title           My Windows XP on the IDE hard drive
root            (hd1,0)
configfile      /boot/grub/menu.lst


Boot into Ubuntu post the output of:
```
cat /boot/grub/menu.lst
```and 
```
sudo fdisk -l
```
peter@Gutsy7_10:~$ sudo fdisk -l
[sudo] password for peter:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006f4f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris
peter@Gutsy7_10:~$

---

### Post by chewearn on 2007-12-27
> **kindafunnylookin said:**
> peter@Gutsy7_10:~$ sudo fdisk -l
[sudo] password for peter:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006f4f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris
peter@Gutsy7_10:~$

Looks like ubuntu cannot see the XP harddisk.  Is the harddisk recognised by the BIOS?  I.e. if you go into BIOS, does both HDs showed up?

---

### Post by kindafunnylookin on 2007-12-27
yes they do

---

### Post by chewearn on 2007-12-27
Ok, sorry this is now pushing what I know... need asistance.  Anyone else?:(

One more thing to try:
```
dmesg | grep ata
```

Should tell you whether the ATA drive is found and configured.

---

### Post by kindafunnylookin on 2007-12-27
Um, with the IDE powered I cannot even open the BIOS. My motherboard reports 'entering setup' then I just get a blank screen. 
I have to go to work now and will open the box when I get back and see what's going on. Maybe the power end of the IDE belt is out.
Thank you for getting me this far.............to be continued...........

---


---
title: "GRUB error :("
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by 2Dum2Kno on 2008-01-06
ok i recently installed ubuntu 7.10 and grub wont load on my new Acer Windows Vista Laptop :(
What should i do?
HD0 wouldnt install it

---

### Post by ryanVickers on 2008-01-06
Get a copy of Super Grub Tool (it's a bootable CD/Floppy, which ever you choose)

It lets you restore/install grub to a certain partition, the Ubuntu one recommended, and/or the MBR.  Also, you can boot the CD and then from there choose to boot a certain partition, like Vista (heaven forbid) or Ubuntu :D

---

### Post by 2Dum2Kno on 2008-01-06
> **ryanVickers said:**
> Get a copy of Super Grub Tool (it's a bootable CD/Floppy, which ever you choose)

It lets you restore/install grub to a certain partition, the Ubuntu one recommended, and/or the MBR.  Also, you can boot the CD and then from there choose to boot a certain partition, like Vista (heaven forbid) or Ubuntu :D

Thanks;

could it be possible im using the wrong version of the live CD?
also, witch is the best version to use?

---

### Post by ryanVickers on 2008-01-07
Any version of Ubuntu should work fine - I would recommend 7.04 or 7.10 if everything works.

as for grub, I believe Ubuntu comes with 1.5, and thats also what the tool installs... its good

---

### Post by 2Dum2Kno on 2008-01-07
ok thanks, but i dont understand this GRUB super thing
it says linux not found

---

### Post by 2Dum2Kno on 2008-01-07
I CANT FIND THE OPTION :(

can you tell me where it is ive looked in windows & BIOX


REFFERING TO Boot Master

---

### Post by ryanVickers on 2008-01-07
There should be an option in it somewhere to restore/install GRUB to the MBR or the Ubuntu partition.  The booting straight to a partition might not work....

---

### Post by philinux on 2008-01-07
Here's a good howto for loading grub to your machine from the live cd.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by 2Dum2Kno on 2008-01-07
ok, im now gonna use FREEBSD

i got the data in, but  i cant figure out how to load it, it keeps coming up in the ista boot manager and says linux not found :(

---

### Post by ryanVickers on 2008-01-07
Can you not just reinstall it using the Grub tool, then boot the live CD and change the /boot/grub/menu.lst file to be correct (if it isn't)???

If your doing this properly, it's pretty much guaranteed to work... if it still won't boot, then something else is severely damaged!

---

### Post by 2Dum2Kno on 2008-01-07
> **ryanVickers said:**
> Can you not just reinstall it using the Grub tool, then boot the live CD and change the /boot/grub/menu.lst file to be correct (if it isn't)???

If your doing this properly, it's pretty much guaranteed to work... if it still won't boot, then something else is severely damaged!

knowing my luck, it probably severely damaged

---

### Post by ryanVickers on 2008-01-07
Because it doesn't matter what happens to mine - windows overwrites it, updates screw it up, etc. I just re-install it using the grub CD, boot the Ubuntu CD, change the partition numbers, and it all works fine! I would bet your just not doing it right...

---

### Post by 2Dum2Kno on 2008-01-07
> **ryanVickers said:**
> Because it doesn't matter what happens to mine - windows overwrites it, updates screw it up, etc. I just re-install it using the grub CD, boot the Ubuntu CD, change the partition numbers, and it all works fine! I would bet your just not doing it right...

well i made the partition with is on SDA5 and installed as an ext3 on the drive it all installed correctly except the last few percent witch was the boot loader...
its still being stupid on me tho

ill post my freebsd code in a few sconds gotta log into windows

---

### Post by 2Dum2Kno on 2008-01-07
```
# NeoSmart NeoGrub Bootloader Configuration File
#
# This NeoGrub menu.lst file should be located at \NST\menu.lst of the boot drive.
# Please see the EasyBCD Documentation for information on how to create/modify entries

title Ubuntu
find --set-root /boot/vmlinuz-2.6.17-10-generic
kernel /boot/vmlinuz-2.6.17-10-generic ro root=/dev/sda5
initrd /boot/initrd.img-2.6.17-10-generic
```
plese tell me what im doing wrong

---


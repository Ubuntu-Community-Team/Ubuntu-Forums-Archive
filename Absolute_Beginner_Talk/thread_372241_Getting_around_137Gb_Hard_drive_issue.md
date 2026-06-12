---
title: "Getting around 137Gb Hard drive issue"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by uclalinux on 2007-02-27
I have a 693btx mother board and a sea gate 250 Gb ata harddrive, my problem is that the hard drive is too big for the bios to read it and will prevent the computer from booting. i think there is someway to get around this using fstab. Does anyone know?

---

### Post by magicfab on 2007-02-28
If the BIOS prevents booting, that's way before any Linux interaction, much less /etc/fstab file helping it.

---

### Post by uclalinux on 2007-02-28
Ya, I know. but I think I can disable the hard drive detection in my bio boot, then some how when the kernel and other things boot in ubuntu they can detect the hard drive. I and one of my room mates remember reading something about how you can get around this issue in Linux by doing something special to the fstab so that even if the motherboard isn’t made for the larger hard drive that Linux will still mount it allowing it to be used.

---

### Post by pistcivet on 2007-02-28
Used to be, the BIOS could only boot from a partition within the first 1024 cylinders.
The fix was a small separate /boot partition defined as the first on the disk.
But that's ancient history. How old is this motherboard anyway?

---

### Post by hardyn on 2007-02-28
is their possiblly a firmware upgrade for that motherboard?

ebay a new motherboard?  socketA motherboards are 50$ new now (used for reference)... im sure you could find a used or new old stock mobo for cheap or free somewhere.

---

### Post by doogg on 2007-02-28
look over at newegg for a promise pci card.
"promise ultra133 tx2 pci ide 66m pci controller card".
i used one to ressurect an old ME machine i have to recognize a 320gb drive that i then turned into a dedicated ubuntu machine.

---

### Post by Patrick K on 2007-02-28
Without upgrading the BIOS, adding a supporting pci card, using a drive overlay, or installing a new motherboard, you'll need to set the size limit jumper on the drive. The jumper setting are printed on the drive's case. Upgrading the BIOS is really the best option provided one is available (this is the option I went with). Overlays can create a lot of problems down the road. A PCI card is pretty easy to do. With a motherboard changeout, you'll likely run into hardware/OS issues that will have dealt with.

---

### Post by uclalinux on 2007-03-03
ok I fix it this is all i had todo. in my bios turn off the auto detect. then when ubuntu boots up, it will not listen to the bios and add the hard drive to my /dev/hdX. then i just find the correct UUID and mount it where i want. in my case it was my /home directory that i was changing. after correctly changing fstad, u have to chown "username":"username" /home/"username", so that way the ".kstartupconf" will  recognize the new hard drive and what not.  Anyways it working and all 250 GBs are free to uses. 
Thanks

---

### Post by teaker1s on 2007-03-03
partitions is another way of fixing issue, in some cases this used to be recommended to windows users

---


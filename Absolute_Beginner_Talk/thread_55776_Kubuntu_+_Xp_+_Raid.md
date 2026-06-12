---
title: "Kubuntu + Xp + Raid"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by Gav-UK on 2005-08-10
I currently have XP on a SATA Raid 0 configuration and i wanted originally to install kubuntu onto a partition on this setup but unfortunatley it has proved to be a bit of a nightmare.

I have now decided to format one of my ide drives and install it there instead. The previous problem was that the partitioner couldnt see my raid formation and instead listed the two drives seperately. What i am wondering is, if i set up kubuntu onto my ide drive, will the bootloader be able to recognise the XP installation which is on my raid drives?

---

### Post by pmjdebruijn on 2005-08-10
Hi,

The problem with the RAID cards today is that 99% of them are Software RAID also called SoftRAID or more properly FakeRAID... You get a plain IDE controller with a BIOS/driver which emulates RAID in software... 

Now, GRUB uses BIOS calls to read/write stuff, so generally it should work... But even if it doesn't ,,, I *think* it's possible to load Linux from the Windows NT bootloader...

Anyway combining FakeRAID with multiboot is a bitch...

Regards,
Pascal de Bruijn

---

### Post by Gav-UK on 2005-08-10
i have tried everything that i can think of to get this to work. 

What i think is happening is that Grub is being installed to the MBR of the 1st IDE drive instead of the Raid drives.

I downloaded [http://www.osloader.com/](http://www.osloader.com/) this to see if it could help. but alas still no joy. When i make it boot the mbr of the first ide drive it just says GRUB and hangs.

I think i will just go back to windows and give Linux up as a bad move. At least until they work out a way of using the raid systems.

Thanks for your help.

---

### Post by TreeFrog on 2005-08-10
Have a read up on the bootloader for XP. 
I think if you leave the XP system as the first system that the Bios looks at you can use the XP BootLoader file to point over to the IDE drive. 

Then when you boot up you will get two options (just like you would if you had XP and 2000 ). One will be the original XP and the other will be the one you type in there. 
It will have a little timer counting down to "Freedom" or "X treem P ain" lol

I cant remember the name of the file to edit righ now.. It is hidden and I think it is on the root of C normaly. It not in a windows or system folder anyway.

Good luck

Treefrog

---

### Post by Gav-UK on 2005-08-10
boot.ini

contains this at the moment:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


I have no idea what you could do to make this work with a Linux install or even if its possible.

EDIT::
more info here: [http://www.wellho.net/solutions/general-linux-and-xp-loading-a-dual-boot-system.html](http://www.wellho.net/solutions/general-linux-and-xp-loading-a-dual-boot-system.html)
[http://www.xtremesystems.org/forums/archive/index.php/t-1097.html](http://www.xtremesystems.org/forums/archive/index.php/t-1097.html)


It says that it does work but its a slightly different setup because i have raid drives.

---


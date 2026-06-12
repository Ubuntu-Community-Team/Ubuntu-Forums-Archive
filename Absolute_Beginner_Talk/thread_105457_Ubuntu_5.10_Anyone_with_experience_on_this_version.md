---
title: "Ubuntu 5.10 Anyone with experience on this version?"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by Gregory West on 2005-12-18
How is the best way to get this program. I tried version 5.04 on an install CD but it won't install. Someone suggested getting the new 5.10 off the unbuntu site and download it to the harddrive then to a disc.

Anything I should be aware of?

thanks,
greg

---

### Post by Weasel on 2005-12-18
Download .iso, burn .iso.

---

### Post by doitashimashite on 2005-12-18
Just download the .iso file, burn the CD, and boot your machine with it.
The installation procedure is straight forward, and Ubuntu installls very smoothly.

---

### Post by Gregory West on 2005-12-19
Ah ha, therein lies my mistake...I did not boot with the CD.
But one of my laptops has the CD still inside and I am stuck on the partioning part. I should have removed the junk in my computer and didn't...how can I get the CD out and start over?
Thank you
greg

---

### Post by az on 2005-12-19
[QUOTE=Gregory West]Ah ha, therein lies my mistake...I did not boot with the CD.
But one of my laptops has the CD still inside and I am stuck on the partioning part. I should have removed the junk in my computer and didn't...how can I get the CD out and start over?
Thank you
greg[/QUOTE]
If you were partitioning, then you did boot from the cd.

What happens when you boot the computer withthe cd inside?

---

### Post by arctic on 2005-12-19
In order to get out of the installer, press "ESC" and abort installation. Now boot your system, defrag your drive and create a new partition for usage with Linux (e.g. with partitionmagic) and start the install process again. I recommend to create four partitions: /boot (~100-200 MB), swap (double RAM size), /[root] (~4-7GB, depending on your needs) and /home (as big as you like it to be).

---

### Post by Gregory West on 2005-12-20
Originally, the linux cd did boot up and began installation. When I reached the partition part I found there was not enough room for the program and tried ejecting the cd. It would not eject so I used a paper clip to get the cd out.

Now, the computer will not boot into windows so I can clean off the hard drive to load linux again. I get an error box which goes through diagnostics but no luck getting windows to open.

Please help me...LOL

thanks,
greg

---

### Post by Gregory West on 2005-12-22
[QUOTE=azz]If you were partitioning, then you did boot from the cd.

What happens when you boot the computer withthe cd inside?[/QUOTE]

What we ended up doing was to remove the hard drive and put it back in. Reset the bios to boot from the cd Ubuntu 4.01 - For some reason this old laptop with a 4GB hard drive would not accept this program. We have now loaded in Fedora and it is working...now we are fiddling with getting the wireless card and connection to operate.

Time to go on Ebay for a larger IBM Thinkpad hard drive and load Ubuntu 5.10, until then we can begin Linux and start the learning process.

Thanks again for all your help...I am sure I will be back here once I get Linux loaded onto my own laptop and desktop.

---

### Post by macheadPDX on 2005-12-23
[QUOTE=Gregory West]What we ended up doing was to remove the hard drive and put it back in. Reset the bios to boot from the cd Ubuntu 4.01 - For some reason this old laptop with a 4GB hard drive would not accept this program. We have now loaded in Fedora and it is working...now we are fiddling with getting the wireless card and connection to operate.

Time to go on Ebay for a larger IBM Thinkpad hard drive and load Ubuntu 5.10, until then we can begin Linux and start the learning process.

Thanks again for all your help...I am sure I will be back here once I get Linux loaded onto my own laptop and desktop.[/QUOTE]

Hello,

I have a very old IBM ThinkPad with a 4GB harddrive. I installed UBUNTU Breezy 5.10 without a problem... Try it out.

Good luck!

---

### Post by elemental666 on 2005-12-23
[QUOTE=Gregory West]Originally, the linux cd did boot up and began installation. When I reached the partition part I found there was not enough room for the program and tried ejecting the cd. It would not eject so I used a paper clip to get the cd out.[/QUOTE]

For future reference, linux (any flavor) will LOCK your CD Rom drive when it mounts the cd inside it, this is why you can't eject the cd with the button, the cd needs to me unmounted first.  Fromthe installed that means, aborting the installation and rebooting, when you see your boot splash (the one that lets you get to your bios) you can eject the cd.  From inside linux the cd will be mounted to /mnt/cdrom or something similar, you need to unmount (see: man mount) the drive first.

Using a paper clip is a bad idea,  you can strip little plastic gears and wear out the tray motors in a hurry that way.

---

### Post by Gregory West on 2006-01-01
[QUOTE=macheadPDX]Hello,

I have a very old IBM ThinkPad with a 4GB harddrive. I installed UBUNTU Breezy 5.10 without a problem... Try it out.

Good luck![/QUOTE]

Thank you, I just may be emailing you for some tips. I got Fedora loaded and still trying to learn a few things, such as setting up my WiFi on Dlink.

thanks,
greg

---

### Post by Gregory West on 2006-01-01
[QUOTE=elemental666]For future reference, linux (any flavor) will LOCK your CD Rom drive when it mounts the cd inside it, this is why you can't eject the cd with the button, the cd needs to me unmounted first.  Fromthe installed that means, aborting the installation and rebooting, when you see your boot splash (the one that lets you get to your bios) you can eject the cd.  From inside linux the cd will be mounted to /mnt/cdrom or something similar, you need to unmount (see: man mount) the drive first.

Using a paper clip is a bad idea,  you can strip little plastic gears and wear out the tray motors in a hurry that way.[/QUOTE]

Hi, we got it working with Fedora and will be back with more questions I am certain. This is a great place for info...

thanks,
greg

---


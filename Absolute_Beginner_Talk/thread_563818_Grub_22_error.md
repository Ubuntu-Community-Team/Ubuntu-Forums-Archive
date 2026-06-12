---
title: "Grub 22 error"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-09-30
Hi, i just bought a new computer. I decided that it should be a Linux only computer, 
Now here is the problem, the other computer i have in the house is going to be a Windows gaming computer, so i just..deleted the Ubuntu partition (yea i know, it was stupid) so now when i try to start it I come to the Grub thing but it says Error 22 and just stops. how do i get ubuntu away and windows to work?:confused:

---

### Post by Pumalite on 2007-09-30
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by rsambuca on 2007-09-30
You will need to restore your MBR to the Windows bootloader.  If you have your XP installation discs, just boot to the recovery mode and type in "fixmbr" at the command prompt.

---

### Post by ajmannen on 2007-09-30
I have a Vista installation disk, is it the same with that?

---

### Post by ajmannen on 2007-09-30
Ok, the vista disk was realy a vista upgrade disk, so i can't use it. I only have a vista recovery partition wich i have no idea how to use. 

I did not understand the guid you sent med (i'm realy incredebly newbi with termina/comand lines!)

---

### Post by ajmannen on 2007-09-30
Ok, i finaly worked it out. but the list of partitions won't show up! :confused:
Need help fast

---

### Post by Pumalite on 2007-09-30
This happens because they are selling laptops with 'recovery partitions' and no disks. Go to your seller and get a disk, or from the laptop maker. Another choice, I guess, would be to get an OEM disk in EBay and use the serial # stamped in your machine.

---

### Post by ajmannen on 2007-09-30
I kinda need the computer soon. and acer would use weeks (or months) to send a CD to Norway, if the bother at all.
 
I have the Ubuntu live CD, is there no way around this?

---

### Post by Pumalite on 2007-09-30
Wipe your hard drive and install Ubuntu. You'll love it.(just kidding)
Try Super Grub and see if you can restore MBR that way: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by rsambuca on 2007-09-30
You could just re-install ubuntu onto the partition that you had it on previously.  Then  grub will be re-installed. You can then just keep it like that until you get some Vista discs, or, you could just use the Vista recovery partition to start over.

---

### Post by ajmannen on 2007-09-30
I can't use the vista recovery partition cuz Grub is somewhy blocking it, i'll try super grub

---


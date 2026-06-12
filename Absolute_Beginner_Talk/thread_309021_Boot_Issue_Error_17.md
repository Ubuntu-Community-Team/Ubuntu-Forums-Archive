---
title: "Boot Issue: Error 17"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by KatanaSwordfish on 2006-11-29
Ok. I decided to format my slave harddrive, and install edgy. I ran GParted, deleted the old ntfs partition on my slave drive, and then ran the installer off of my ubuntu live desktop CD.

Installation went smoothly, i think. And i got the installation complete message. My options were to continue running off of CD, or restart computer.

I restarted, entered BIOS, set my Harddrive Boot priority to my slave disk, and save/exited. Some menu came up, asking which OS to boot. When i selected the "Ubuntu, kernel 2.6.17-10-generic"; i get a message that says:

Error 17: Cannot mount selected partition

Press any key to continue..._




Anybody know what this means or how to fix this? I have my ubuntu desktop CD nearby incase i need that. Thanks.

KAT

---

### Post by lhtown on 2006-11-29
It sounds like you goofed something up with your hard drives.

From what you are saying, it sounds like Edgy might have gotten installed to you master and you are trying to boot from your slave.

You might make sure that your hard drive jumpers are set correctly (located on the drives themselves) as well as your bios settings.

You may just have to double check your BIOS setings, cables and jumpers, and then reinstall Edgy. I don't know about installing it to a slave drive. That seems a bit goofy to me.

---

### Post by xolot1 on 2006-11-29
i had this problem when i first installed ubuntu..1.5 years ago? something like that. 

anyways, i remember fixing it by playing the the hard drive values in the bios setup screen. im sorry i cant remember too much more, but definitely start out looking in that direction. (i dont think it was manually changing number of sectors etc, but one of the other options.. ugh i wish i could be of more help cause i had such frustration with it.)

willi

---

### Post by KatanaSwordfish on 2006-11-30
Hi, thanks for the input all. After searching around a bit i found out what my problem was.

i had my boot set to (hd1,0).

which is actually the **second** partition that grub looks for.

so all i had to do was press 'e' when the option came up. press e again, and set the number to...

(hd0,0)

which is the first and foremost partition that is found. and since i had my hard drive boot order where Ubuntu was on the first partition to be recognized, it was just skipping over it and trying to mount the second partition in stead.

I hope this helps if anyone else gets that same problem with their dual-boot configuration. good luck!

---


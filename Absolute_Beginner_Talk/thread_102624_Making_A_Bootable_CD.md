---
title: "Making A Bootable CD"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by johnnymo87 on 2005-12-12
Hi. I'm currently trying to make the switch from windows to the Ubuntu distro of Linux. This will be my first time ever using linux.

I am trying to make a boot CD (my floppy drive is broken). 

I checked my BIOS, and set it to 1st boot to the CD-ROM. So, my computer can boot CDs.

I have burned the lastest Ubuntu distro (Ubuntu 5.10 "Breezy Badger" i386 version for my AMD Athlon) as an image onto a blank CD. I bleive I did this right because the CD is now called "Ubuntu 510 i386". The contents of the CD are folders called ".disk, dists, docs, install, isolinux, pics, pool, pressed" and files called "md5sum.txt, README.diskdefines, ubuntu"

OK. So I haven't repartitioned my computer yet. I just want to test out the bootability of the CD before I fdisk.exe and format.com my harddrive (windows programs for repartitioning and wipe areas of my drive. I would lose all my windows stuff when I do it, which is what I want. I still made backups of all my windows stuff in case the bootdisk fails.).

I put the CD in my bootable CD-ROM, and restart my computer. The "reading" light on my CD-ROM comes on for a few seconds, but then disappears and my computer continues to load windows as usual.

Did I make the CD wrong? (I burned it as an image)
Is my CD-ROM not bootable? (I check it in my BIOS)
Do I need to repartion my drive before the boot CD responds?
Do I have the wrong distro?
Should I have them ship me a CD instead of trying to make one? (I like the challenge)

I'm a total newbie to switching OSs and linux in general. Please help!

---

### Post by lutrafobic on 2005-12-12
If you burned the cd as an image, you've done it correct. (se image below how it's done in Nero burning rom)
[IMG]http://www.lutrafobic.com/forum_pics/nero.jpg[/IMG]
If your BIOS is correctly setup, the ubuntu installation/bootmenu should appear, without any previous partitioning at all.

So i would guess that the problem is with BIOS. Eather the BIOS hasn't support for CD-ROM-booting (and therefore need to upgraded, check the manufactors homepage for more into about that)
or the setting is just wrong. 
When thyring diffrent settings, don't just try the right way, also try the otherways.
(regarding boot-sequence) I've had computers that I had to set a wrong boot-sequence for it to work. don't ask me why :D

Good luck & get back if you have more questions or this didn't help.

Best regard
Lutrafobic

---

### Post by rogershera on 2005-12-12
Having similar confusion.

I do not have Nero SE.
I had a wizard come up where I could check an "image" box.
Did this and it prompted me to save a *.nrg file.
I did this but it seemed to burn but I was unable to "explore" the CD so perhaps not.
I am now burning the ubuntu.nrg file to a CD.
Do you know if this the same?

---

### Post by lutrafobic on 2005-12-12
rogershera:

You do NOT want to make a .nrg file.
That means you create a image, that's not what you want. 
You want to burn FROM a image. (the image is the .iso file you downloaded from internet)
You want to look for a thing called "Make from Image, or burn from image"
There was a simular question on this forum some time ago, were the use posted a screenshot that was helpful, perhaps you can search for that?

Found a guide by searching the forum, hope this make sence. [http://www.xmastree.34sp.com/ubuntu/burn/]("http://www.xmastree.34sp.com/ubuntu/burn/")

and here is a previous post with simular problem:  [http://ubuntuforums.org/showthread.php?t=91074]("http://ubuntuforums.org/showthread.php?t=91074")

---

### Post by JimmyBEng on 2005-12-12
do you all have another computer where you check if the CD is bootable or not or do you have another CD that you already know is bootable to check whether the BIOS is set right. Just some ideas for limiting the unknowns in the problem.

---

### Post by rogershera on 2005-12-16
thanks folks, must have been the bios on the PC I first tried to test it on.
The actual PC launched right away and installed perfectly.

Odd thing is that the test PC was trying to boot to CD but didn't find what it wanted.
????

---


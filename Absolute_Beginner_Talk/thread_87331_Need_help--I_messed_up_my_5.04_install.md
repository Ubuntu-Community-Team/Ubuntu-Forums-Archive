---
title: "Need help--I messed up my 5.04 install"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by lgbpop on 2005-11-07
Hope someone has suggestions or a solution. My new machine is a dual-boot (98SE & XP). I've been intrigued with Linux and heard about Ubuntu. Tried the live CD and liked it, so I copied an install ISO and downloaded it to my crash-test Compaq (different computer) as the sole OS on 8GB HDD, 192MB RAM, old Pentium III. It worked fine. So I decided to install it into the new machine (160 & 300GB SATA HDD, RAID-0, 768MB RAM, Athlon XP3000+). All was fine until I got to the point where it detected other OSs and asked if all were detected. I entered "yes" instead of "no" before I realized that 98SE wasn't on the list. The GRUB install did something in the boot.ini or MBR (maybe they're the same thing, I don't know) but now I can't get anything to load. After the POST but before a splash screen, I get:

GRUB loading stage 1.5
GRUB loading, please wait

Error 21

Then a blinking cursor that won't take entries. I put in my 98 boot floppy (and CD just in case) and got into DOS. The 98SE files on drive C: and XP files on drive D: seem intact, as well as the remaining virtual partions (E:, 20GB; F:, G:, H:, and I:, 100GB each). Any ideas how I can edit the boot.ini or MBR, or delete GRUB from DOS to be able to boot up again?

Also, has anyone had any experience with installing Ubuntu as a third OS on a computer?

---

### Post by Kapre on 2005-11-07
lgbpop - I found this [thread]("http://www.ubuntuforums.org/showthread.php?t=86217&highlight=sata+install"). Maybe it will give you some info.

K

---

### Post by Herman on 2005-11-07
[http://users.bigpond.net.au/hermanzone/p4.htm](http://users.bigpond.net.au/hermanzone/p4.htm)

See if anything in the above link helps. 
 (Herman)

---

### Post by lgbpop on 2005-11-07
Thanks for the leads, both of you.  It's bedtime, will try them tomorrow.

---

### Post by lgbpop on 2005-11-09
Thanks again to both of you.  I wound up installing GAG--not without a little trepidation after what I already had done:D --and the problem was solved for now.  Both Windows systems are bootable again.  Am getting ready to try and install LILO on the Ubuntu partition, will let you know what happens.

---

### Post by lgbpop on 2005-11-21
Well.........let's just say I put this install on hold for now.  I instead installed it on my crash-test Compaq to practice the setup and see how it should go.  

I do have one question, though.  When I first installed it I didn't have any speakers hooked up, so I found a pair a few days later and plugged them in.  No sound.  I found the volume settings control, tried to open it and got a message window saying the computer couldn't connect to the sound daemon, and to run esd from a command window.  When I did that, it came back "no such file found."  Shouldn't that be part of the OS?  Anyplace I can download it to the computer?

---


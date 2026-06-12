---
title: "New install xubuntu 6.06 Grub error 18"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by anagramspin on 2007-03-12
Hi,
I'm receiving the dreaded Grub 18 error after a fresh install of ubuntu 6.06 alternate cd.

The install is supposed to be running on a old Compaq PII 450 w/128 MB Ram, and most importantly a 250 GB HDD. The result of lots of research seems to be a conflict between the BIOS not being able to read the large disk. BIOS update not avaliable, and not possible to turn off autodetect HDD. So it seems to me the only way around this is to:
1.  repartition the drive, create a small boot partition
2. reinstall xubuntu

A sad detail is that fedora 5 seems to get by this error (although I do not have enough ram to run fedora) it seems more newbie friendly when it comes to installing on older systems.

So to the questions:

Is there an easy way to get up and running with some tweaks to the existing install or is the no other way round this than a complete reinstall?
Is it possible to boot knoppix and start xubuntu - is that possible? 
Just to get a testdrive before another couple of hours of installing.

Thanks for your time!

---

### Post by corax on 2007-03-13
Hi !

I had the same issue on a PIII 450 with an old ABIT motherboard ...

The solution was to ENABLE (you said it is also enabled right ? :S ) HDD detection and then my bios knows that it is a large disk (20 GB :-) ). If I disable boot detection and detect it manually it says also the right size (20 GB) but after the first reboot (and for all the later boots) it is only 7,1 GB ... and it is not working ... it is strange :-) But the point is IT WORKS with Auto detection (for me on an old ABIT board).

"A sad detail is that fedora 5 seems to get by this error (although I do not have enough ram to run fedora) it seems more newbie friendly when it comes to installing on older systems."

Have you bought your Compaq PC with P2 450 AND 250 GB HDD ??? (Was it shipped originally with 250 GB HDD ? ) I don't think so ... It IS user friendly on older machines with older parts and newer machines with newer parts ... :)

Why don't want to upgrade BIOS ?

For your problem a solution can be to backup the whole install to .tar.gz (1 command  ) repartition the drive and extract the tar with live CD (1 more command and some others to make folders like /proc and /sys ) and it is ready to go ... :) The compression and decompression is fully automatic ... (you can leave the machine to work on it while you can do something else ...)

good luck :)

---


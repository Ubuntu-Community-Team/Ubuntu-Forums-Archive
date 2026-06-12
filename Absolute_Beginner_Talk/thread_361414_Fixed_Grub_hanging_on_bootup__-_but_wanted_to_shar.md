---
title: "Fixed Grub hanging on bootup  - but wanted to share"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Woodsy on 2007-02-14
Hi All,

I've fixed my problem but I just wanted to post this on the off chance that someone with the same hardware as me had the same problem as I've not seen it posted anywhere with these exact symptoms.  I'll try and be as brief as I can...

I'm using a Compaq AP400 (dual processor), a 20 gig HDD primary and a 160Gb drive secondary.  I'm running Windows XP (can't remember on which drive its installed though!) but I decided to free up some disk space on the 160Gb drive, install Ubuntu 6.10 and use as a dual boot system.
I had a dreaded "Grub Loading Please wait...." hang and surfed the net looking for a possible solution.  There is quite alot of possible solutions for this error.   Unfortunatley none of them worked for me  and after 3 days and several early mornings I was in the process of posting on this forum.
I looked around my BIOS for the 15th time and quite innocently unticked a "Disable translation" setting for the 160Gb drive in the BIOS.  I haven't a clue what this setting does but GRUB now loads.
I just would like to say thanks to everyone on this board as you've been an invaluable source, I've learnt a few things on the way and you all seem like a very friendly bunch!

I look forward to picking your brains soon!

---

### Post by tgalati4 on 2007-02-21
Good job!  Disabling translation is BIOS-speak for not translating logical block addressing (LBA).  For large disk drives (greater than 130 GB?) motherboards handle large disk devices differently.  Turning off the translation allowed the mini-linux operating system that Grub uses to properly see the drive.  It's obscure but with so many different types of pc hardware out there, we forget the lack of standards for some of these issues.  I think new users get the wrong impression of linux when they run into these problems--not realizing that it does require some work on your part to get linux to run properly.  Dell spends the time to get windows to work properly on their machines.  They even put nice little stickers that say "Designed for Windows!".

---


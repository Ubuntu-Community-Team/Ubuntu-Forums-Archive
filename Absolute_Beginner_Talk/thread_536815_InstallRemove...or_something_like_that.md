---
title: "Install/Remove...or something like that"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by kuddo on 2007-08-28
I want to install ubuntu on my pc... because i want to give up microsoft... But i want to install it with windows on the same PC. I tried to do that with another distro...i made ext2 partitions...and i installed it...all was fine...but when i tried to remove it (the linux distribution) in my stupidity i deleted the EXT2 partition from windows :lolflag:
When i restarted my pc...surprise... lots of numbers apeared on the screen... like 01234 01234 and so on... The windows cd was not recognized anymore...the linux cd wasnt either... And i had tu fdisk mbr...redo the mbr and lose all data from my pc...it was very nasty... Now i know a little something about linux ( i said a little :-D )...but i want to see a tutorial or something to be 100% sure that i wont do something stupid again...i want to know if i install ubuntu on the same pc with windows, if i can remove ubuntu with 0% risk to damage data from ntfs or the bootloader... And i want to know if windows broke while i have installed WinXP and Ubuntu if it will be a problem.

Can u please help me...because i`m tired of Billy Gates. :-D

Sry for my insistence...i`m just frighten of loosing again all my data.
(excuse my english i`m not to good at it...it`s not my natural born language)

---

### Post by phyrewall on 2007-08-28
Your hard drive partitions shouldn't affect your CD-ROM recognizing CDs... so I suggest booting a WinXP CD, going into recovery console, running "fdisk /mbr" to reset the boot loader to the Windows one. Then you can boot into windows again.

1. Boot the computer using the XP CD. You may need to change the 
      boot order in the system BIOS. Check your system documentation 
      for steps to access the BIOS and change the boot order. 
    
    2. When you see the "Welcome To Setup" screen, you will see the 
     options below This portion of the Setup program prepares Microsoft 
     Windows XP to run on your computer:

   To setup Windows XP now, press ENTER.

   To repair a Windows XP installation using Recovery Console, press R.

   To quit Setup without installing Windows XP, press F3.
 
   3. Press Enter to start the Windows Setup. 
      do not choose "To repair a Windows XP installation using the 
      Recovery Console, press  R"

   4. Press R


Run fdisk from the console to remove the linux partitions, or load Windows and use a program like Partition Magic to remove the linux partitions and resize the NTFS partition.

---

### Post by louieb on 2007-08-28
> **kuddo said:**
> ...but i want to see a tutorial or something to be 100% sure that i wont do something stupid again...
:lolflag: see the uninstall page here [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/").
Lots of ways to do it right. Sorry you found one of the ways that did not work. 
That site has good install information to. another site with good stuff is [Psychocats Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php")

---

### Post by kuddo on 2007-08-28
I was simply deleted the partitions from Windws XP with partition magic...then after the restart an booting error occured...i was entering the windows xp...but when i was inserting the windows bootable CD, it was not recognized neighter the linux cd...and after a few days the pc crashed and appeard another error...and it was dead and i couldn`t do nothing because when i restarted the pc the screen was full of numbers...

---


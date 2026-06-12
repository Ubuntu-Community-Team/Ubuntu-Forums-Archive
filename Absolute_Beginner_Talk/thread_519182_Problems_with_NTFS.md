---
title: "Problems with NTFS"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by fadedreality01 on 2007-08-06
Hello all. I switched over to Ubuntu from XP today. Complete re-format of the drive with XP on it, so it's completely gone. I've followed the instructions from several different sites, forum posts, etc. trying to get a" the data on my second hard drive. 

I can't change it to read and write and now it's giving me an unclean error. I have no dual boot XP installed to switch over to, only Ubuntu. How can I get to the files on my other drive without XP?

---

### Post by Depressed Man on 2007-08-06
Ok let me understand if I read this correctly. You had two HDDs. One with the OS installed, and a second NTFS drive. 

You formated the one with the OS (Windows) installed on it and replaced it with Ubuntu. And you left the second NTFS drive alone.

And you want read/write access for the second NTFS drive but your also getting unclear mounting issues?

Ok well for read/write access you want NTFS-3G (you can get the config while your at it). Go to synaptic and do a search for NTFS grab NTFS-3G and the NTFS-config (or some file like that). I forget their exact name otherwise you could sudo apt-get install name of program.

It seems to me that the drives weren't mounted correctly (well automounted as they usually are nowdays). Though I believe NTFS-3G can help with mounting issues as well (at least it has for me in the past).

---

### Post by zxccvb on 2007-08-06
Just install ntfs-3g and ntfs-config.
To install them you may use synaptic but you may have to add some repository.

Then go in the menu  Application->System Tools->NTFS Configuration Tool.

A window will present you with just two options one for internal and the other for external volumes. Pick according your needs and you're good to go(maybe you need a reboot).

---


---
title: "uninstalling ubuntu"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by Dozerman30 on 2006-01-20
I don't want to but i have to uninstall ubuntu from my main computer. I am going to put it on another box i got. It will be a linux only box. But what is the easiest way to get ubuntu off the main computer?

---

### Post by Cool Calm Chris on 2006-01-20
This is something I'd like to know as well...

---

### Post by endersshadow on 2006-01-20
[QUOTE=Dozerman30]I don't want to but i have to uninstall ubuntu from my main computer. I am going to put it on another box i got. It will be a linux only box. But what is the easiest way to get ubuntu off the main computer?[/QUOTE]

If it's not a dual boot, just pop in the disk of your the OS of your choice and it will format the HDD.

If it's a dual boot, you can just erase the partition and give it back to the primary OS (make sure you do this via the primary OS!).

---

### Post by MadMan2k on 2006-01-20
[QUOTE=endersshadow]
If it's a dual boot, you can just erase the partition and give it back to the primary OS (make sure you do this via the primary OS!).[/QUOTE]
if grub is in your MBR its not that easy - you will have to boot the Windows repair-console and run fixmbr.

---

### Post by endersshadow on 2006-01-20
[QUOTE=MadMan2k]if grub is in your MBR its not that easy - you will have to boot the Windows repair-console and run fixmbr.[/QUOTE]

Oh, I thought you could use grub with Windows?  At least, my friend always replaces MBR with grub on his Windows boxes...

---

### Post by Dozerman30 on 2006-01-20
yes it is a dual boot system. My gf hates it when i experiment on the main computer. I guess that is a hazard when living with a geek!!! i read a few things on the web but they say to delete the partition which ubuntu is on then just reboot the computer and remove grub from the master boot record. but i have gotten error 22 everytime i try to do that. How do I get to the Windows repair-console? Thanks for all the help

---

### Post by dueY on 2006-01-20
[QUOTE=Dozerman30]yes it is a dual boot system. My gf hates it when i experiment on the main computer. I guess that is a hazard when living with a geek!!! i read a few things on the web but they say to delete the partition which ubuntu is on then just reboot the computer and remove grub from the master boot record. but i have gotten error 22 everytime i try to do that. How do I get to the Windows repair-console? Thanks for all the help[/QUOTE]

Boot with the Windows CD in the CDROM drive.  Then use the repair.  I believe if you get to a console you type "fixmbr" as previously recommended and "fixboot" too I believe.

---

### Post by Dozerman30 on 2006-01-20
ok got it fixed thegf will be happy everytime she would turn on the comp she would grip about two OS's oh well it just give me something else to do now. heheheheh. thanks for all the help guys.

---

### Post by dueY on 2006-01-20
[QUOTE=Dozerman30]ok got it fixed thegf will be happy everytime she would turn on the comp she would grip about two OS's oh well it just give me something else to do now. heheheheh. thanks for all the help guys.[/QUOTE]

She ever tell you why she didn't like it?  I mean, Windows still works fine, right?  And you know you can make Windows the default so you don't have to hit the down arrow a few times. :o

---


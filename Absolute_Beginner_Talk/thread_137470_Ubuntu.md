---
title: "Ubuntu"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by Coop on 2006-02-28
Hi,I installed Ubuntu Linux for the first time.The installation took around 3 hours on my PC(a Pentium 3/Celeron with 196 MB of RAM and a hard drive of around 20 GB space).I just want to know some things:                                                                                                                                                                                                                           
                                                                                                          1.In the installation process,whenever the installer said the computer would reboot,it did not but instead it shut down.So,when the installer says the computer will "reboot",does it actually mean it will shut down,or is there a problem with the PC or the Ubuntu CD I am trying to install Ubuntu Linux from?                                                                   

2.I am using an A4TECH 520 DPI Serial mouse.When I try to move the mouse on the desktop in the Ubuntu Live CD or the installed Ubuntu system and also in the Fedora Core installer and I think in every Linux system,the mouse does not move.But the mouse pointer is present on the screen.Is this because the mouse is incompatible with linux.Are there any ways to fix this problem(besides buying another mouse)?

3.How can I remove GRUB from the MBR of a computer and remove Ubuntu Linux from the computer?

---

### Post by untwisted on 2006-02-28
[QUOTE=Coop]Hi,I installed Ubuntu Linux for the first time.The installation took around 3 hours on my PC(a Pentium 3/Celeron with 196 MB of RAM and a hard drive of around 20 GB space).

[/QUOTE]  

Welcome to the Ubuntu community, I hope you like it :)

[QUOTE=Coop]                                                                                                                                                                                                               
                                                                                                          1.In the installation process,whenever the installer said the computer would reboot,it did not but instead it shut down.So,when the installer says the computer will "reboot",does it actually mean it will shut down,or is there a problem with the PC or the Ubuntu CD I am trying to install Ubuntu Linux from?                                                                   
[/QUOTE]
I'm not 100% on this, but I'm guessing that there is no problem if the computer just shuts down.  I seem to remember mine doing that as well, and my Ubuntu install works just peachy.  No worries there.
[QUOTE=Coop]
2.I am using an A4TECH 520 DPI Serial mouse.When I try to move the mouse on the desktop in the Ubuntu Live CD or the installed Ubuntu system and also in the Fedora Core installer and I think in every Linux system,the mouse does not move.But the mouse pointer is present on the screen.Is this because the mouse is incompatible with linux.Are there any ways to fix this problem(besides buying another mouse)?
[/QUOTE]
It may be that your mouse is out of date, and you need to install drivers for it.  Try following these instructions to get your mouse working: [http://www.faqs.org/docs/Linux-mini/3-Button-Mouse.html](http://www.faqs.org/docs/Linux-mini/3-Button-Mouse.html)  I didn't read through them but from the description google gave it may help.
[QUOTE=Coop]
3.How can I remove GRUB from the MBR of a computer and remove Ubuntu Linux from the computer?[/QUOTE]
Now why would you want to do a SILLY thing like that?  If you're going to install Windows, or even another distribution of Linux, you can just boot from the install disk and reformat/repartition.  If you're trying to just remove Ubuntu and keep an exisiting install, I would suggest keeping Grub as your boot loader for now, and just formatting the partition with Ubuntu.  From personal experience, I can say that playing with boot loaders when you're not quite sure what to do can be a pain.  If its not necessary, and you don't want to ruin your system I'd say keep it.  Otherwise, google for information about Grub and removal.  Enjoy tinkering.

---

### Post by K.Mandla on 2006-02-28
[QUOTE=Coop]1.In the installation process,whenever the installer said the computer would reboot,it did not but instead it shut down.So,when the installer says the computer will "reboot",does it actually mean it will shut down,or is there a problem with the PC or the Ubuntu CD I am trying to install Ubuntu Linux from?[/quote]
It should be all right, although I've never seen that happen. Shutdown or restart shouldn't interfere with it. I don't even think the installer would bother to tell the difference.                         

[QUOTE=Coop]2.I am using an A4TECH 520 DPI Serial mouse.When I try to move the mouse on the desktop in the Ubuntu Live CD or the installed Ubuntu system and also in the Fedora Core installer and I think in every Linux system,the mouse does not move.But the mouse pointer is present on the screen.Is this because the mouse is incompatible with linux.Are there any ways to fix this problem(besides buying another mouse)?[/QUOTE]
I'll have to defer to someone who's used a serial mouse. Luckily, xmastree has [some experience with them]("http://www.ubuntuforums.org/showthread.php?p=604061#post604061"). 

[QUOTE=Coop]3.How can I remove GRUB from the MBR of a computer and remove Ubuntu Linux from the computer?[/QUOTE]
If Windows is already on the machine, you could reinsert your WinXP installation disc (I'm assuming you're using WinXP), and I think (I haven't done this in a LONG time) you can use the repair option to kill out Ubuntu but keep XP.

Of course, if you just want to blank the drive completely, try [Killdisk]("http://killdisk.com/").

---


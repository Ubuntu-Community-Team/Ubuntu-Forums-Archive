---
title: "[SOLVED] Froze during installation"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by pokerphobia on 2008-03-11
Hello folks, I decided to dive right into the whole Lunix thing and decided to download / install Ubuntu. However, during the installation at 15%, my computer froze. I left it for a couple of hours (just in case it was simply taking a long time), but there was still no progress, so I was forced to shut it down. This leaves me with an interesting situation in that now booting up, and selecting Ubuntu gives me an Error 17 : File not Found, /ubuntu/install/boot/grub/menu.lst .. To add insult to injury here, I selected the option to write over Windows, so I have no OS now I guess =P. What should I do now? I ultimately want to end up with Ubuntu only on my PC. Any help would be greatly appreciated.

Thank you,
Kevin

---

### Post by Rocket2DMn on 2008-03-11
You should be able to just try again to install.  You might have to set your CD Drive to ahead of your hard drive in the boot sequence (inside your BIOS).
If it fails to install again, try the alternate install cd from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) - just check the box at the bottom first.  It is a text based installer, but it is intuitive and easy to use.

---

### Post by bumanie on 2008-03-11
You should check the md5 checksum and also scan the cd for errors. If they are OK, you can download an alternate cd, which is text based and will often install onto systems that the live cd won't install on.

---

### Post by pokerphobia on 2008-03-11
So, this might be a stupid question, but can I run this text based installer from what appears to be the DOS menu.. My problem now is that I dont have access to any OS, since I believe Ubuntu killed Windows and then messed itself up by freezing part-way through the installation process. So now all I have access to is a GRUB menu when I select Ubuntu from what appears to be a Dual Boot menu. The other options are Windows XP, and the recovery partition for XP, which I dont believe either will work now. Sorry, I am completely new to OS installations!

Kevin

---

### Post by Rocket2DMn on 2008-03-11
What you need to do is boot from the cd, bypassing GRUB.  You may need to enter your BIOS during the initial startup sequence when you usually see your computer manufacturer logo.
Here is a guide for the altnernate cd install: [https://help.ubuntu.com/community/Installation/I386](https://help.ubuntu.com/community/Installation/I386)
and here's one for the graphical (live cd): [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

To get into the BIOS, you only have a second or so to hit the correct key at your initial bootup, it is usually something like F4, F8, F12, DEL, or ESC.  It may say something like "Press <key> to Enter Setup".  That is what you want.  Once in the BIOS you can navigate around until you find the area to change the Boot Order - put the CD above the HDD.

---

### Post by pokerphobia on 2008-03-11
Hey, thank you for your help guys. I got it installing again. =D !!

---

### Post by uberlube on 2008-03-11
Just some friendly advice, once your problem is solved click on the forum tools button and mark as solved. :)

---


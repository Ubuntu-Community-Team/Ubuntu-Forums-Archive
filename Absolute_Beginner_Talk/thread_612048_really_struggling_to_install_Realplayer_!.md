---
title: "really struggling to install Realplayer !"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by rioja on 2007-11-13
Sorry to post this question up; i've done all the searches and still can't find an answer that works. I've downloaded the realplayer file, and copied to the desktop ( downloaded at work onto mem stick). the file properties show it as executable, but I try to 'open' and nothing happens, I try double-click nothing happens. I tried this in the Terminal;

[COLOR="Red"]kevin@kevin-desktop:~/Desktop$ sudo ./RealPlayer10GOLD.binrealplay-10[1].0.9.809-linux-2.2-libc6-gcc32-i586.bin
[sudo] password for kevin:
sudo: ./RealPlayer10GOLD.binrealplay-10[1].0.9.809-linux-2.2-libc6-gcc32-i586.bin: command not found
kevin@kevin-desktop:~/Desktop$ 
[/COLOR]
Help, what now?

Other than this little glitch, Ubuntu has been very good; wireless PCI card and sound worked on install and all the other updates have been fine; although I seem to be getting as many update notifications as I did with XP!!!

---

### Post by bakeneko on 2007-11-13
Your file name looks too long and has .bin twice.  Do you maybe want to be running just **sudo ./RealPlayer10GOLD.bin**?

---

### Post by Inxsible on 2007-11-13
you first have to make it an executable using chmod```
sudo chmod +x *filename*
```then do ```
./*filename*
``` Real player files is normally named RealPlayer10GOLD.bin

Make sure you are using the correct name. Have you downloaded two different files and trying to install them together?

---

### Post by por100pre1 on 2007-11-13
If using Feisty or Gutsy get this and double click it to install it:

[http://archive.canonical.com/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb](http://archive.canonical.com/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb)

---


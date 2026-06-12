---
title: "How to configure Grub manually?"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Foster on 2006-06-19
Hello there!

I've installed Dapper Drake 6.06 (Desktop CD x86), but one big problem remains: grub isn't working when installed automatically, it fails all the time. "Error 21". I understand now that this means that grub can't find the Ubuntu installation, okay. 

My PC has 3 hard disks, 2 IDE and 1 S-ATA. IDE 1 (/dev/hda1...) runs my Windows XP installation and is, of course, the drive selected in BIOS for booting. Ubuntu is installed on the S-ATA drive in the first logical partition (first and only primary partition is SWAP). 

What do I have to write in my "menu.lst", so that grub will start Ubuntu? Or what must be done, so that grub will boot Ubuntu in this constellation?

I've red several FAQ's, but nothing helped me so far to configure the menu.lst to make it work.

Thanks for any help,

Foster

---

### Post by catlett on 2006-06-19
Are you getting the grub menu on startup and you can boot to windows but when you try to boot to the ubuntu entry you get error 21?

Or do you get error 21 right from the beginning and never get into the grub menu?

---

### Post by anaconda on 2006-06-20
I had wery similar problem. Ubuntu-installer configured grub wrongly for me too. 

It mixed hd0 and hd1, so I just had to edit /boot/grub/menu.lst and change hd0 to hd1 in the place, where ubuntu is loaded.

But since you have 3 Hard-disks your ubuntu hd could be any of hd0, hd1 or hd2.. so you can try all of those.

---

### Post by matrooswolf on 2006-06-20
I found this thread interesting to understand how Grub updates.
Maybe it is of interest to you ...
[http://ubuntuforums.org/showthread.php?t=119512](http://ubuntuforums.org/showthread.php?t=119512)

---

### Post by Foster on 2006-06-20
[QUOTE=catlett]Or do you get error 21 right from the beginning and never get into the grub menu?[/QUOTE]
Yes, I got it right from the beginning - that's why I had to use the XP CD and created a new MBR with "fixmbr" and "fixboot c:", so at least XP would boot again. 

I booted with the Ubuntu Desktop CD again and tried to re-install grub from there with "grub-install /dev/hda1", but only a message similar to "access denied" is shown. 

I searched the net and found this

[http://grub4dos.sourceforge.net/](http://grub4dos.sourceforge.net/)

I used Wingrub and with that I was able to use "e" in the menu when booting up. But pressing tab showed only hd0 and hd1, as if it wouldn't find/recognize my S-ATA drive. Maybe Wingrub is too old?

And I only tried this, because I don't know how to setup the "normal" grub so that it works. :( Let alone that I would prefer a normal grub installation into the MBR.

---

### Post by Gustav on 2006-06-20
Did you use sudo?

---


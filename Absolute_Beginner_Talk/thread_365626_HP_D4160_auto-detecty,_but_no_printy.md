---
title: "HP D4160 auto-detecty, but no printy"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by squig on 2007-02-19
I apologize in advance since I can see that there are a gazillion beginner posts about getting printers to work. I'm only a day into Ubuntu 6.06, have used the basics, but I can't get my printer to work. Apparently it is supported on Linux, and when I try to add a new printer, it does detect an HP D4100 series printer (in fact, it detects two local, and shows the USB connection again below. See attachment.

Step 2 of 3, the next screen of the printer wizard, does not show an HP D4160. I've tried several options in this list. Have tried the CUPS driver, and some others, When I try to print lights flash on printer but nothing happens. It says the printer is "Ready" then "Printing," and even "Printing 3%.." but nothing happens but little flashing lights. I tried turning off printer, turning on again. Nothing. (Printer connects via USB.) The lights flash whether I configure with the USB port specifically or the autodetected option.

I googled it and found someone else with similar problem on ubuntu, same printer. Thread said to download and install a more recent version of hplip, or hpijs... but Synaptic tells me I already have hpjis, and hplip. When I select them it says "Mark for reinstallation" as the first option.

Do I need to download and install these drivers? If not, how do I direct CUPS to them? 

Thanks,
squig

---

### Post by NewOldTimer on 2007-02-19
n00b here. but this is what I used to get my Hp printer up and at em
[http://hplip.sourceforge.net/install/manual/index.html](http://hplip.sourceforge.net/install/manual/index.html)
see if it helps point out anything you may have missed

---

### Post by squig on 2007-02-19
amy@amy-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

I have no idea what this means.

---

### Post by squig on 2007-02-19
From what I can see on Synaptic, I already have all the most recent foomatic and hpijs and hplip installed. There must be something I don't understand about directing this OS towards files...

---

### Post by SunnyRabbiera on 2007-02-19
you need to use sudo, type in sudo then apt get update.
lucky though as HP is normally very good with thier printers under linux :D

---

### Post by squig on 2007-02-19
Now long download process, concluding with Setting up build-essential (11.1)

Directions say to download hplip-1.7.1.tar.gz

I proceed...

---

### Post by squig on 2007-02-19
Now what do I need to do differently?

amy@amy-laptop:~/Desktop/hplip-1.7.1$ ./confgure --prefix=/usr --libdir=/usr/lib64
bash: ./confgure: No such file or directory

---

### Post by Monkalou on 2007-02-20
I may just be suggesting the obvious, but it looks like you just misspelled ./configure as ./confgure so bash couldn't find the program with that spelling.

---

### Post by squig on 2007-02-20
Now I have this trouble:

amy@amy-laptop:~/Desktop/hplip-1.7.1$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 1.7.1)
Printer/Fax Setup Utility ver. 4.3

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
error: Unable to connect to hpiod.
error: Unable to connect to HPLIP I/O. Please (re)start HPLIP and try again.

I have restarted the printer a few times but no change.

(Thanks everyone for your help so far!)

---

### Post by squig on 2007-02-20
No, I get it. I was restarting CUPS but not HPLIP. I restarted HPLIP. Ran through the gui setup screens. A TEST PAGE IS PRINTING!!!!

Thanks everyone for your patience with this simple task of mine. 

squig

---

### Post by squig on 2007-02-20
Now I can print all kinds of test pages, but I can't print a document from open office. What should I do? Anyone had any ideas?

Thanks,

---

### Post by squig on 2007-02-20
Restarted cups and hplip and that did the trick. Will I need to keep doing this?

---


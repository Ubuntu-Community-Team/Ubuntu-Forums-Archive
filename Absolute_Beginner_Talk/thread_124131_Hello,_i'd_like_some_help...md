---
title: "Hello, i'd like some help.."
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by Akiha Tohno on 2006-01-31
I'm somewhat new to Ubuntu here, and I recently got another harddrive for this computer. I'd like to put Ubuntu Linux on it, whilst keeping Windows XP on the HD I have already. How would I go about doing this, without losing anything, and/or getting lost in the installation process?  Thanks ahead of time! :)

---

### Post by az on 2006-01-31
Boot the installer.

I am pretty sure that by default it will offer to use the free space on the new hard drive.  You will then end up bual-booting with a menu apprearing when you boot for you to chose which OS to boot into.  You can also do this with just one hard drive - the installer can shrink your windows partitoin and create a new partition for linux.

If it is not the default option, press cursor down and you should be on that option - - basically, use the entire second hard drive (probably /dev/hdb, depending on what channel you installed the hard drive.)

Just be sure of what drive you are installing it on and it will be easy.

---

### Post by Akiha Tohno on 2006-01-31
I can't get my CD drive to boot before my hard drive does. My BIOS goes by so quickly (like, you can't even SEE the BIOS screen before it loads Windows!) so I have no idea what button to press to change what boots first.

---

### Post by Geekboy on 2006-01-31
What type of PC do you have?

You can try F1, F11, or DEL.  I think they are most common.  Also, just press and hold any key when you turn the PC on.  That will give you a 301 Keyboard error and will take you to the BIOS.

Good Luck.

---

### Post by aysiu on 2006-01-31
[QUOTE=Akiha Tohno]I can't get my CD drive to boot before my hard drive does. My BIOS goes by so quickly (like, you can't even SEE the BIOS screen before it loads Windows!) so I have no idea what button to press to change what boots first.[/QUOTE] Try any of these...

Delete
Escape
F2

One of those should work.

By the way, the fifth link of my signature walks you through a dual boot (complete with screenshots).

---

### Post by Akiha Tohno on 2006-01-31
I've tried the above, and still nothing. Not even the keyboard error thing works. The only different thing I get is this Intel Boot Agent thing I get when I do F12 or F11, it tries to find some DHCP thing, then says it can't find something, and then auto-boots windows before I can do anything, once again.

---

### Post by towsonu2003 on 2006-01-31
can you call the manufacturer of the computer (if you bought it pre-built)? they should know how to access the bios. what are the specs of your somputer? maybe someone here usses the same thing...

originally, I just wanted to say: "**back up everything before installation** (sorry for the bold ;) )

I dont wanna scare you ;) but you just never know. there is a well known hall.dll error some people get for an unknown reason, and they and up re-installing everything. or, much more probably, you might just press the wrong key on the keyboard during the install. or wrong partitioning. the probability of having a problem is very low, but the risk is too big, so pls back things up. 

one last thing: once you get the bios to boot from the cd, you might wanna try the live cd first to see how ubuntu behaves.

---

### Post by Akiha Tohno on 2006-01-31
I can't call the manufacturer.. I bought it from a used PC place. It's made by IBM, has 1 GHZ, 512 MB RAM, 256 MB video card..

---

### Post by towsonu2003 on 2006-01-31
[quote=Akiha Kohno]by IBM[/QUOTE]
I found these googling for <bios ibm> (try a search with the exact name of the comp if you know it (mine is an hp pavilion zv5120us for example)...

from: [http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-50273#initializing](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-50273#initializing)

> 
BIOS Initialization is suggested for some problems. To initialize the BIOS settings:

   1. Turn off the computer.
   2. Turn on the computer.
   3. While the "To interrupt normal startup, press the blue Access IBM button" message is displayed at the lower-left area of the screen, press the Access IBM button.
   4. Double-click Start setup utility. The BIOS Setup Utility menu will be displayed. If you have set a supervisor password, the BIOS Setup Utility menu appears after you enters the password.
   5. Press the F9 key to load default configuration.
   6. Select Yes.
   7. Press the F10 key to save default configuration and exit.
   8. Select Yes.

Notes:

    * After initialization you may need to reapply some settings that you had changed previously.
    * After the initialization has been completed, the system restarts automatically.


from: [http://www.cyberwalker.net/faqs/reinstall-reformat-winxp/enter-BIOS.html](http://www.cyberwalker.net/faqs/reinstall-reformat-winxp/enter-BIOS.html)

> 
IBM:

    * Older Models - In order to get into the configuration of the IBM setup screen (CMOS) screen you need to hold down both mouse buttons during bootup.
    * Aptiva - Press F1
    * IBM PS/2: (Ctrl)(Alt)(Ins) after (Ctrl)(Alt)(Del)
    * IBM PS/2 with reference partition: - Press Ins during boot
    * Some PS/2s, such as 75 and 90: - Ctrl Alt ?
    * Some PS/2s when pointer at top right of screen: - Ctrl + Ins


hope one of these will work...

---

### Post by mips on 2006-02-01
[QUOTE=Akiha Tohno]I can't call the manufacturer.. I bought it from a used PC place. It's made by IBM, has 1 GHZ, 512 MB RAM, 256 MB video card..[/QUOTE]


What is the ibm MODEL number? That way we can get you the excact bios procedure.

---


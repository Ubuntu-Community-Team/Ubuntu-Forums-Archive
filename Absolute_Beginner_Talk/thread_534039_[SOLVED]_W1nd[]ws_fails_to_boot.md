---
title: "[SOLVED] W1nd[]ws fails to boot"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-08-24
this normally wouldn't be a problem for me, but my mom would like to have a dual boot of windows and ubuntu.

when i installed ubuntu i did the same thing as on my computer, but now that it's done, windows is failing to boot properly. All the information is still there, and it recognizes windows as an OS, but when i select windows, the screen will turn to the windows startup splash screen for maybe 1 second, then drop back and restart the entire computer.

what can i do to fix that?

---

### Post by Tyke91 on 2007-08-24
*bump* :)

---

### Post by Tyke91 on 2007-08-24
i saw this problem before, and i know they solved it, but for some reason, i can't find it again searching the forums

---

### Post by bdoe on 2007-08-24
Just for the sake of curiosity, what's in your /boot/grub/menu.lst file?

---

### Post by Tyke91 on 2007-08-24
her boo/grub/menu.lst says that windows is in

hd(0,0)

which makes sense because its the first one on the first hard drive. 


it starts to boot up windows, but then stops around a second in... i can tell it's trying to boot in the right place, but there is an error with the windows boot script

---

### Post by logos34 on 2007-08-24
> **Tyke91 said:**
> this normally wouldn't be a problem for me, but my mom would like to have a dual boot of windows and ubuntu.

when i installed ubuntu i did the same thing as on my computer, but now that it's done, windows is failing to boot properly. All the information is still there, and it recognizes windows as an OS, but when i select windows, the screen will turn to the windows startup splash screen for maybe 1 second, then drop back and restart the entire computer.

what can i do to fix that?

If this is a typical dual boot installation, then Ubuntu shrank your windows partition.  What is supposed to happen when you boot back into windows for the first time is that checkdisk runs a scan on C: drive--a blue screen should come up right after the splash screen.  

If you have the XP install CD you could boot from that and run it from the recovery console:

chkdsk /r

That's the first thing I'd try (but you need the cd)

---

### Post by bdoe on 2007-08-24
Have you tried booting Windows in Safe Mode?

Or do what ^^^he said.  I hadn't thought about the partition shrinkage problem.  I didn't have that issue myself, since I've got Vista on the first partition, XP on the second, and I split the second partition to install Ubuntu.  Since all three bootloaders are on the first partition, that might be why I dodged that bullet.

---

### Post by pgar23 on 2007-08-24
> **logos34 said:**
> If this is a typical dual boot installation, then Ubuntu shrank your windows partition.  What is supposed to happen when you boot back into windows for the first time is that checkdisk runs a scan on C: drive--a blue screen should come up right after the splash screen.  

If you have the XP install CD you could boot from that and run it from the recovery console:

chkdsk /r

That's the first thing I'd try (but you need the cd)

Logos34 is ryte...this is wut happened to me and when i booted from the windows recovery cd, there was "one or more unrecoverable items"...if this is your case I suggest a fresh install of XP first, then a fresh install of Ubuntu second...if this is not the case just do the recovery cd thing.

logo34...where were you wen I posted a similar thread and almost no one replied...smh :(  
oh well got it fixed now, thats all that matters...

hey man,
GOOD LUCK

if you need assistance w/ the dual boot process, my sig has a google VIDEO TUTORIAL on how to dual boot XP and UBUNTU...check it out

 |
 |
 |
V

---

### Post by Tyke91 on 2007-08-24
windows safe mode didn't work, but using the install cd did... i just went into a terminal (urgh... can you even call that near useless thing a terminal?) and ran CHKDSK /r ... it worked :D


*flagging this as solved since it looks like the only one on the forums


EDIT: i've set up a dual boot on 3 computers now :) it's just that this one happened to be old and farty, and the hard drive isnt as good as it used to be.

---


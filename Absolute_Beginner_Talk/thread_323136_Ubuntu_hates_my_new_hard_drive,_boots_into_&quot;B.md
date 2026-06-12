---
title: "Ubuntu hates my new hard drive, boots into &quot;BusyBox&quot;"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by scooty on 2006-12-21
Hi everyone.

Today I installed a third SATA drive in my PC (500GB Seagate), and now my previously perfect Edgy install will not boot with it at all. After choosing Ubuntu in GRUB, it goes to the loading screen like it normally would, but the the bar will not move at all. Then after about two minutes, it will go to this:
> BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
Now, if I disconnect the drive, it will boot fine with no problems. 

Does anyone know what the problem could be? I'm about to just do a fresh install (not a huge problem since I can still boot without the drive and backup my data), but it would be nice if there was a fix for this.

---

### Post by TwoWordz on 2006-12-21
Have you tried setting the drive order differently in the bios?

because grub is on the mbr of the drive your system boots but probably tries to load the kernel on the first drive. It knows nothing about sata or pata so, depending on your configuration, it must try the first drive. 

TW

---

### Post by scooty on 2006-12-21
I can't change the order. The BIOS already knows its SATA1, SATA2, SATA3, or SATA4 depending on which port I have it plugged into on my motherboard.

---

### Post by scooty on 2006-12-21
Okay, here's something interesting. I replaced my second SATA drive (just used as storage) with this new one, and it boots fine! So there is no problem with the new drive, Ubuntu just freaks out when there are three drives in at once. What the heck is going on ](*,)

One other thing, I don't know how relevant this is, but Windows XP boots and works perfectly with all three.

---

### Post by atarileaf on 2006-12-21
I get the same message when Ubuntu boots:

/bin/sh: can't access tty; job control turned off

In my case I just type "exit" and it boots normally.

I've asked on this forum and googled it as well but I have yet to find a satisfactory answer as to what this tty error is, what it does, and how to fix it.

---

### Post by scooty on 2006-12-21
Did you do a fresh install? If I go that route (which I probably will tonight) that would really suck if it didn't fix this.

Also typing exit at the busybox prompt does nothing for me.

---

### Post by scooty on 2006-12-21
Yeah I've been at this all day, I can't find a solution anywhere. I'm just going to start from scratch.

This is pretty much how I want my stuff set up:
1st drive - 250GB - Windows XP
2nd drive - 250GB - Ubuntu
3rd drive - 500GB - storage for both OS's

Any tips on how I should go about this? I don't really know what order to install everything.

---

### Post by TooRight on 2006-12-22
> 
This is pretty much how I want my stuff set up:
1st drive - 250GB - Windows XP
2nd drive - 250GB - Ubuntu
3rd drive - 500GB - storage for both OS's


 Hehehehe, I want your harddrives!! :P

I have one 250GB and everyone teases me about being a size-queen because I want moreeeeee :D

---

### Post by Craig Caldwell on 2006-12-22
I think I had the same problem.
All I did was plug in my drives into the motherboard differently.
If you have 4 sata headers on your board then you probably have 2 controllers.
Just switch your primary to the other controllers #1 header.
hope that works it worked for me.

---


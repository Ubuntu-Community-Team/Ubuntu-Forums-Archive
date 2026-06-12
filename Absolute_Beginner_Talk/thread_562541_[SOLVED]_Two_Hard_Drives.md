---
title: "[SOLVED] Two Hard Drives"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-09-28
I have 1, 160 Gb hard drive, and 1, 80 Gb hard drive, in my system right now.
Only the 160 Gb is connected to the motherboard. In order for me to use the 80 Gb hard drive, I have to switch SATA cables around.

Hard Drive A, (160Gb) has Ubuntu Feisty Fawn installed on it.
Hard Drive B, (80 Gb) has Ubuntu Feisty Fawn (Command Line Mode) installed on it (installed via the alternate cd.)

Is there any way I can plug both drives into my motherboard, and then be able to choose which drive I want to boot from ?

Experimenting is fun, until it comes to boot loaders, and stuff that could potentially lock me out of my system. I would like to hear advise from the pro's. :D

Dr Small

---

### Post by Shazaam on 2007-09-28
With the proper cabling anything is possible :)
Once you get that sorted out a "grub-update" command should get you going.

---

### Post by Pumalite on 2007-09-28
I imagine they are both SATA drives and that you have a motherboard that supports these drives. Most motherboards have 6 to 8 SATA cables to connect, So unless you have a BIOS problem, I'm at a loss. I don't understand the problem.

---

### Post by Dr Small on 2007-09-28
So, what exactly are you suggesting that I do ?
Hook both hard drives up to the motherboard and then bootup in one of them and run "grub-update" ?

That sounds too simple... Something is bound to go wrong... It always does for me :p

Dr Small

---


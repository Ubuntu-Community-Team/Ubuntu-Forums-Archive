---
title: "How do I make bootable CD?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by FiremanBob on 2007-01-29
I'm trying to install 6.10 onto a Dell desktop (P4) that has no operating system. I have verified that the CD image was correctly burned onto the CD.  I don't have any old DOS disks in the office and the computer does not have a floppy drive. I've been all over download.com and microsoft's site and can't find a set of boot files to put onto a CD. 

How can I boot the computer so that I can install Ubuntu?

Thanks.

---

### Post by Ramses de Norre on 2007-01-29
The cd should be bootable if the image is correctly burned, just pop it in, start and make sure the cd drive is listed as first device in your bios' start up sequence. There should be a message in one of the screen edges on the first black screen when you start the pc about a key to press to enter setup or bios, there you can change that boot sequence.

---

### Post by FiremanBob on 2007-01-29
Thanks. I have already specified the CD as the primary boot drive, and verified it by running my XP installation CD.  What else can I do to get the computer started?

---

### Post by Zzl1xndd on 2007-01-29
if its not booting from the Cd and you have the bios set correctly then there must have been an issue with the Burning process. What program did you use to make the Cd?

---

### Post by irish_flu on 2007-01-29
If it will boot to the Windows CD but not to the Ubuntu CD, it sounds like something went badly during the burn.

The standard Ubunti Live/Installer CD is bootable.

---

### Post by punx45 on 2007-01-29
yep.   make sure that with whatever burning software you used you did the "burn image" option rather than the typical data CD option.   the former will result in a CD with a complete file structure, while the later will result in a cd with merely a file.iso on it.

---

### Post by skyhopper88 on 2007-01-29
Punx is right, I made that mistake last week.

---


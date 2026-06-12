---
title: "Problems installing :S"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by Esteban_Panzera on 2006-08-04
Hi, I have got ubuntu 5.1 and today I made a partition in my disk to install ubuntu. I put the cd and everything went ok. As i have also got win xp, it asked me if I wanted to have GRUB installed and I said yes, the installation was completed, but when I rebooted my pc it was like if ubuntu was not installed, win xp started and it was everything the same :s
what can i do?

---

### Post by Metacarpal on 2006-08-04
When your computer starts to boot up, and you see a message that GRUB is loading, press Esc (there should be a message telling you to do this to enter the menu)

You should then be able to choose between WinXP and Ubuntu.

---

### Post by Esteban_Panzera on 2006-08-04
I don't see the message that grub is loading :s

---

### Post by cheway on 2006-08-04
The "press esc" message to go into GRUB (lasting a few seconds) only comes up (as far as I know) when Ubuntu is the ONLY operating system. With both Ubuntu and Windows installed, it loads into GRUB automatically.

Do you have any other options when you reboot your computer? For example, when I reboot I can press F12 (before GRUB loads) to go into a boot selection manager (hard disk, removeable device, etc).

Another thing you could try is to go into BIOS, and see if you can select your new partition (with ubuntu installed) to be the primary boot device (just for now).

ANOTHER thing you could try is to download GParted Live and burn the image to a CD, and boot to this (Live means that it will run off the CD without installing anything in case you didn't know....). Once booted to this, JUST USE IT TO HAVE A LOOK, and see what you've got going on partition-wise. Don't fiddle around unless you know what you're doing.

And you've backed up all your data on your XP partition right? (just in case, you can never be too careful)

---


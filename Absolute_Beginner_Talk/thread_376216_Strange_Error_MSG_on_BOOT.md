---
title: "Strange Error MSG on BOOT"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by CrisScott on 2007-03-04
I have been trying to install Ubuntu onto an HP Pavillion 712 computer that has two hard drives (Master-Slave on Primary EIDE), a CD ROM drive, and a DVD/CR ROM Writer drive (Slae-Master respectively) on the Secondary EIDE.  BIOS is setup to boot from the drives correctly.  However, when I boot from my LiveCD, the initial screen comes up, I select the "Startor Install Ubuntu" option, the Loading Linux kernel Dialog box comes up, then I get an error: "Unknown Interrupt or Fault at EIP nnn60XXXXXXXXXXXX" message that posts for multiple times, then the system reboots.  Can anyone help me solve this problem?  I have loaded this LiveCD on two other systems (both at work), but can't get it loaded up on this home system.

Pease help, if you can!
Cris Scott

---

### Post by omrsafetyo on 2007-03-04
This could be a motherboard conflict.  Add "linux acpi=off" to the end of the boot parameters from the command line in the CD Menu - and see if that works.

---

### Post by CrisScott on 2007-03-04
I don't see a command line, just the graphic list. How do I get a command line?

---

### Post by omrsafetyo on 2007-03-04
The command line (I believe) is "already there".  If instead of using the arrow keys to navigate, you simpyl start typing (just type "linux acpi=off"), you should see the command line at the bottom of the screen, along with whatever you are typing.  At least I believe this is how it worked for me.

---

### Post by CrisScott on 2007-03-04
I tried this, but there is no command line and simply typing the line of text did nothing.

I also posted this in the Installation Forum, but haven't heard anything from anyone else but you.  Thanks for your attempt.  If you have anyother suggestions, I would love to hear them.

Cris

---

### Post by CrisScott on 2007-03-04
Well, I discovered that I could put this line "Linux acpi=off" onto the 'boot options' by selecting F6.

It is apparently trying to do something.  Will let you know if I am successfull!

Thanks again.
C

---

### Post by omrsafetyo on 2007-03-04
I thought there may be a key stroke - but I couldn't remember for sure.  hope it works.

---


---
title: "Non-Install of Feisty Fawn"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by darkflake on 2007-05-22
Greetings.

I would like to join the Linux world via Feisty Fawn, but I'm having a problem.  I've tried every option on the CD to load the OS, but I only get the following error message across the bottom of the screen:

Int 14:  CR2  cf800000  err  00000000  EIP  c020c384  CS  00000060  flags  00010007
Stack:  c00f7d50  co3f129b  c0371d8c  00000002  c00f7d59  000f7d50  00000000  00000000

My computer is a Compaq Presario, 2.66G Celeron, 256M memory, Compaq FS7600 Monitor w/Inter(R) 82845G/GL/GE/GV Graphics controller.  Windows XP Home Edition (SP2). v2002.

 If I insert the CD while the computer is running, it allows me to download the individual programs show, but it won't boot and run the OS so I can try it.

I really want to upgrade my status to Raw Noob, but if I can't get the OS on my box, well....

Any assistance will be greatly appreciated.

Thank you.

Frank

---

### Post by h0ax on 2007-05-22
How long into the boot process to you get before it drops this error?
I'm guessing you get to the boot parameters screen, which allows you to choose options..
Could you have downloaded a different processor version than x86?

---

### Post by Lucifiel on 2007-05-22
My recommendation is to try the Alternate Installation Cd since it's likely the cd might have problems even running with just 256 mb(or less) of RAM.

---

### Post by johnny4north on 2007-05-22
here is a posting with the same error.  this below maybe a possible solution. 
link - [http://ubuntuforums.org/showthread.php?t=427834](http://ubuntuforums.org/showthread.php?t=427834)
 BenPeeler 
Re: Live CD stops booting after first screen
I GOT IT TO WORK!!!!
Type this after the install cd boots...

linux acpi=off

the hit return
This should start the installer.
note - you may also turn off your ACPI in the bios.  be careful in there.

---

### Post by darkflake on 2007-05-22
Hi, h0ax.

I purchased a CD from Amazon.com because I didn't want to wait a month+ for Shipit.  They had one copy of the x86 CD, so that's what I got.  

It doesn't go anywhere in the boot process.  Right after 'loading kernel', the screen goes blank and the error message shows up across the bottom.  I have a cursor blinking at the top, but it's unresponsive.  I have to power down and restart to use the computer again.

Frank

---

### Post by darkflake on 2007-05-22
Hey, Johnny.

Thanks a bunch.  I'll try this and report back.

Frank

---

### Post by darkflake on 2007-05-22
Hello, again.

Tried the ACPI=off at boot, but  no joy.  I think I'll just wait until I can acquire another computer, a non-Compaq computer.

Thanks to everyone that tried to help.

Peace,
Frank

---


---
title: "Ubuntu error message"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by rafeg on 2007-09-26
I have just tried to install version 6.06 onto a brand new hard drive but get the following message:
   
   MP-BIOS bug: 8254 timer not connected to IO-APIC.

    I have an identical HD on which I have sucessfully loaded SUSE 10.2.  Both drives are new out of the  packages and have never been used  before.

   Can anyone help with this please?

---

### Post by Jimmyfj on 2007-09-26
You could try the latest release of Ubuntu for that drive. Dapper has not as good a hardware support as does 7.04.

---

### Post by darc on 2007-09-26
This sounds like the APIC problem...

On boot, pass 'noapic' to your kernel.  Refer to this thread for more info on solving the same problem:
[http://ubuntuforums.org/showthread.php?t=560243](http://ubuntuforums.org/showthread.php?t=560243)

Let us know if that doesn't help.
-darc

---

### Post by wpshooter on 2007-09-26
Have you tried setting all of the BIOS parameters back to the defaults ?

---

### Post by rafeg on 2007-09-26
Thanks to you all for such rapid responses to my question.  I've decided to order the latest version and see if that works.  I can't get into the bios to enter noapic since I can't even load the os to start with.  Pressing F6 goes nowhere!  I have had earlier versions of Ubuntu on an older computer with no problems but this machine is relatively new so perhaps the fiesty version will be the answer.  We shall see!

---

### Post by darc on 2007-09-26
Your BIOS runs before the OS loads.  It's the black and white screen that very first happens when your computer turns on.  Though, sometimes it gets covered by a computer maker logo (like toshiba, HP, etc) and you can hit ESC to close the logo/splash screen and see the POST messages from the BIOS.  It should also tell you what key to hit to enter your BIOS settings... it's usually one of the following : TAB, DEL, F1, F2, or F11. 

But, you don't enter the 'noapic' in the BIOS, that's just where you set all your hardware settings to default.

The 'noapic' goes in your GRUB menu as listed in the thread I linked you to:

> 
Do you get the GRUB boot menu when you start your computer up? Or, does it go straight into booting Ubuntu?

1) If you get the GRUB menu, hit ESC and find the kernel line, then hit 'E' to edit it, and add noapic at the end. Then hit whatever key it tells you to save it, then 'B' to boot it. If this works, then you can edit /boot/grub/menu.lst to make it permanent.

2) If you don't get the GRUB menu, it's set to auto-boot your kernel and you need to give it a time to wait (or try smashing 'ESC' frantically as soon as the computer passes the POST) which can be done by editing /boot/grub/menu.lst

NOTE: My steps may not be exact because I'm at work on a windows machine (I know... it sucks!) so I can't try it on my Linux machine and be sure.


Let us know if you want to keep trying or just wait for the new version to come/download.
-darc

---

### Post by rafeg on 2007-09-27
Darc,         Thanks for your reply.  You'll see that I'm a total dimwit with Linux but learning slowly.
                  For now I'll wait for Fiesty to arrive but I've bookmarked your instructions for future reference.
                           I use plug in Hard drives so as not to risk my Windows installation and this frees me to
                  do what I like with Linux.  My main problem now is a thing called work!  I have to go!!

---

### Post by darc on 2007-09-27
I know how that goes, luckily I'm posting from work right now : D

Good luck, just post if Feisty doesn't solve your problems.
-darc

---

### Post by rafeg on 2007-10-27
Sorry to be so long in getting back on this thread.  I've tried again to install 6.06 without success.
I'm afraid I don't understand how to get into GRUB to write noapic.  Have since aquired 7.04 64 bit
as I have a 3500 athlon 64 processor.  No luck with this either.  I get a message saying
 Can't access tty; job control turned off.  
  May I presume on your patience to help with this please.

---

### Post by rafeg on 2007-11-02
Have just received Gutsy Gibbon cd.  It installed ok but only in OEM mode.  At least I now have Ubuntu up and running.  Very pleased with it so far.  thanks to you all for your attempts to help with earlier installations.  I'll be looking at other threads now for guidance on various things.

---


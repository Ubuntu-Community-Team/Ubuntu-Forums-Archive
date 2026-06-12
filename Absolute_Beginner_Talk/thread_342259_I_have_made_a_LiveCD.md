---
title: "I have made a LiveCD"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by bryctucker on 2007-01-19
I just made a LiveCD but it will only tell me how to how to get it to work i have rebooted my computer but it wont work and left the CD in the CD Drive

---

### Post by mikewhatever on 2007-01-19
Make sure your BIOS is set to boot from the CD. If you do not boot from the CD, but just put it in the tray and close, does it load the wellcome screen?

---

### Post by thomasbaker on 2007-01-19
Make sure you check to the bios on your system. Make sure it set to boot from cd.  Also make sure you burn the .iso image to the cd. and not just copy it to a cd

---

### Post by jvc26 on 2007-01-19
You have to enter BIOS - usually pressing DEL during the BIOS sequence (at the start of boot) Then navigate to your boot options (under one of the headings) select 'CDROM' as first boot option then save and exit. On rebooting you will boot from the cd. Is this what you are inquiring about?
Il

---

### Post by irish_flu on 2007-01-19
Your computer might not be set up to boot to a CD.

Reboot it again, and enter the BIOS.

To get to the BIOS:
As soon as the computer starts to boot (right after it beeps) look for some text on the screen that says "Press F12 to Enter Setup" or "Pres DEL to enter setup" or something like that.

This "setup" area is called the BIOS (Basic Input-Output System).  When you enter this area, look around a bit.

You'll see something called  "Boot Order".  It might be a tab up at the top, or it might be an option within ""Basic Setup" or "Advanced Setup".

When you find this "Boot Order", you'll see things listed like "Hard Drive 0" and "Floppy" and "CD-ROM".  It might not be exactly like that, but it will be something similar.

There should be instructions there for how to change this order around.  Your mission here is to set it up so that it looks for a CD-ROM before it looks for your hard drive.

Save your changes and Exit.  Your PC will reboot, and either it'll automatically boot to the CD or you'll see something during the boot that says "Press any key to boot to CD".

Done!


Some advice for working in your BIOS:
If you don't know what something is, don't change it.  If you think you might have accidentally changed something but aren't sure, find the key (usually ESC) to "Exit without saving" and start all over.

---


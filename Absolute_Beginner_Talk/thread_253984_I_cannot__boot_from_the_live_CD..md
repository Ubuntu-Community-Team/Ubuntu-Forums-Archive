---
title: "I cannot  boot from the live CD."
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by holymuffins on 2006-09-09
:confused: I would like to try out ubuntu, but I cannot boot from the live CD. I put the disc in my drive, restart the computer, and my computer restarts like normal, and winXP shows up. I am not good with computers, and theres probably somthing obvious I am missing, Thanks in advance.

---

### Post by elpuerco on 2006-09-09
You need to reboot your computer, press F2 or whatever to get into BIOS setup and locate the boot options.  Set it to CDROM first boot device.

Save settings 

Put CD in drive and reboot and away you go

---

### Post by seshomaru samma on 2006-09-09
2 possibilities*
the first - you didn`t burn the CD correctly . you need to burn the Ubuntu files as `image` . you can read here about it *[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)

the other possibility is that you didn`t set the BIOS correct
the BIOS is what tells your computer where to boot from
what you need to do is reboot and when the first screen comes up press one of those :Escape, F1, F2, F12, or Delete , this will take you to a menu (which looks different on each computer) where you can choose the boot order. Choose  boot from Cd as first (dont forget to change it back to what it was after you finish installing)

---

### Post by Buddha443556 on 2006-09-09
You can probably can get in your BIOS by pressing either the F1 or delete key during startup. This is the time when the manual for your motherboard comes in real handy. ;)

---

### Post by bodhi.zazen on 2006-09-09
> **holymuffins said:**
> :confused: I would like to try out ubuntu, but I cannot boot from the live CD. I put the disc in my drive, restart the computer, and my computer restarts like normal, and winXP shows up. I am not good with computers, and theres probably somthing obvious I am missing, Thanks in advance.

LOL 

You have to set your BIOS. Change Boot order.

Boot your box. As it is booting you will need to hit Escape, F2, F8, who knows. You may see a text message. Otherwise Hit them all!!!

This will enter BIOS.

Look for the boot or boot order section.

Change it to:
> First - CD ROM/DVD

Second- Floppy

Third Hard Drive.

Save and exit. 

Continue booting, if you boot to windows again, reboot. 8)

---


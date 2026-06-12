---
title: "Neither Alternate nor LiveCD work.  Why?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by GrahamCracker on 2007-05-09
I got Ubuntu running with LiveCD on my main computer, but I also want to install it on my backup PC.  I tired LiveCD first, but when I reboot, I get a "cannot boot from this CD" message, so I dowloaded the Alternate CD and have the same problem.  If I explore the CD, is there an icon I can just click on to get the intallation started?  or does it have to start up with the CD?
Thanks.

---

### Post by starcraft.man on 2007-05-09
> **GrahamCracker said:**
> I got Ubuntu running with LiveCD on my main computer, but I also want to install it on my backup PC.  I tired LiveCD first, but when I reboot, I get a "cannot boot from this CD" message, so I dowloaded the Alternate CD and have the same problem.  If I explore the CD, is there an icon I can just click on to get the intallation started?  or does it have to start up with the CD?
Thanks.

If you got it from both CDs exactly the same, it doesn't sound like an anomaly. Can you check your BIOS? Usually when you start up you should see a screen from your manufacturer, you may have to push Esc/F2/F10/F12 to get to the menu. Then navigate to whatever menu controls your boot order, check to see that CD is the first option on that computer. Some BIOS (like mine) are older and instead of a boot order, I actually select the option directly to boot which CD drive/other media I want. If you have that make sure you are manually booting the right drive.

Post back with whatever happens, if its not BIOS then you should reburn the ISO of alternate install on the lowest possible setting. I've yet to hear of a system completely incompatible with Ubuntu.

---

### Post by GrahamCracker on 2007-05-09
I went to the BIOS first, and it has the order as the CD, then C drive, then A drive.  It says 130+ MB  RAM,. so from what I understand, the Alternate CD is what I need for this computer.  Both CDs cause the same "cannot boot from this CD" error, then there is a line with the word Debian in it, so there is something wrong, but I just don't know what I should try next, if anything.

---

### Post by Sef on 2007-05-10
How much ram does your computer have?  If it is less than 256 mb ram, then [Xubuntu]("http://Xubuntu.org") would be a better choice.  It is made to run on hardware from 64 mb ram (though 128 mb ram is recommended.)

---

### Post by GrahamCracker on 2007-05-10
Okay, I'll try installing Xubunut on it.  Is Xubuntu similar, in that it has an easy to use desktop interface and Firefox 2 browser on it?
Thanks.

---

### Post by Sef on 2007-05-10
The backend of Ubuntu and Xubuntu is the same, but the desktop is different.  Ubuntu is based on Gnome, and Xubuntu is based on XFCE.

---

### Post by umarvlie on 2007-05-10
If it is a reallly old PC the BIOS might not support booting of CD unless there is a boot floppy image on it (there are 2 ways of booting from CD as i understand). That might cause the issue, you can check that if you happen to have an old Win98 CD that does boot with teh floppy image on CD (as you boot from that CD you get the A:> prompt as it simulates a floppy drive rather than a real CD).

Dont know if there are boot floppys available for Ubuntu to help get you underway in that case.

---

### Post by Sef on 2007-05-10
> If it is a reallly old PC the BIOS might not support booting of CD unless there is a boot floppy image on it (there are 2 ways of booting from CD as i understand). That might cause the issue, you can check that if you happen to have an old Win98 CD that does boot with teh floppy image on CD (as you boot from that CD you get the A:> prompt as it simulates a floppy drive rather than a real CD).

Dont know if there are boot floppys available for Ubuntu to help get you underway in that case.

If that is the case, get [Super GRUB Disk]("http://supergrub.forjamari.linex.org/").

---


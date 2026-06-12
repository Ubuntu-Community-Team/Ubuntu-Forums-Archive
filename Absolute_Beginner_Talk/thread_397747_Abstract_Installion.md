---
title: "Abstract Installion?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Psyik on 2007-03-31
My friend has this old Toshiba laptop. The model escapes me, but I do know it has only 128 MBs of RAM, and a DVD-ROM. Since it has so little RAM, I can't try to use a LiveCD. So I've been trying to install Xubuntu on it using the alternate install CD, but the CD always goes bad.

The first thing I do is the disk check, and get a "everything's just fine" response. So I start installing, but at some point I start getting disk error messages. The place of the error keeps changing. I know it isn't because of an improper burn since I used data verification (confirms that there were no errors on burn), slower speeds, and different burners. I've been using the brand for a long time (Verbatim), so I know it isn't poor CD quality/life. The laptop is literally eating CDs.

But I don't want to get up just yet. I've tried switching CDs mid-installation, but that doesn't work. I doubt that the USB ports on the thing are 2.0s, but it does have a floppy drive.

What I'm thinking is: is there a way to get a USB driver on a floppy, and have the floppy recognize and boot my flash drive, conveniently loaded with the Xubuntu alternate CD?

And no, the bios doesn't have an option to boot from USB. It's far too old for that.

---

### Post by Brendantb on 2007-03-31
Hi, 

I had an old toshiba laptop too, and I looked around the net to see if I could enable usb booting where the bios didn't support it. The consensus seemed to be that while it was theoretically possible, there wasn't anyone who had successfully done it. 

Rather than waste time trying, I would suggest that you look into installing using ethernet, or if you have a pcmcia slot, using an external cdrom on that - early toshibas supported booting from pcmcia drives, but you have to use the alternate cd. 

I am puzzled that your machine seems to be "eating cds." Have you tried to use these same cds afterwards on another drive to check their integrity?

---

### Post by david_kt on 2007-03-31
Could you remove the harddisk and install ubuntu in it using other computer? You might need adaptor if you use desktop computer. After it is operational in other computer, put it back to the laptop. When you boot, you might not able to start x (not configure properly). Run this command:

[INDENT]sudo dpkg-reconfigure -phigh xserver-xorg[/INDENT]

Hopefully after that it could run properly.

DK

---


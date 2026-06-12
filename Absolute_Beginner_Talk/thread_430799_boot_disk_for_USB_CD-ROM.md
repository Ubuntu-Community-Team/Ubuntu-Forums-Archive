---
title: "boot disk for USB CD-ROM"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by cobra_style on 2007-05-02
Hey everyone,

So I recently downloaded Ubuntu 7.04 (x86) to install on this Dell laptop I have from 2000.  The problem is that the DVD/CD ROM drive is acting up (drive motor seems to be failing) so although I can boot to my Ubuntu CD, it always bails out while loading.

I do have a external USB CD-ROM drive (USB 1.1) that works fine with that laptop when I'm using Windows.  The floppy drive on the laptop works fine as well so I was hoping someone could point me to a bootdisk image that would allow me to use the USB CD-ROM drive to load and install Ubuntu.

So long story short, I need bootable floppy to enable my USB CD-ROM drive so that I can boot the Ubuntu CD.

Thanks for any assistance!

---

### Post by Cypher on 2007-05-02
Check to see if your BIOS supports booting from USB, if it does, you should be able to use the USB CD-ROM without the need for a bootable floppy..

---

### Post by starcraft.man on 2007-05-02
I could be wrong here, but wouldn't you need your bios to support this attached cd/dvd drive? Boot into your bio by pushing your manufacturers key, F2 F12... one of em. Then check you can boot from a USB.

Not to mention now adays DVD burners are getting to be almost dirt cheap, you could buy one in canada for under 60$ new.

---

### Post by cobra_style on 2007-05-02
The BIOS does not support booting from USB (remember the computer was made in 2000).  The only options on the Boot menu are:

[LIST=1]
[*]CD\DVD drive
[*]Floppy drive
[*]Internal drive
[/LIST]

I checked Dell's support site for my laptop (I was amazed they still listed it) and I have the latest BIOS that was made available for my model (Inspiron 7500).

---

### Post by orb9220 on 2007-05-02
I believe if you download the alternate CD it allows you to install the grub to the floppy.
Not sure tho it is a vague rememberence.

---

### Post by cobra_style on 2007-05-02
I took a look at the GRUB documentation and it does not seem to include the support I need.  What I really need is something that can bootstrap a USB CD-ROM drive with a bootable CD in it.  This magic bootdisk that I need would have to include interfaces for both USB and some generic CD-ROM driver.

---

### Post by techpr on 2007-07-04
I have this issue too. I'm trying to install 7.04 on a toshiba laptop with a bad CD-ROM drive and cannot boot from USB (old BIOS). I only have the floppy working. Any help with a driver so I can load an external USB CD-ROM?

---

### Post by neodarksaver on 2008-03-29
same problem with a L2000 HP. i used to be able to boot from usb, i think they took the support away in a bios update for some reason. now i have a bad drive.

---


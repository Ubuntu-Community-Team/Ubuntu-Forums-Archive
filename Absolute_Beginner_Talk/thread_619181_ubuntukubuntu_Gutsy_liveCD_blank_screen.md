---
title: "ubuntu/kubuntu Gutsy liveCD blank screen"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by faux_05 on 2007-11-21
i know there is bits of this around everywhere, but nothing i have done has worked thus far...

the ubuntu and kubuntu gutsy liveCD wont boot... it runs through everything until it starts the kdm/gdm. at that point i get a blank screen.

i have tried everything listed in this thread: [http://ubuntuforums.org/showthread.php?t=259575](http://ubuntuforums.org/showthread.php?t=259575) and elsewhere on the forums
however, i was unable to get the x server to restart after making the changes. it wouldn't restart (ctrl+alt+bkspc) and force-reload gave the error (GDM/KDM not running), startx (no screens found)

Specs:
AMD AM2 3800+ (64bit)
1.5 GB RAM
Asus M2N-MX SE mobo
ATI Radeon X1600 PCI-E (PCI 0:2:0:0)
ASUS VW192T monitor by DVI

Thanks

---

### Post by Sef on 2007-11-21
1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

3) Have you checked the disk the disk for errors?

4) Have you run the live cd sucessfully on another computer?

---

### Post by coolguy2006delhi on 2007-11-21
Do you have the 64 bit edition of the cd or the normal one?

---

### Post by faux_05 on 2007-11-22
i have md5d the dl, checke dthe disc for errors, burned it slowly, and the 32bit disc runs fine on my laptop. i have tried both the 32 (noapic) and 64bit discs on the pc, im \trying to get 64 running tho...

---

### Post by AySz88 on 2008-01-18
I had the same symptoms, and I also happen to have an nVidia 8800 GTS (320MB).  I found the solution here: [https://bugs.launchpad.net/ubuntu/+bug/140908](https://bugs.launchpad.net/ubuntu/+bug/140908)

...basically, select the option you want, then press "F6" and delete "quiet" and "splash" from the end of the string.  Then, after installing, boot into recovery mode and modify /boot/grub/menu.lst , then remove the kernel option "splash".

Apparently, it's "an xorg problem". :( Very time-consuming....

---


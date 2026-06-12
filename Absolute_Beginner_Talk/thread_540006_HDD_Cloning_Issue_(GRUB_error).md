---
title: "HDD Cloning Issue (GRUB error)"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by maleficarium on 2007-09-01
Recently I decided to upgrade my PC starting off the HDDs, so my current lineup is the following

A: 200GB HDD (Windows installation)
B: 250GB HDD (2 partitions: files and Linux)
C: 250GB HDD (files)
D: 750GB HDD (files)

The problem arises when I try to one my windows HDD into a newer smaller HDD (120GB) though Norton Ghost. The cloning goes fine but when I replace my A HDD with the new 'clone' and try to boot I get to a screen with only "GRUB" on it, no error message or anything else I can do. 

If I replace the 'clone' disk with the original the system boots normaly giving me the option to choose between Windows and Ubuntu.

---

### Post by southernman on 2007-09-01
Sounds as if ghost didn't copy the mbr info... never used it so I can't say if its a bug or just natural for ghost.

You can look into partimage which you can get on a livecd called systemrescuecd and cop/clone your drives with it. Only thing, when you restore a copy to a new drive, the partitions have to be setup exactly as they were before... well maybe larger is ok, but certainly not smaller.

hth's

---

### Post by ramjet_1953 on 2007-09-01
Ghost for Linux (G4L) works a treat!

You can get it from here: [http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

It is an iso that you burn to a CD. You then boot from the CD and choose the local clone option.

Don't forget to burn the iso SLOWLY, no faster than 4 X, for an error free CD.

Regards,
Roger :cool:

---

### Post by maleficarium on 2007-09-01
Problem was partialy solved by using MBRFix ( [http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm) ) to setup MBR on the 'clone' HDD. Windows boots normaly now, only thing left is to setup GRUB so I can dualboot linux.

I doubt the problem was Norton Ghost not copying the MBR since it used to work fine on cloning in the past when I didnt have Linux installed. I think the problem was Ubuntu being 'sensitive' to the change of the HDD (size difference probably?)

---

### Post by kaysersoze on 2007-09-04
I'm not sure if we have the same problem but here is what I did:

I successfully cloned my laptop which was running ubuntu 704 using Ghost 8. But when I restored the image, I got a continues "GRUB GRUB GRUB ..." message filling the screen upon booting it up.

Here is what I did to fix it up (found using google)

1.) boot laptop with ubuntu 704 livecd
2.) opened a terminal and switched user to root
3.) on the terminal typed: grub
4.) in grub, typed: find /boot/grub/stage1
5.) it then displayed something like (hd0,0)
6.) typed: root (hd0,0)
7.) typed: setup (hd0)
8.) typed: quit to exit

After restarting, everything was ok.

---


---
title: "Help"
date: 2008-03-27
forum: Apple PPC Users
---

### Post by goodfelix on 2008-03-27
Yesterday I download Ubuntu 7.10 desktop cd  PPC and burnt it into a cd by NERO. However, either I press C or alt-command-shift-delete when it start, the cd can't boot (the cdroom is ok, and I heard it was reading the cd). Even I hold alt to start, I can only see there is only a system hard drive there, can't find the cd.
I'm sure I download the right version and burnt the image in "minimum speed", Please Help. My machine is IBOOK G4, should be competible.
Do I need to boot the yaboot, how can I?

---

### Post by adelahunty on 2008-03-27
Your machine should definitely be able to run the CD, so let's just check the obvious first:

1.  You downloaded a PPC version, and not one for an i386, Sparc, etc?

2.  You burnt the CD as a disc image, and didn't just copy it over to the burning dialog to copy what you downloaded to the CD?  Way to check - open the CD in another operating system (such as Mac OS), and see what's on the CD.  If it is a big file which just ends in iso, that's your problem.

---

### Post by goodfelix on 2008-03-27
Thanks for your reply. I'm sure it's the right version and I checked it many times. And also I believed I burnt it in a right way. So I have rally no idea why cd can't boot.

---

### Post by Kasa on 2008-03-27
ok 
1) hold down Apple+option+f+o
2) is it an internal or external CDrom drive ?
3) type in this code if external, I will look up the code for internal I expect it to be something like boot cd
```
boot fw/node/sbp-2/disk:,\install\yaboot
```
but try it anyway.

---

### Post by goodfelix on 2008-03-27
It's internal, but I tried it, it showed"can't open device or file"

---

### Post by fussyoldfart on 2008-03-27
I have a lot to learn about Ubuntu on a Mac but on my G5 2 GHz iMac I don't need a 4 finger guitar chord, I hold down the option key as the machine reboots with the CD in the drive. This presents the available boot volumes including the optical drive. Click on that and away I go!

---

### Post by goodfelix on 2008-03-27
I tried it before, it only showed the hard drive, is it because the machine can't recognise the cd-room? but I did hear the sound from the cdroom when it was reading the cd, just can't boot

---

### Post by driven1 on 2008-03-28
I would start over by burning a new iso, then press and hold the "C" key while restarting the machine. I noticed that my powerbook was rather picky about the cd that it would boot from. btw, are you try to book from a live cd or alternate install? You will have better luck with the alt install iso as a general rule. Good luck.

---


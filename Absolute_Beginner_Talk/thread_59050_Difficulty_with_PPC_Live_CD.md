---
title: "Difficulty with PPC Live CD"
date: 2005-08-22
forum: Absolute Beginner Talk
---

### Post by DJCreation on 2005-08-22
So I'm trying to boot from the PPC Live CD to my PowerMac G4 (dual 867s, 60 GB IBM HD, Philips CDD5101, 256 MB RAM), but having no luck. When booting from CD (holding 'c' at start-up) I get a lovely maroon-colored screen that does not change. No sound from the HD or the CD either, though the fan winds up and down every 30 seconds or so. Keyboard and mouse are kaput.

The ISO is, as far as I can tell, fine.

I've also tried booting holding 'option' at start-up, and this shows the CD as bootable (CD + tux image and everything), but attempting to boot from this goes nowhere (clicking on CD+tux and hitting the arrow button refreshes the screen with bootable disk options).

I can't help but feel like there's something blatantly obvious I'm missing... can anybody tell me?

---

### Post by aysiu on 2005-08-22
[QUOTE=DJCreation]
The ISO is, as far as I can tell, fine.[/QUOTE] When you say "as far as I can tell," what have you done to ascertain its integrity?

---

### Post by DJCreation on 2005-08-22
... that'd be nothing. I haven't, so far, found out how to check integrity from OSX.

---

### Post by aysiu on 2005-08-22
[QUOTE=DJCreation]... that'd be nothing. I haven't, so far, found out how to check integrity from OSX.[/QUOTE] 

[http://lists.terrasoftsolutions.com/pipermail/yellowdog-newbie/Week-of-Mon-20040510/005632.html](http://lists.terrasoftsolutions.com/pipermail/yellowdog-newbie/Week-of-Mon-20040510/005632.html)

You may also (even if the image is good) want to burn the image at a slow speed (2x or 4x).

---

### Post by DJCreation on 2005-08-22
[QUOTE=aysiu][http://lists.terrasoftsolutions.com/pipermail/yellowdog-newbie/Week-of-Mon-20040510/005632.html](http://lists.terrasoftsolutions.com/pipermail/yellowdog-newbie/Week-of-Mon-20040510/005632.html)

You may also (even if the image is good) want to burn the image at a slow speed (2x or 4x).[/QUOTE]
 No luck with disk utility (internal file system error).

md5 at the terminal prompt renders a hexidecimal value - what do I check this value against?

---

### Post by aysiu on 2005-08-22
[QUOTE=DJCreation]No luck with disk utility (internal file system error).

md5 at the terminal prompt renders a hexidecimal value - what do I check this value against?[/QUOTE] Where did you download the image from? There's usually a text file called MD5SUM something...

---

### Post by DJCreation on 2005-08-22
[QUOTE=aysiu]Where did you download the image from? There's usually a text file called MD5SUM something...[/QUOTE]
 Downloaded from the Ubuntu website.

I have the md5sum.txt file from the disk(-image). The file has the md5sum values for all the files contained within the disk-image - do I need to check each individually, then?

---

### Post by xmastree on 2005-08-22
You didn't make the newbie mistake of putting the ISO on the CD rather than using it to create the CD did you?

Take a look [**here**](http://xmastree.34sp.com/ubuntu/burn) at a page I made to help people with this.

It's for XP and Nero, but it might help you. Particularly the last bit. What do you see if you look at what's on the CD?

---

### Post by DJCreation on 2005-08-22
> You didn't make the newbie mistake of putting the ISO on the CD rather than using it to create the CD did you?

What do you see if you look at what's on the CD?

The files from the virtual disk. I've burned it using Disk Utility (from OSX) as well as having a go at burning with FireStarter FX. Both render CD-Rs with the full dir/files list rather than a single ISO image.

---


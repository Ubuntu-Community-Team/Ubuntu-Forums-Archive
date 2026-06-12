---
title: "Is my CD burn invalid or what?"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by dderolph on 2006-07-01
I downloaded Ubuntu 6.606 and burned the ISO file to a CD.  If I try to boot from the CD, the screen stops with "[DR-DOS] A:\>" at the bottom.  Two line above that: Caldera DR-DOS 7.03.  If I enter dir, I see an executable file named WWBMU.  If I type it at the prompt, I get a message saying "Not enough memory".  

Specs: Athlon XP 2200, 512MB RAM, nVidia GeForce4 Ti4200, with two monitors attached.

---

### Post by nalmeth on 2006-07-01
Is your BIOS set to boot from CD-ROM?

---

### Post by Jagot on 2006-07-01
You did actually burn it as a disk image rather than a data cd right?

You could try checking the MD5SUMS.  Take a look here:

[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)

---

### Post by aysiu on 2006-07-01
Did you do something similar to this? [http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

---

### Post by dderolph on 2006-07-01
Yes, my BIOS set to boot from CD-ROM.

Yes, I burned a bootable CD using Nero Express.  

Yes, I did use the MD5SUMS procedure to verify the file; it was OK.

Yes, I read [http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html) before downloading and burning.  I just looked at it again and see a comment about burning speed.  I did not throttle back my burning speed; as I recall, it burned at 48X.  Do you think I should burn again, at slower speed and see whether that makes a difference?

---

### Post by Jagot on 2006-07-01
[QUOTE=dderolph]Do you think I should burn again, at slower speed and see whether that makes a difference?[/QUOTE]

You can give it a try and see if it works - it's worth a shot.

---

### Post by cacharreo on 2006-07-01
Check if you cd i burned rightly

---

### Post by cacharreo on 2006-07-01
Check if you cd si burned rightly

---

### Post by dderolph on 2006-07-01
[QUOTE=Jagot]You can give it a try and see if it works - it's worth a shot.[/QUOTE]
Well, I tried burning at 8x; it did not work.  Then, I successfully burned at 24x but the CD behaved the same as my original CD.  I wonder whether I should download the free burning software mentioned in the reference previously cited and try it for this purpose.  

Can anybody confirm whether Nero Express should work for this?  Again, I selected bootable data disc when creating the burn job.

---

### Post by confused57 on 2006-07-01
> **dderolph]Yes, my BIOS set to boot from CD-ROM.

Yes, I burned a bootable CD using Nero Express.  

Yes, I did use the MD5SUMS procedure to verify the file said:**
> http://www.psychocats.net/ubuntu/iso.html[/url] before downloading and burning.  I just looked at it again and see a comment about burning speed.  I did not throttle back my burning speed; as I recall, it burned at 48X.  Do you think I should burn again, at slower speed and see whether that makes a difference?

I have Nero, which has an option to burn a bootable cd...that's _not_ what you want to do.  There is an option to "burn image to disc", that's how you want to burn the iso.

---

### Post by fhqwhgads on 2006-07-01
Is there a floppy in your A: drive? Maybe a partitioning software you were using?

EDIT: above post is likely the answer. The Ubuntu ISO is already a bootable disc, don't use that option.

---

### Post by crystal on 2006-07-01
> Can anybody confirm whether Nero Express should work for this?
Yes. I used Nero Express 6 with the "Disc Image or Saved Project" option.

---

### Post by richbarna on 2006-07-02
[QUOTE=crystal]Yes. I used Nero Express 6 with the "Disc Image or Saved Project" option.[/QUOTE]

When I used to use Nero, I found the easiest way was to right click on the iso, and select open with...... and scroll down to Nero and accept.
This way Nero does the configuring for you, you just choose 8X burn and you should end up with a bootable CD.

---

### Post by dderolph on 2006-07-02
Thanks for replies, everyone.  Indeed, the problem was my erroneous setting up of the burning procedure.  I tried the the "Disc Image or Saved Project" option and that worked.  When I start with CD-ROM set as first boot device, the Ubuntu screen appears which lists options:

Install in Text Mode
Install in OEM Mode
Install a server
Etc.

And then, across the bottom of the screen:
F1 Help  F2 language  etc.

---


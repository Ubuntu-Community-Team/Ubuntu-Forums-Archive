---
title: "Can't boot into Ubuntu Live - First time user"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by michaelr on 2006-11-15
I've downloaded the latest release of Ubuntu to give it a try, and am currently trying to boot into the OS from the CD I made, with little success.

In both the full graphical mode, and graphical safe mode, the OS almost loads fully, but stops just a couple of bars from the end, and display a band of corruption across the middle of the screen.  It just stops here and does nothing more.  Please see the attached picture to demonstrate.

My system specs are

Athlon64 X2 3800+
3Gb RAM
Radeon X800XL
NF4 SLI

Can anyone offer any advice as to how to make this work?  I've tried other Linux distros before, and I've always thought they need to be made more user friendly for anyone to actually want to use them.  Here's another case in point...

TIA,

Michael.

[IMG]http://img.photobucket.com/albums/v420/mrochester/16112006021.jpg[/IMG]

---

### Post by TheRingmaster on 2006-11-15
you maybe have a bad disk. Try burning it again at a slower speed. this usually helps.

---

### Post by michaelr on 2006-11-15
Hi there,

I will give that a try, thanks!  BTW, I'm using the ImgBurn program suggested on the site as Nero just wouldn't play ball at all!

---

### Post by Redache on 2006-11-15
Yeah try it at about 4x since that's within safe levels for a good disk. They make 'em fast but it doesn't make 'em safe. I've had a few coasters made since I first had a CDRW! 
God Nero....That thing is bloated, Ugly and full of crap. I love Nero Vision, brilliant DVD encoding the rest is just UGH!

---

### Post by TheRingmaster on 2006-11-15
> **Redache said:**
> Yeah try it at about 4x since that's within safe levels for a good disk. They make 'em fast but it doesn't make 'em safe. I've had a few coasters made since I first had a CDRW! 
God Nero....That thing is bloated, Ugly and full of crap. I love Nero Vision, brilliant DVD encoding the rest is just UGH!
You can always erase a cd-rw and use it again.

---

### Post by Redache on 2006-11-15
I meant in the sense of the drive rather than disks. the Disks are too expensive in erasable glory :P

---

### Post by 56phil on 2006-11-15
I could not boot Edgy (6.10) either. I had success with a Dapper (6.06.1) CD in safe graphics mode. It's worth a try. Good luck.:)

---

### Post by michaelr on 2006-11-16
Well I have tried burning the image at 4x speed, and unfortunately I have exactly the same problem :( Any other ideas?

Thanks,

Michael.

---

### Post by to4i on 2006-11-16
That's the Ati driver. :)
I had the same problem. Download the alternate-install cd and install Ubuntu in text mode, but that's not all :P
After install, restart and go to recovery mode and change the device driver name in /etc/X11/xorg.conf from "ati" to "radeon".

---

### Post by michaelr on 2006-11-16
Sorry what?  I'm beginning to see why most people don't use Linux... I feel like this everytime I try a distro.  Not one seems to 'just work'.  Thank god for Windows eh?!

---

### Post by to4i on 2006-11-16
Ok, use the search button, the problem is from the Xserver, try these threads:
[http://www.ubuntuforums.org/search.php?searchid=9837586](http://www.ubuntuforums.org/search.php?searchid=9837586)

---

### Post by manishk on 2006-11-16
**I'm not sure about this...(I'm a noob too)**

When I had similar problems booting from the LIVE CD, I tried the *noapic* parameter at the boot prompt and it worked!!

Heres how I did it [Again, **I am not sure** whether this'll work for you.]

In the LIVE CD, when you get the boot options in the beginning at the bottom of the screen theres a menu which has something like 'Boot Options' (F6, i guess). Press it.

At the end of the line that pops up add this word:

noapic

And press ENTER.

---


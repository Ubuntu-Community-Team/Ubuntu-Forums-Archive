---
title: "Imac 8,1 which version of ubuntu to download and install?"
date: 2010-06-06
forum: Apple Hardware Users
---

### Post by johntkucz on 2010-06-06
Have iMac 8,1.  How do I pick which one to download nad what's the link to that? thanks.  I see a lot of documentation on macbooks but not much on imacs.

I downloaded a version of ubuntu 10 lucid and when I "c"-key boot it just blinks an underscore and doesn't boot.  That same live cd does load on macbook though.

---

### Post by sha.goyjo on 2010-06-06
If the 8,1 is the one I think it is (ie if it is aluminum cased) than you want lucid 64-bit from the main page.

---

### Post by johntkucz on 2010-06-07
> **sha.goyjo said:**
> If the 8,1 is the one I think it is (ie if it is aluminum cased) than you want lucid 64-bit from the main page.

Thanks mate!  I have been downloading that.  Only prob is I downloaded some version...I think it was 32-bit and that one didn't boot on the imac.  hopefully 64 version will thanks.

---

### Post by johntkucz on 2010-06-07
> **johntkucz said:**
> Thanks mate!  I have been downloading that.  Only prob is I downloaded some version...I think it was 32-bit and that one didn't boot on the imac.  hopefully 64 version will thanks.


Hey again.  I expect (but hopefully not) this thread to be long and convoluted.  But...what format do I format the HD as ?  Disk util only offers 4 formats none of which seem applicable except maybe ms-dos fat32???

I found a lot of dual and triple boot guides many mentioned
refit
not using boot camp
etc

I can't even boot off the live cd so I guess until I get that fixed will be difficult to install to hd.

---

### Post by sha.goyjo on 2010-06-07
What setup are you looking for? Do you want a dual boot, a triple boot? For a triple boot you will need to use refit (it's absolutely necessary). I'm not the man to ask, as I dual boot Ubuntu and Windows XP on my MacBook. But there are PLENTY of rEFIt Triple Boot tutorials on the web.

Also, please don't try to put ubuntu onto a fat32 partition. You want ext4 or reiserfs, but not fat32.

---

### Post by johntkucz on 2010-06-08
> **sha.goyjo said:**
> What setup are you looking for? Do you want a dual boot, a triple boot? For a triple boot you will need to use refit (it's absolutely necessary). I'm not the man to ask, as I dual boot Ubuntu and Windows XP on my MacBook. But there are PLENTY of rEFIt Triple Boot tutorials on the web.

Also, please don't try to put ubuntu onto a fat32 partition. You want ext4 or reiserfs, but not fat32.

outcome is triple boot, migrating a way from OS X, but still have many apps for osx so will be triple-booting eventually.  considering couldnt' even boot off live cd...I was taking it one step at time and doing a double boot first. ;)


yeah, well how the hell do I get the option to format in ext4 or (ext3)?

---

### Post by danbishop on 2010-08-03
Hey,

Did you get Ubuntu to install? I can't get it to boot at all on an iMac 8,1... I just get a blinking cursor and nothing more.

Tried live 32 and 64bit as well as alternative 64bit. All have the same effect :(

---

### Post by Beth on 2010-08-03
Did you try to load older versions of Ubuntu? I've discovered they will easily load but then there's the problem of updating Firefox. The older versions will get you on the internet, however. 

Ubuntu, Fedora and Yellow Dog will all load on iMacs. I have one iMac that is used in software testing -- an older iMac 4. These iMacs are used by various schools which is why I include this one in the group of computers when I test software.

By the way, it's not just an issue with iMacs. It seems many computers are experiencing strange problems loading operating systems, even Windows. Viscious code is everywhere and it's massive in scope.

---

### Post by danbishop on 2010-08-04
Hi Beth,

I've not tried an older version no. I really need the latest version though. However, I will try an older version to day, then I'll try an upgrade and see if that works.

It's an iMac 8,1 I'm using which seems to be the worst one possible... I've seen successful reports on 7,1 9,1 and most below 7 as well, but no one has managed to get Lucid to work on 8,1 :(

---

### Post by danbishop on 2010-08-04
No luck :(

8.04, 8.10, 9.04, 9.10... none of them will even boot. Just get a blinking cursor...

---

### Post by danbishop on 2010-08-05
For anyone else stuck trying to boot Ubuntu on an iMac 8,1 DO NOT burn your Ubuntu disc using OS X.

I had used OS X's disk utility to burn all the ISOs and whilst they boot fine on other machines, they won't boot on the mac! I burnt a new copy of 10.04 using an Ubuntu machine and it booted perfectly!

---

### Post by alphonce on 2010-08-07
have you tried the alternative cd? thought i saw something that you could try that one if the desktop install cd doesnt work.

---

### Post by Regunirun on 2010-08-07
Hi guys.
I own an iMac (8,1), 24'' 2.8GHz C2D, 3GB of ram, 320GB HD

I have been triple booting Ubuntu/W7/10.6 for some time now (months). I would like to clear a few things up:

First: I do NOT use 64 bit OSs. The iMac simply will not benefit in any noticeable way from 64 bit. (The max ram is 4GB, anyway). And, naturally, 32 bit works perfectly, as does flash, for which support has been dropped ATM for 64bit linux.

Second: There's nothing wrong with using OS X, be that Leopard or Snow Leopard to burn the disks. I, too, have had the blinking cursor, but can't figure out why. Sometimes I got it, sometimes I didn't. I did however find that burning disks at the *slowest *possible speed in OS X helped greatly. The various versions I've tried and can confirm work (that is, they boot) are 8.04-10.04 (my current one).

Third: As for the right version, I can only say that I've tried each one as it was released. 8.04 worked pretty well, 9.04 had some problems with drivers for gfx, and 9.10 didn't work too well. However, Lucid worked flawlessly. Full 3D drivers + wifi out of the box, in the livecd. The proprietary fglrx ATI drivers, however, are a different story. They have, until quite recently had a significant bug which caused the whole system to freeze for 1-2 seconds during various compositing functions. Making a window go fullscreen, minimizing/maximizing, resizing, some Compiz stuff. The bug has since been fixed, but I still find the drivers to be worse than the free ones, because the Lucid bootsplash, Plymouth, does not support them correctly, and displays an ugly, distorted, mis-proportioned image, unlike the free drivers.

Fourth: Your apple remote will work out of the box, with LIRC. The mic I have not gotten to work, but the iSight works 100%, out of the box, (with Cheese that is). I, and several others with this model imac can not get the brightness to change. Don't ask why, but I don't mind, as the screen is perfectly bright out of the box in Lucid anyway. The last driver thing is about the speakers. I don't recall if they work out of the box in Lucid, but doing a mod to your modprobe and adding something like "snd-model-mbp3" or something works if not. However, to say they work is far from saying they work well. They sound like crap, period. No patch, no hack, no mod will ever get them to sound good in either windows or Linux. I called applecare twice about the issue, and they told me BS and that it was a driver issue (obviously). They are audible, but if you care about how your music sounds, especially bass, they are absolutely noticeably worse than in OS X. Adding a system-wide equalizer helps. The solution that I use is external speakers, which oddly enough, work flawlessly. As good if not better than OS X, in both Linux and Windows.

Fifth: As for bootloaders, I use rEFIt ([http://refit.sourceforge.net/](http://refit.sourceforge.net/)) and GRUB. Works fine. Just make sure to, when installing ubuntu, *not* install grub to OS X or Windows. rEFIt will take care of managing that for you.

I think that's it. I apologize if I wasn't coherent or specific. I'm 14 years old, and writing in a concise and logical flow is not one of my strong points.

Hope this helped!

---


---
title: "Can boot off CD to main menu and only memtest works."
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Sterkenburg on 2006-08-29
Firstly, I'll just say I had to burn the CD a few times to even get it to work.  I originally tried to burn the ISO as a bootable CD using Nero 7, but I read the FAQ (I think it was the 2nd last point that made me realize the iso is of a bootable CD and I'm just stupid) and so I tried burning it as a regular ISO, which, of course, failed.  To my unhappiness.  Nero was burning at its slowest possible speed/second slowest possible speed, 2.4x I think, and when it finished and started verifying it found zillions of errors.  So I gave up on Nero.

Using DVD Decrypter, a program I have never (up until this CD possibly) had a problem with, I tried burning the ISO (first accidentally I burned it to a DVD) at 1x, probably unnecessarily slow, and the slowest possible speed, but you never know.

Somewhere in that mess of a handfull of CDs on two burners with two programs, I got a CD that would boot (broken yet bootable cd number 1).  I could get to the main menu, but nothing would work.  Not the regular boot, not the safe graphics mode, not the CD check, and not the memtest.  I don't think I tried booting from the main HD, but that didn't seem to be what I was trying to do, ie: boot live linux.

So the last CD, the DVD Decrypter one (probably broken yet still bootable CD 2), gets me to the main menu fine.  I can get to the memtest, and I let it go for 11 minutes (until it started again?) before I rebooted (I ran it twice, the second time just to make sure it worked again).  When I select the first option on the main menu, the one that runs automatically after 30 seconds, the same thing happens that did with the first broken yet still bootable CD I made.  Once I select it the word "Loading" appears on the screen, and is soon underlined by a line of apparently random colours (this line spans accross the entire screen).  This bar seems to grow in thickness, and then after quite some time (6-15 mins?) another bar has appeared above it.

On the second probably broken yet bootable CD, the one made with DVD Decrypter, this same thing happens with the Safe Graphics Mode and the CD Check.  On the first broken yet bootable CD, this also happened when the memtest was selected.

All the stuff at the bottom of the main menu (F1-F6) seems to work fine.


I checked 12-15 threads about CDs not working, and none of them seem to say what I see.  I don't even know if this is posted in the right place, but I could see no better location.  Sorry if I'm just crazy.

Appreciative,
Rob Sterkenburg

Oh yeha, I downloaded the ISO from a torrent with uTorrent, and none of the pieces failed the data check so I would presume the file is fine.  I have ordered a CD from ShipIt too, just because that would rule out burning errors, but, of course, that'll be 6-10 weeks.

---

### Post by PPAAUULL on 2006-08-29
Did you do a check sum?

Paul

---

### Post by Sterkenburg on 2006-08-29
A ... who what?

---

### Post by bodhi.zazen on 2006-08-29
> **Sterkenburg said:**
> A ... who what?

A md5sum checks the integrity of your iso.

see:
[http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html)

I like this one the best:
[http://downloads.activestate.com/contrib/md5sum/Windows/md5sum.exe](http://downloads.activestate.com/contrib/md5sum/Windows/md5sum.exe)

---

### Post by Sterkenburg on 2006-08-29
Well...  What is the md5sum of the ISO supposed to be?

...Or does this program compare the ISO and the CD, not the ISO and what the ISO is supposed to be?

I'm guessing its the first one.

---

### Post by xpod on 2006-08-29
Your not going to like this but mabey "burning" the alternate cd might be better....
Our kubunto pc did the exact same thing (i could only run memtests) when i first tried to install ubunto on it (and stangely xubunto)

I ended up being able to install the kubunto alternare version ok which uses a text based installer with more options.

Of course this was an older machine and might not be relevant in your case?

As far as "simple" burning is concerned i found "cd burner xppro 3" really simple for a pc newb....

---

### Post by bodhi.zazen on 2006-08-29
> **Sterkenburg said:**
> Well...  What is the md5sum of the ISO supposed to be?

...Or does this program compare the ISO and the CD, not the ISO and what the ISO is supposed to be?

I'm guessing its the first one.

You generally get the md5sum from where you download the iso.

See here:
[http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/](http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/)

At the bottom of the page is a file "MD5SUMS" which links to here:
[http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/MD5SUMS](http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/MD5SUMS)

---

### Post by Sterkenburg on 2006-08-29
Thank you...  now I know what I need and how it works and all that.

(fb3af44c21f1f68cc25fda7edb8c1bd3)

So how does 'md5sum.exe' that you suggested work?  Not what it does, I understand that, but how do I get the exe to spit out the check sum of my downloaded iso?

Also, thankey kindly to all three of ya.

---

### Post by bodhi.zazen on 2006-08-29
The program you downloaded is command line only from windows (sorry, my mistake)

Try this site for a GUI:

[http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum)

---

### Post by Sterkenburg on 2006-08-30
All fixed, everything works!  Is uhh what I'd call "znake" multiplayer?  I saw 4 players accross the bottom.


Alsooo, you guys/girls should add 'doing a checksum' to the FAQ.  I'll write you guys a tutorial for $1.00 :smile: 


--Sterk out.

---

### Post by bodhi.zazen on 2006-08-30
> **Sterkenburg said:**
> e2e5e0bfb2edffd2ce02dd77bda4558e

And unless I'm crazy, none of the currently available ones start or end with E.

You may or may not be crazy. If this is a MD5sum from your iso you need to re-download and re-check md5sum. If md5sum checks out -> burn & boot.

---

### Post by Sterkenburg on 2006-08-31
Okay, so now I've downloaded the file directly from you guys, no torrents involved (though it took me three tries because firefox would inexplicably stop, and pausing and resuming would put me at a whole 000.00%) and the checksums match up.  Though I downloaded the regular i386 desktop version, I'm gonna try that before I go advanced.

Now all I have to do is find a blank CD that isn't 650 MB.  Apparently I have a zillion DVDs, and not one decent CD. :)

Will report back.

---


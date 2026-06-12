---
title: "Is there a way to just install GRUB?"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by OOnbuntOO on 2007-07-30
So.. I am having a nerf of a time getting Ubuntu 7.04 (from a purchased dvd) on my Sony Vaio PCG-FXA53.  Not sure off-hand what proc speed the Vaio is, but I know it's AMD Atholon XP, and I upgraded the ram to 512 MB.

I"m led to believe the DVD/CD ROM on my Laptop  is a bit flaky - after numerous hangs in both the GUI installer and the Text-only installer, it sometimes resumes if I eject and reload the DVD.  Even so, I know the DVD rom works and the laptop works - I've had XP, Windows 2000 (recently) and even Ubutu 6.something run on it and install fine in the past.  The DVD I am trying to install from has passed the built-in CD ROM integrity test twice.

Just this last time I really thought I had it - surprisingly in the GUI install it got to 94%!!!
I almost cried when it crashed and I got a message (which I can post here if it will help).  It said it was setting up GRUB boot loader. I tried to boot it anyway...sure enough, when I try and boot I get this error

GRUB Loading stage 1.5

GRUB loading, please wait ...

Error 15

Now I am afraid to try and resintall because this is the farthest I have gotten so far... I am wondering if there is some way that I can JUST INSTALL THE GRUB part and thereby finish the installation?

I am really a Linux Newb... but would consider myself a Windows power user.  I am able to follow instructions and often can figure things out from documentation, if I know where to look.  But this is unknown territory for me...

I did find the ALT-CTRL-F1, F2, F3 and F4 console... but I don't know what to do with the commands or really where to start, of if they will help me at all.

Can someone help me get my GRUB loaded - or do I really have to try and install the whole thing again? (Doubtful that I will get this far again - I have been trying for 4 days and it usually flakes out when partitioniong...) :cry:

---

### Post by aitorcalero on 2007-07-30
Check out this site:

[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

Here you can download an ISO, burn it, and try to restore your grub, or in case you need it, repair it, or just lauch you Linux partion.

Hope this helps ;)

---

### Post by dfreer on 2007-07-30
If you don't feel like burning another CD, you can use the Ubuntu Live CD and use it to fix GRUB (pretty much any linux Live CD will work).
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
this should help you out!

---

### Post by OOnbuntOO on 2007-07-30
Thanks for the suggestions so quickly -  I will try this out when I get home!

The Ubuntu is going to run my Neverwinter Nights persistent world ([http://www.gnostica.info](http://www.gnostica.info)) so hopefully I can get this going and get the game on :)

---

### Post by NewbieNik on 2007-07-30
Ive had this error before and it&#347; because Grub is not recognising the boot partition. When installing try resizing your drives and set aside a 500Mb partition specifically for /boot. I experienced this on a RAID system though, but I think it should still apply

---

### Post by OOnbuntOO on 2007-08-03
Well I gave up on the laptop.... that dvd drive doesn't like ubuntu at all.  Couldn't get the LIVE ubuntu up long enough to type those GRUB restore commands... BUT I  managed to get an old HP desktop to install it on.  So far so good...

---

### Post by khughitt on 2007-08-03
I've had similar problems with the installer freezing up several years back, but that was due to a quirky graphics card. If you are still having trouble down the road, another option would be to consider installing a test version of 7.10 .. In general, you don't want to run early releases if unless you are testing / developing, but if it's just for a home machine, and nothing else works, it might help.

---


---
title: "Hardy Heron Alpha 4 up on G5 iMac"
date: 2008-02-06
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-06
Well, I was browsing the cdimage repository and found the daily live builds for Hardy Heron for PPC!

Probably best to choose the latest:

[http://cdimage.ubuntu.com/ports/daily-live/](http://cdimage.ubuntu.com/ports/daily-live/)

It has been reported that some may find that their cd rom won't be detected just after the start of the install, and that was the case for me, but I found a workaround in case you want to try it out and this happens to you.

I had to use an external firewire cd-rom drive, but here's the kicker:  I couldn't get any cd or dvd burns of the Hardy alpha install to boot from the firewire cd rom.  It would boot an apple dvd of course, but not Hardy.  Hrmmm....

Solution:  Burn TWO copies of the live-cd install.  Boot from the internal cd, and when it eventually fails, it automatically finishes up from the external firewire cd!  yeah baby!

Ok, it's still Alpha but the screaming loud fans are back!!  Got to dig out my notes when stmiller saved my sanity back in the Edgy days, but too tired to fix it tonight.

The 20" G5 iMacs screen has that same annoying 1/2-inch shift and wraparound from the right to the left as Gutsy did.  Man, I hope there's a solution for that.  I think the smaller-screen iMacs don't have this problem.

Otherwise, it looks ok so far.  But man, those fans again..... "its just an alpha, its just an alpha, its just an alpha"  **But it is also LTS!!**

**** UPDATE**** Bugs filed for the screaming fans.  Tried the windfarm fixes from the past, but they failed.  Also filed bug report on the non-centered screen, even though resolution is correctly detected.

---

### Post by VCF on 2008-02-07
Great news!
Just a quck question for you though?  Did it find your IDE disk controller OK? (that may be why you had to continue the boot from the firewire cd drive) 

I was trying to install the livecd on my iMac 500/G3 and the modprobe ide-core didn't work for me like it did in Gutsy.  Just back to busybox.
 
I did the alternate install CD after taking the CD over to the connected firewire (lucky my machine has the case off and I could eject it with a paperclip) and found that it cannot detect a disk controller and gave me a list of controllers ide-core was one of them but it didn't work.

Did you have to manually select a disk controller?

Do you have a console command to tell me what kind of IDE  controller driver I've got (in Gutsy where I can at least get to console, but not Gnome)

---

### Post by BladeMelbourne on 2008-02-07
When I attempted to run the Hardy live CD, I did get the busybox prompt. The modprobe ide-core followed by exit instructions didn't work. I didn't need to do this with Gutsy (G4 mini).

I also attempted to install the Hardy kernel in Gutsy, however upon boot it seemed to stop just after the line "ethX link is up at 100mbps" - it's like the root partition is never mounted.

It will sit there forever. Ctrl Alt Delete will respond correctly and restart the system.

Not sure if it's related to your issue. /etc/fstab has UUIDs in it, so it shouldn't matter much if /dev/hda4 has become /dev/sda4 due to some new driver.

---

### Post by stream303 on 2008-02-07
> **VCF said:**
> Did it find your IDE disk controller OK? (that may be why you had to continue the boot from the firewire cd drive)

No problem there.  The notes for Hardy say that some CD drives aren't being detected (like my iMacs) once Ubuntu takes over.  Boot initially goes fine, but then fails detecting the cdrom, hence the need to have an external drive with another copy of the install cd, since it detects a firewire cdrom just fine. :)

After the install, the only way to eject the install cd was to boot from the OSX install disk, and eject the disk since the internal cd drive didn't exist to hardy anymore. :)

I didn't have to manually select a controller, so the HD was detected with no problem.

Have you tried resetting your pram / nvram?  Supposedly cures all ills from hair-loss to booting issues. :)  I like to do this at least once just to assure I'm starting with a clean slate with Ubuntu:

[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

(don't confuse CTRL key with the Command key [cloverleaf] icon.)

Hang in there.  Once you get it running, you won't believe how good you'll feel!

---

### Post by kugn on 2008-02-09
The bug you're experiencing is probably this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/183338](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/183338)

which seems to have been fixed now :)

---

### Post by stream303 on 2008-02-09
Allright!  Time to burn a new image, or manually install the latest kernel and see what's up!  Thanks for the heads up... off to try it now...

---

### Post by ssam on 2008-02-09
> **kugn said:**
> The bug you're experiencing is probably this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/183338](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/183338)

which seems to have been fixed now :)

but as far as i can tell the fixed kernel has not made it to the live cd yet ;-(

---

### Post by stream303 on 2008-02-09
Noticed that too.  It did do an automatic upgrade to the latest kernel, but it still does not detect my G5 iMac's internal cd/dvd drive.  And as of now, I suspect that they aren't compiling for G5 as I still have screaming fans without any thermal support.  Makes it hard to enjoy the Alpha for more than a few minutes at a time. :(

At the very least though, it looks like we'll have a Hardy-Heron release, and if worse comes to worse, we can compile our own kernels with G5 thermal support  - I think.

---

### Post by VCF on 2008-02-10
> **stream303 said:**
> Noticed that too.  It did do an automatic upgrade to the latest kernel, but it still does not detect my G5 iMac's internal cd/dvd drive.  And as of now, I suspect that they aren't compiling for G5 as I still have screaming fans without any thermal support.  Makes it hard to enjoy the Alpha for more than a few minutes at a time. :(

At the very least though, it looks like we'll have a Hardy-Heron release, and if worse comes to worse, we can compile our own kernels with G5 thermal support  - I think.

Try the the alternate install CD.  It is now recognizing my IDE controller (and thus CD) BUT the installer is compiled with a different kernal so it cannot proceed past H/W detection and language/keyboard prompts which looks good as it scrolls past, (how do I get to see it again at a busybox prompt?).  I reported the bug and hopefully it will be fixed soon.

---

### Post by stream303 on 2008-02-11
Yep - the alternate installer is the only thing I use these days.  I think I'm going to take a break from Hardy Alpha for awhile because if they don't compile in thermal control for G5's, the vacuum-cleaner fans are just too hard to live with - even if the exhaust isn't hot.

---

### Post by stream303 on 2008-02-12
I guess this was my last shot at sanity in regards to the screaming exhaust fans.

I tried compiling a custom kernel under Hardy Alpha 4 with g5_defconfig support and all goes well until therm_p72 just errors out the whole compile.

Since this came from the generic kernel sources, maybe I can't blame Ubuntu.  Arrgghhh

---


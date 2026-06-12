---
title: "trying to boot Ub 7.04 Live CD -- G3"
date: 2007-09-18
forum: Apple PPC Users
---

### Post by Average_Joe on 2007-09-18
Hello --

I am trying to boot the Ubuntu 7.04 Live CD for ppc.  I also tried below with the Alternate Install CD for ppc (7.04)

This is on an iMac PPC G3 500 MHz.   The Open Firmware console reveals "Apple PowerMac2,2 3.0f3 BootRAM from 06/13/00"

I burned the image on speed 1x with verify, and have burned a few dozen ISOs successfully on the CD device before.

I get into Open Firmware and I have tried the list of commands below.
The CD spins and it tries to do {something} after each command,
but then it returns this:
   bad READ-1   can't OPEN : cd {...followed by directory path requested}

Here are the commands I have tried.  Please note that I do not know whether my CD drive is IDE1 ... I just tried that command hoping it would help.

[HTML]O> dir cd:,\ 
O> dir cd:,\ install
O> dir cd:,\ install\yaboot
O> dir ide1:,\
O> boot ide1:,\ install\yaboot[/HTML]

If anyone can help it is greatly appreciated!!

---

### Post by rjt1000 on 2007-09-19
Hi,

I had a similar problem with being unable to boot from Feisty live or alternate CD's with my G3 500 Pismo, and got a similar error message. I am pretty sure that the problem was the replacement combo drive I have is wired as slave not master.

I used [this]("http://ubuntuforums.org/showpost.php?p=2887410&postcount=4") work-around to boot from my hard drive and install from an alternate install .iso image on the hard drive.

Good luck,

rjt1000

---

### Post by bodycoach2 on 2007-09-19
I've never been able to get a LiveCD to boot on a G3 under 600 MHz. It probably has more to do with memory than the processor. I have been able to get the Alternate Install CD to work on almost every machine. If I can't get 7.04 to install on a G3, 6.06.1 always does, then I can upgrade from there.

---

### Post by Average_Joe on 2007-09-19
Thanks to you both for the replies.

I wasn't able to get the Live 7.04 nor the Alternate Install 7.04 to boot on the ppc 500 Mhz G3, so I ...

... went out and bought an older G3 for $30 to experiment.  (The first machine in question -- a ppc 500 MHz machine with 640 MB of RAM and OS X, is actually owned by someone else.  I didn't want to screw with it too far without some experimenting on a second machine.)

So, this second machine, is a G3 ppc 233 MHz with only 32 MB RAM and runs OS 9.0.x.  I was stuck in the same unable-to-boot-from-CD situation with it, too.  It is a tray-loading CD.

This machine had the latest Open Firmware update available for it (from year 1999)
so what I did was go to Apple's support site and found a CD (optical) firmware update for this particular machine.  After installing this optical firmware, I am now able to get this second machine to
start loading Ubuntu with a boot from the CD.

I should mention that with only 32 MB of RAM, the loading of the Linux OS fails (for now) at the point of creating the virtual disk.  This is very likely because there isn't enough RAM, so I am going to up the RAM tonight to 128 MB.  I think I will be successful after that, at least with the Alternate Install of Xubuntu 7.04.  

I'll let you know.

Thanks again.

---


---
title: "Can't install 6.10 desktop or server on G4 400mhz"
date: 2006-11-08
forum: Apple PPC Users
---

### Post by stickmangumby on 2006-11-08
I'm trying to install Ubuntu 6.10 on an old G4 400MHz 768MB RAM computer I've  been given. I'm not sure how the hardware is going, or if there's anything wrong with it, but I simply cannot install Ubuntu.

I downloaded and burned Ubuntu 6.10 PowerPC Server, and tried to install that. When I boot using any of the images, it will let me select the language and keyboard, then when it gets to "Detecting Hardware to find CD-ROM drives" it hangs at 0% for about 5 minutes, moves to "Loading module 'via82cxxx' for 'IDE chipset support'", which is 9%, and it hangs there indefinitely (well, at least for 20+ minutes).

I figured I'd give the desktop edition a try, and that didn't work either. The live image boots to the desktop but the keyboard and mouse don't work at all... they don't respond or seem to have power; the LED under the mouse if off and the caps and num lock keys don't light up when you press them. It takes about 10 minutes to get to the desktop, and in the process it has the following error:

udevd-event[1543]: run_program: '/sbin/modprobe' abnormal exit

Eventually it keeps going and reaches the desktop but I can't do anything.

I tried installing it again using the monitor that came with the G4 (rather than my ViewSonic which has a standard VGA input) and after choosing an image at the boot prompt it went black.

There may well be hardware problems, but I wouldn't have thought the server edition would hang looking for CD-ROM drives given that it's running off the CD-ROM drive, and it seems like the desktop edition has a different problem.

Can anyone shed some light on my grief? If not, it may be </G4>

Thanks for the help in advance :)

---


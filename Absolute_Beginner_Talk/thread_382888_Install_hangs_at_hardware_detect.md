---
title: "Install hangs at hardware detect"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by parthamage on 2007-03-12
I am a complete newbie to linux.  Trying to install ubuntu on a box I built myself.  Have run windows for a couple of years on it.  Has a Shuttle AK39N mb, Athlon1700+ CPU, 1.5 gb of RAM, RADEON 7000 64MB DDR 4XAGP video card, CREATIVE LABS 12X DVD/40X CDROM INT.#DVD1241, AOPEN 48X-RC/12X-RW/50X-RD CDRW, using a dell lcd tv as monitor.  I have downloaded both versions of ubuntu 6.06 and 6.10.  I have checked the images.  I have probably created 6 CDs, and none of them work.  I get past the keyboard verification, and when the installer starts to detect the rest of the hardware, it just dies.  I get a blue screen with a silver bar at the bottom, and that's it.  I really want to get this thing to work.  Any advice?

---

### Post by scrooge_74 on 2007-03-12
When you get to the menu try using the safe mode version or try the options at the bottom

---

### Post by parthamage on 2007-03-13
Where is "Safe Mode"?  I found "Rescue Mode", and tried that.  Only difference is it now says,"Rescue Mode" in the blue screen where it hangs during hardware detect.  
Also, what options are you referring to?  I have looked through the helps, and tried a couple of the things that seem obvious, but nothing changes my results.

---

### Post by scrooge_74 on 2007-03-14
press F2 when the option menu comes at boot and try different options,if not maybe the alternate CD will work for you

---

### Post by parthamage on 2007-03-15
On both of my versions, F2 is the language menu.  I really need English.
I was already using the alternate disc, so I went back to the desktop and used the Safe-graphics mode.  When I do that, it goes to a series of error messages:
[17179767.556000] Buffer I/O error on device hdc, logical block 0
[17179772.560000] hdc: drive not ready for command
[17179892.664000] Buffer I/O error on device hdc, logical block 1
[17179897.668000] hdc: drive not ready for command
etc. etc., etc.
now what?

---

### Post by dstew on 2007-03-15
What distribution CD are you using? Is it the i386? 32 or 64 bit?

What is happening is that the Live CD is not configured properly for your system. It could be the Live CD's fault (they didn't anticipate a system with your hardware), a bad CD burn (probably not), or using the wrong CD for your system. Try the Live CD in another computer (with a different system from yours). If it works, the CD is probably OK. It looks like your third hard drive is causing the problem (hdc in linux-speak). If hdc is your DVD drive, and you aren't using it, you can unplug it and see if the disk works. At least that would tell you where your incompatibility is. You can try adding various kernel boot options (press F6). However, which options to add would depend on what the hardware issue is.

---

### Post by parthamage on 2007-03-15
I am using the i386,  (32 bit) and have attempted both the desktop and alternate install versions.  I broke down and ordered the DVD version from Amazon; will that have a better shot at installing?  Should I just wait for it to come in?  If I do unplug my dvd, and it works, am I setting myself up for failure later when I want to plug it back in?

---

### Post by desyressylence on 2007-03-15
The disc that you are using to burn the livecd, does it happen to be a CD-RW disc?  I was randomally searching google and it appears that other debian / gentoo users have experienced issues reading from discs while booting when utilizing this type of media.

[http://forums.remote-exploit.org/archive/index.php/t-1942.html](http://forums.remote-exploit.org/archive/index.php/t-1942.html)

If so, try a plain CDR disc without rewrite capability, it may help.

As others have stated, try disabling your dvd drive if you are not using it.  At least it will help you narrow down your problem.

---

### Post by parthamage on 2007-03-15
Am using CD-R discs at the moment.

---

### Post by dstew on 2007-03-15
You are only setting yourself up for failure later if you install Ubuntu with the DVD-ROM unplugged. It was just my thought that, if you took it out, and the Live CD ran, then you have a good idea of what boot options might help you get it working with the drive in place.

---

### Post by parthamage on 2007-03-18
Well, dstew, you had a good point.  Unplugged my DVD, got the same error.  Plugged it in, and unplugged the CDRW, ran Live CD from the DVD.  Started getting different errors, and as I was copying them down, it managed to boot.  I was so tickled, that I installed it.  Now, of course, my CDRW doesn't work.  System sees the drive, but if I put a cd in, it starts spinning like mad, and I have to shut down to get it out.  On an unrelated note, the video coming from my digital video is weird; it is too big to display on the screen, no matter what resolution I use, I always lose the right hand side of the screen.  Can live with it in most applications, and by not expanding the toolbars, but NeverWinter Nights (main reason I loaded Linux on that box) is a full screen app, and I lose the right hand side of the game, which renders it unusable.  I can get by with my RGB cable, but would like to use the digital, as the picture quality is better.  Any help on either issue greatly appreciated.  Or do I need to start new threads?  And thanks for the help so far.  I am really enjoying Ubuntu.

---


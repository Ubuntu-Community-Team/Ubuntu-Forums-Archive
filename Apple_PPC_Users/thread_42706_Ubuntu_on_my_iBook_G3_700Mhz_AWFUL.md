---
title: "Ubuntu on my iBook G3 700Mhz AWFUL"
date: 2005-06-19
forum: Apple PPC Users
---

### Post by Rinnan on 2005-06-19
So far my experiment to install Hoary Ubuntu 5.04 + Beagle instead of Tiger has been a total failure.  I installed Ubuntu PPC on my (HD completely blanked) factory standard iBook G3 700 (except for a little added RAM for a total of 384MB).

I chose all standard options for install, which completed without any apparent problems.  And at first, things looked great.  My airport card worked out of the box, perfectly.  I was very impressed.  Furthermore, 3D acceleration also worked.  Very nice.

But the screen wouldn't go higher than 640x480.  I fixed that by explicitly setting the horizonal and vertical refresh rates for the LCD display in the xorg.conf.  This twiddling is exactly what I try to avoid by using a distro, rather than, say, LFS.

Three other problems, very serious, have caused me to give up and buy Tiger, but I left half the HD (10GB) ready for Ubuntu when I figure this stuff out.  The problems are with writing a CD, with sound, and waking from sleep.

With sound, I get a very muffled, distored sound.  Twiddling the settings in alsamixer does not improve things, nor does changing the gstreamer sink.  Very frustrating.  And when I write a CD (with "Write to disc..." on the context menu of right-clicking a CD .iso image), it invariably writes about 2% of it, fixates it, and finishes, seeming to succeed but of course in actuality ruining the disk!

Waking from sleep is the most frustrating.  My iBook will sleep, but not wake.  I've already tried every idea I found in Ubuntu Forums to fix this, but killing hald or changing the hal scripts does not change anything.

Anyone have ideas to fix this stuff?  Why doesn't this work out of the box, since the iBook is a standard collection of hardware and very common?  Wouldn't this stuff be known and well understood?  Yet there's a lot that resists fixing.

Erik

---

### Post by Len on 2005-06-21
The sound problem is known, ALSA doesn't support some of the newer sound chips on the Mac, resulting in garbled sound (here too) or no sound at all. This is a problem you'll encounter on any linux distribution. With a little luck a kernel update will fix this in the future (so use that 10 GB to try out future versions :).

I don't have an iBook, but for power management you should look at ACPI. Here are some links that might help you:
[http://www.acpi.info/](http://www.acpi.info/)
[http://www.thinkwiki.org/wiki/How_to_configure_acpid](http://www.thinkwiki.org/wiki/How_to_configure_acpid)
although I never have looked into power management since it worked fine when I had it, so I have no idea whether the info applies to Ubuntu.

The CD problem is rather weird. You'd say it would write or not work at all, not only does half the job. Did you try an application where you can change the driver/settings for your CD writer?

Linux always needs some terminal work, I never experienced otherwise. The site of[Terra Soft (YellowDog Linux)](http://www.yellowdoglinux.com/) features a full compatibility list. The hardware supported/unsupported by YellowDog Linux mostly applies to other distros as well.

---

### Post by wmarco on 2005-07-20
Xorg may be having problems determining your mode lines for higher resolutions, so you may have to specify them directly in your xorg.conf. To find the proper mode lines check out [http://ubuntuforums.org/showthread.php?t=27546&page=2&pp=10](http://ubuntuforums.org/showthread.php?t=27546&page=2&pp=10). The key differences would be that instead of running :

./parse-edid /proc/device-tree/pci/NVDA,Parent/NVDA,Display-A@0/EDID

you would have to find where your video card keeps it's own EDID file so do a search:

find /proc -name EDID -print 2> /dev/null

Then if you have an EDID file run:

 ./parse-edid where_your_EDID_file_is


best of luck,
Warren Marco 
 ](*,)

---

### Post by gruepig on 2005-07-20
Regarding wake from sleep:  I think I have the same model iBook.  My solution(running Warty) was to create the dbus-1 script as described at [http://ubuntuforums.org/archive/index.php/t-2368.html](http://ubuntuforums.org/archive/index.php/t-2368.html).  When I upgraded to Hoary, that broke.  I downgraded from the Ubuntu 2.6.10 kernel to the 2.6.8 kernel, and all is well.

---

### Post by Rinnan on 2005-07-30
I would like to update the title of this thread to "Ubuntu on my iBook G3 700Mhz -- Much Improved"

I went back to using Mac OS X on the laptop because of my many problems with it.  The main one, as before, was that I couldn't for the life of me get it to sleep.

Since then, my main development machine (also an Ubuntu box) died a horrible death.  I was forced to get my iBook to use Ubuntu, (or at least, some kind of Linux) as all my work for my business was in a Linux format.

So I tried again.  Much to my happy surpise, on this install, everything except sleep worked perfectly.  The screen changed to the right resolution, sound worked out-of-the-box, and so on.  

Even the sleep situation had changed.  My iBook still couldn't wake up.  But this time, the behavior changed.  Before I'd just get a black screen, now I got a bunch of text telling me each stage of its wake up process, but no X.

I tried the scripts mentioned above again.  Last time they didn't work, this time they worked perfectly!

Now I only need to get the external display to work (no dice yet).  But it's totally fine as a laptop.  As for the external display, it didn't work anyway on Mac OS X so I'm not competing against anything.

On Mac OS X, on an iBook, unless you hack around, it will just clone the 1024x768 screen on the external display.  But I wanted 1280x1024 on the external, plus 1024x768 on the built-in display, dual head.

I've seen it work, I know it's possible, but no amount of xorg.conf fiddling (or downloading of other people's xorg.conf's) has worked yet.  Any ideas guys?

Erik

---

### Post by harryc on 2005-07-31
[QUOTE=Rinnan]...I've seen it work, I know it's possible, but no amount of xorg.conf fiddling (or downloading of other people's xorg.conf's) has worked yet.  Any ideas guys?

Erik[/QUOTE]There is an OS X screen spanning hack that gets you what you need with dual screen. I use it on an ibook G4 and it works great. You'd have to look around for something similar for Linux, I am having my doubts it exists though.

[http://www.rutemoeller.com/mp/ibook/ibook_e.html](http://www.rutemoeller.com/mp/ibook/ibook_e.html)

---

### Post by Abhi Beckert on 2005-08-02
[QUOTE=harryc]There is an OS X screen spanning hack that gets you what you need with dual screen. I use it on an ibook G4 and it works great. You'd have to look around for something similar for Linux, I am having my doubts it exists though.

[http://www.rutemoeller.com/mp/ibook/ibook_e.html](http://www.rutemoeller.com/mp/ibook/ibook_e.html)[/QUOTE]
 I thought the screen spanning hack was a firmware hack? I'm sure the read me stated that if you wipe your HD and re-install you won't need to re-apply the hack.

Doesn't this mean it should apply to all installed OS's?

---

### Post by Rinnan on 2005-08-02
It is kind of a "firmware hack", but only in the sense that the Apple OS keeps some of it's settings in CMOS.  It's really kind of a "registry hack", if anything.  Since Linux does not store any data in the CMOS, it does not make use of any settings there.

At this point I'd be satisfied with an xorg.conf that make my iBook use it's external monitor at 1280x1024, even if it shut off its built-in monitor.  I don't need two, I just need the external monitor at its fullest.  Any ideas how to do that?

Rinnan

---

### Post by harryc on 2005-08-03
TTBOMK, all iBooks only mirror their max display resolution on external monitors, without the hack that is. For example, without the hack, my ibook will only display 1024x768 max. As was stated, this is a firmware limitation. Apple decided not to include higher resolutions in the firmware(the options are there but deactivated). Anything you do in xorg is not going to change that.

---

### Post by Rinnan on 2005-10-20
I doubt this -- I just don't see how it's possible to limit it in the firmware -- the X drivers are talking directly to the hardware, the firmware doesn't enter in to it at that stage.  Even if you are right, the same firmware modification that makes it work for Mac OS X ought to make it work for Linux.  I suspect that that firmware modification is nothing but changing the value of a variable read by Mac OS X telling it not to allow or not allow spanning.

In other news, all the issues with my ibook, including some issues I didn't mention (like the trackpad not tap-clicking without playing with powerprefs) are fixed, but not including the spanning-display thing.  Maybe I'll work on that again for fun :razz:

---


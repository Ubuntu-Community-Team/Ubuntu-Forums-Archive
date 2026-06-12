---
title: "After 1st splashscreen, no signal to DVI LCD"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by sketchstudios on 2007-02-08
Hey all,

This is my first time trying out ubuntu and was really excited to start using it, expect I ran into a problem already. :(

I have just downloaded the Ubuntu 6.10 DVD image for PC (intel) and burned it successfully to a DVD. I popped that sucker into my computer and was smiling as I got to the boot menu which, when I selected the first option "Install or Run Live CD/DVD" it started up with the ubuntu logo and a progress bar going back and forth.

So far so good, except after that splash screen goes away, my whole monitor blacks out, and "no signal input" is shown. :(

I also tried booting the DVD into "safe graphics mode" but, same thing happens. Actually, not quite, after the splash screen, the monitor still goes black, but there is no "no signal input" displayed. weird.

so any help, whatsoever is REALLY appriciated, I really want to get going with ubuntu..

Here are the specs of my PC:
Sony Viao 1.8Ghz, PIII, 
1gb ram
ATI All-In-Wonder Radeon 8500DV 64mb video card
Windows XP SP2 installed (if that matters)

my monitor:
Princeton 21'' LCD hooked up via a DVI wire.

thanks in advance for any help :)

---

### Post by Sunflower1970 on 2007-02-08
Do you have an analog hookup you could plug in while trying to figure it out? I have one computer I cannot use the DVI on one of my computers due to the age of it (I'm guessing. No matter how much fiddling, I've been able to get the DVI to work on it.)

---

### Post by sketchstudios on 2007-02-08
I do not have an VGA hookup, the only output my PC has is the ATI's video card DVI output, which is what I use. I have tried running the "check dvd/cd for errors" as well, and there were 0 errors, so I know that works fine. I looked around online a little more and the only thing I can think of is that the drivers are not on the dvd for my particular ATI  All-In-Wonder Radeon 8500DV, so I found this site:

[http://ati.amd.com/support/drivers/linux/linux-firegl-prer200.html](http://ati.amd.com/support/drivers/linux/linux-firegl-prer200.html)

which is ATI's site for the linux drivers for the video card I own, but I would have no clue how to install this driver, since I cant even get into ubuntu. 

I also found this site:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

but Im not quite sure where to read on that page that would help me with my particular problem. 

I also found another thread:
[http://ubuntuforums.org/showthread.php?t=262092&highlight=ati+8500](http://ubuntuforums.org/showthread.php?t=262092&highlight=ati+8500)

but im not sure if it relates to my problem since they are talking about TV output, and not monitors. 

*ack* any help is totally appricated, thanks :)

---

### Post by RoaringOasis on 2007-02-09
I have a similar problem w/ the init splash screen when booting an installed and  functional version of edgy... and if I remember correctly, I ran into the problem with the Live CD as well. 

I'm running a Hanns-G 19" WXGA LCD off an ATI X1300, the LCD has a native/max res of 1440x900 and is really sensitive to resolutions outside it's range. Unfortunately, when the graphics drivers do an autodetect for supported resolution/refresh settings, it reports back values outside the actual range (1920x1080), and apparently it takes the highest values for the init splash screen, which causes my screen to black out until it hits the log-in screen, at which point it drops down to something displayable, but still rather large for the screen (with the text box ending up towards the lower right part of the screen, rather than centered). Once I log in, its fine (I have the res set to 1440x900, but I have to set it for each user/profile I create, the first time I log in). 

This should rather easily be fixed by manually entering the res, refresh, and depth info in the xorg.conf file, I just havent had the time to screw around with it recently... and the only time it really bothers me is when fsck decides to run (something like every 30 mounts), and I'm left wondering why the heck the computer is taking forever to boot. I'm not entirely sure how it would be resolved for a live CD though -- I think you can manually choose the resolution at the boot menu of the Live CD (look down towards the bottom -- it should be one of the function keys that brings up the menu) -- choose something nice and safe, like 1024x768@60Hz. If you're looking to do an install, you should be able to get around it by using the text-based installer on the Alternative Install CD, rather than the GUI install on the Desktop Install CD, and then simply changing the xorg.conf file after install.

Rock on. :guitar: 

-RO

---

### Post by gnyoda on 2007-02-12
Install alternate cd from the ubuntu web site.  That will allow you to boot into a text based installer. Let me know if that works for you. From there I'm almost positive you will have to configure a few more settings in order to get the distro up and running.

---

### Post by cieje on 2007-02-13
I had the exact same problem with my ati card. I installed with the alternate cd and still faced problems. But once I could boot into recovery mode to access the console I was able to do this:

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

and after, to configure:

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

then you want to restart.

However, even after that I still don't have direct rendering working... and it's saying it's using Mesa... but at least the 2d looks and runs fine.

---

### Post by riggits on 2007-02-15
It looks like the installer chokes on any DVI graphics cards.  I've tried Ubuntu 6.10, Kubuntu 6.10, in the i386 and AMD64 versions.  All four install CDs checked out perfect.  All four died with rubbish characters on a "blue screen of death" and a rather phony offer to let me view Xorg's display detection log.  The log never appeared so I have no idea what's going on.
Safe graphics mode installation is the one that gave me the bogus log offer, the regular install just blanks my display & the monitor says "unsupported video mode" and that's it.
Graphics card is a ATi Radeon x600SE with DVI output only.

Maybe the graphics driver on all these install CDs is hosed?  I've seen a bunch of threads on this same issue with DVI graphics.

---


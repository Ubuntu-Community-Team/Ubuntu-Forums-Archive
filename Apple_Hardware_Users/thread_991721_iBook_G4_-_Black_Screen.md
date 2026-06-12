---
title: "iBook G4 - Black Screen"
date: 2008-11-24
forum: Apple Hardware Users
---

### Post by pmhauge on 2008-11-24
So I have an iBook G4 (1Ghz or so. It has a dead HD in it, which I plan on replacing myself soon. Once it is up and running, I plan on making it a strictly Ubuntu machine. I've downloaded and burnt the live CD for PPC machine, but when I try to boot from it, I get past the screen where it says that my display has been found, or whatever, and then I get a black screen... nothing else. I have to power off the machine to get anywhere. I know the dead HD isn't the problem, naturally, because I'm booting off of the live CD. Just to be sure my wife has an identical iBook and the exact same thing happens. What am I missing here? I've set my intel Mac Mini to dual boot using the Intel build with little issue, but the PPC is giving me nothing but trouble. 

Any and all help/advice is most welcome. 

Oh yeah... This is my first post here, I think. (insert obligatory introduction message here)

---

### Post by stream303 on 2008-11-24
Welcome aboard!  Hopefully you'll be able to add another Ubuntu install to the pack.

> **pmhauge said:**
> So I have an iBook G4 (1Ghz or so. It has a dead HD in it, which I plan on replacing myself soon.

Because ppc hardware can be pretty finicky, be sure to identify your exact model just to make sure of it's capabilities, so you can get help faster:

[http://www.everymac.com/systems/apple/ibook/index-ibook.html](http://www.everymac.com/systems/apple/ibook/index-ibook.html)

It isn't uncommon to boot to a black screen without passing any kernel parameters.  It has been awhile since I've used the live-cd, but if you can see the second-stage boot: prompt, hit TAB to stop the countdown.  Then try this at the commandline:

```
Linux video=ofonly nosplash
```

and see if that gets you further down the road.  Thing is, it might be necessary to manually edit your /etc/yaboot.conf with values specific to your model that the installer doesn't know about.  We can get these specifics from these good faqs:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
and
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

There are other good sources of info, especially here in the forum.  Also be sure to check the read-only archive of the old Apple-PPC forums.

Let us know exactly which version of Ubuntu you are trying to install.  Each one sometimes has it's own little quirks, such as Intrepid needing *modprobe ide-scsi* in a virtual terminal to detect the cdrom.  Other releases have different issues.

Some suggest that for a first time install, you might want to install Dapper 6.06x and if that works, copy down your existing /etc/X11/xorg.conf and /etc/yaboot.conf for referernce before you upgrade to Hardy 8.04.  Of course you can try the latest releases directly.

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

While Kubuntu and Xubuntu are good, I always recommend getting your feet wet with Ubuntu first, and then if all works out, try the others.  I've found it best to use Ubuntu as the reference-install before tackling the others.  In some cases, Kubuntu and Xubuntu *may* have their own issues to deal with, but the flip side is that many have had no problem.  Just a personal observation...

Without a hard drive, if we can get you to a point where you can boot by passing those kernel parameters, you might still be able to manually edit your /etc/X11/xorg.conf with some test variables, and just logout / login (do not reboot!) and see if the changes worked. Hopefully it won't come to that.

It sounds like a lot of work, but once you've done it a few times, (grin) it doesn't seem like drudgery. :)

Again, happy to see you here.

---

### Post by pmhauge on 2008-11-24
I downloaded ubuntu-8.04.1-desktop-powerpc.iso from [http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

I'm using a 12" iBook G4 (Early 2004). IBOOK G4 12"/1.0/256/30/COMBO. 

The code you gave me to enter leaves me with the following: "Linux:2,/vmlinux: Unable to open file, Invalid device"

I'll check out the other resources and see if that gets me any further. Let me know if I have not provided you with enough info. Thanks for the quick reply!

---

### Post by pmhauge on 2008-11-24
Update: So I was playing around more at the boot prompt. Pressing tab gave me some various "suggestions" I guess you might call them. One of them was live-nospash. Typed that in. Enter. low and behold I got a Heron looking right at me.

---

### Post by stream303 on 2008-11-24
Great!

See if your screen is running at it's native resolution of 1024x768 in System > Preferences > Screen Resolution.  If not, that might be something to force with a manual edit of /etc/X11/xorg.conf later.

Make it look pretty by going into System > Preferences > Appearance > Fonts and turning on Subpixel Smoothing for lcd's.  This is an objective opinion of course.

Mouse pointer:  It took me awhile to find it, but for me I find that the mouse pointer is too small, especially on a laptop.  You may want to go back into Appearance > Theme > Customize > Pointer and choose one of the "DMZ" pointers, from which you can move the slider to make the pointer larger.

Since you are running live with no hard drive, there's no point in editing your /etc/yaboot.conf to take care of not having to enter nosplash in the "append=" lines followed by sudo ybin -v   

Normally after any installation or even live-cd environment, I like to run top in a terminal to see if there are any rogue processes hogging the cpu at 100%.  Probably not with Hardy, but this was a problem I had with earlier releases with my 12" ibook and network manager.

Tip: if you notice that the machine seems to be running at full speed all the time no matter what, you might try using synaptic or apt-get to download and install **cpudyn** as your frequency scaler.  You'll be able to do this without rebooting as the change will take place quicky - merely downloading it will do all the work.

Have fun!

---

### Post by pmhauge on 2008-11-24
Getting WiFi working seems to be the issue right now. However, it seems pointless to do all this work just working off of the live-cd. I simply need to replace my HD and get up and running. Thanks for all your help!

---

### Post by stream303 on 2008-11-24
No problem!  Seems like you've gotten past the point-of-proof concept. :)

When replacing the drive, just note the positions of the original jumpers, and it might be necessary to do a reset of the nvram after it is replaced - any time hardware is changed in a mac it is usually beneficial.

---

### Post by skralljt on 2008-12-07
I had to use the video=ofonly nosplash parameters to get to a desktop but then I get an error that says Nautilus cannot be used now, due to an unexpe           cted error.   Then it asks if I want to delete a bunch of panel applets.  How annoying!  The worst is that when I switch to one of the tty's by hitting control alt f2 I don't get a prompt, just that black screen.  I guess I'll have to hit the faq's.  
My trackpad doesn't work, if anyone needs a terminal hit alt+f2 and type xterm.

---

### Post by t1mb0 on 2009-04-04
Hi all, Please forgive me if this is incorrect as i am new to linux, but i think that i have found the answer to the black screen issue after a good install on a PPC laptop.

I brought a Powerbook G4 1.67Ghz off ebay and just finished getting it to boot into linux without any issues.

To avoid booting into darkness, at the boot prompt type:
 Linux video=ofonly

then enter your username and password, I then followed what i read in the 'howto' section of the following folder. "file:///usr/share/doc/yaboot/yaboot-howto.html/ch7.en.html" which said the following...

"There are currently three utilities provided to save your boot configuration changes to the boot partition: ybin, mkofboot, and yabootconfig. Ybin copies yaboot, yaboot.conf, and the CHRP script to the boot partition, and then performs the necessary blessing. Mkofboot initializes the bootstrap partition, then runs ybin. And yabootconfig creates a working yaboot.conf and then runs mkofboot. For details and options of these utilities, see the associated man pages or type the utility name followed by --help on the command line."

so i ran 'ybin' and then 'yabootconfig' and restarted my powerbook and all is well... cheers, i hope i helped someone and also that i may have found a simple fix. Tim

---


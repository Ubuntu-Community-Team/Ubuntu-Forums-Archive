---
title: "Booting to black screen, cannot get terminal"
date: 2009-05-13
forum: Apple Hardware Users
---

### Post by colinhayes on 2009-05-13
Yesterday I wiped my secondary hard drive, repartitioned it, reinstalled osx on one half, and let jaunty install on the other half.  Jaunty was on there before and worked fine, but I hadn't done a fresh install since like 6.04 I think, so it's been awhile.

Well, after yaboot comes up, I tell it to go into linux, it says "Loading, please wait...", and it goes into a beautiful black screen and stays there.  After a while the fans start firing up and I have to power off the computer.  ctrl+alt+f1(2,3,4,5,6...) does absolutely nothing.  I've tried repeatedly pushing the combination right after yaboot is done many, many times.

I'm at a loss, I remember there being problems with the video driver in the past, but I worked around that by getting to a terminal!

here's some pertinent info:
[HTML]
Hardware Overview:

  Model Name:	Power Mac G5
  Model Identifier:	PowerMac7,3
  Processor Name:	PowerPC G5  (2.2)
  Processor Speed:	2 GHz
  Number Of CPUs:	2
  L2 Cache (per CPU):	512 KB
  Memory:	1.5 GB
  Bus Speed:	1 GHz
  Boot ROM Version:	5.1.8f7
  Serial Number (system):	G8429ACHQPR

ATI Radeon 9600 XT:

  Chipset Model:	ATY,RV360
  Type:	Display
  Bus:	AGP
  Slot:	SLOT-1
  VRAM (Total):	128 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x4152
  Revision ID:	0x0000
  ROM Revision:	113-A13602-121
  Displays:
Apple Studio Display:
  Resolution:	1280 x 1024
  Depth:	32-Bit Color
  Core Image:	Hardware Accelerated
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported
  Rotation:	Supported
Display Connector:
  Status:	No Display Connected
[/HTML]

Any help would be appreciated!

---

### Post by tiresia on 2009-05-13
Have you tried with following argument```
Linux nosplash
```

---

### Post by stream303 on 2009-05-13
Yikes!  It is failing because it isn't loading the kernel for possibly one of these two reasons:

Were you sure you installed the 64-bit kernel version and not the 32-bit one?  When using the "alternate" installer, I normally stop the boot process at the second stage yaboot boot: prompt, hit TAB, and then have to enter something like:

install-powerpc64

as shown in the boot options.  It will then boot and install the 64bit version that a G5 needs.

Since I don't use the live-desktop CD, is there an option similar to that when first starting out?

Makes me think that the 32-bit kernel got installed, even though the installer itself chose the right one to bring itself up with.

The other issue might be that 64-bit kernel got installed correctly, but for some reason the /etc/yaboot.conf is misconfigured, pointing to the kernel at the wrong path.

I'd be surprised if this was the case, since that machine only has one hard drive controller, and you are merely dual-booting off the first drive, which yaboot usually has no problems with.

Since you can't even get past the 1st-stage of yaboot, something is wacky with the kernel - either it is the wrong 32-bit one, or the path to it is wrong in yaboot.conf.

OR, everything IS actually ok, except that at the end of installation, yaboot.conf never got written to nvram (manually one has to issue *sudo ybin -v* to do it.

I think step one would be to confirm that the 64-bit kernel has actually been told to install.

---

### Post by colinhayes on 2009-05-13
> **stream303 said:**
> Were you sure you installed the 64-bit kernel version and not the 32-bit one?

...

Since you can't even get past the 1st-stage of yaboot, something is wacky with the kernel - either it is the wrong 32-bit one, or the path to it is wrong in yaboot.conf.


regular disc won't boot on mine for some reason, so I used the alt installer, and told it to do the powerpc64 one, so it has that kernel.

also, it is getting past the first stage of yaboot.  I hit l, and then type Linux.  It is after that point that is says "Loading, please wait..." and goes to black.

I will try "Linux nosplash" when I get back home, at least that should be able to show me if anything is failing during the booting sequence.

---

### Post by stream303 on 2009-05-13
If that dreaded Ubuntu splashscreen is the problem (use a capital-L for Linux nosplash), I may have to visit Canonical in person. :)

---

### Post by colinhayes on 2009-05-14
> **stream303 said:**
> If that dreaded Ubuntu splashscreen is the problem (use a capital-L for Linux nosplash), I may have to visit Canonical in person. :)

Have fun during your travels!

---

### Post by stream303 on 2009-05-15
If that works for you temporarily, you can make that a permanent change so you don't have to type that in after every boot.

```
sudo nano /etc/yaboot.conf
```

Then, add *nosplash* to the **append=** lines, or change it from splash to nosplash.

CTRL-O to write out your changes, and CTRL-X to quit the editor.

Now make the system aware of the changes with:

```
sudo ybin -v
```

---

### Post by stream303 on 2009-05-15
Just a side note - keep an eye on your power supply, as they are very expensive and difficult to replace on G5 PowerMacs.

In fact, I'd heartily recommend downloading with the synaptic package manager the cpu frequency scaler "cpudyn", as it will cut down on the watts required of the power supply when the system goes idle.  In my case, it was about 10 watts when measured at the electrical outlet.

For some reason the standard cpu frequency scaler, powernowd, doesn't seem to be working reasonably well again, and cpudyn has never failed me.  Note that in jaunty, neither are installed by default.

One caveat - cpudyn isn't really intended for smp - that is, it will scale the processors simultaneously - which is not really ideal for smp.  BUT, it may be just fine for general purpose use especially when you consider the cost of finding and replacing your supply down the road.

In Ubuntu, I normally use the cpu-frequency scaling applet to keep an eye on it.  (right click the top bar, and "add to panel" and find the applet.  There are other ways to watch it, but this is nice visually.

Anway, just a hardware tip.

---

### Post by colinhayes on 2009-05-15
good enough fix, but that has to be a way to make it work.  When I first updated, it worked perfectly fine.  my old xorg.conf wasn't even anything special, it used fbdev instead of the ati driver.

---

### Post by stream303 on 2009-05-15
I think I'm getting lost as to what is happening now.  Are you saying that the screen issue is back after a successful update, even when you use Linux nosplash at the 2nd-stage boot prompt?

On a side note, I found this recent addition to the Known Issues faq about Jaunty and ATI cards which might be of interest:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu%209.04%20Jaunty%20Jackalope](https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu%209.04%20Jaunty%20Jackalope)

And you could try using video=ofonly in addition to nosplash to help diagnose it - if it works we make that permanent in yaboot.conf:

```
Linux nosplash video=ofonly
```

---

### Post by colinhayes on 2009-05-15
here's the rundown:

I wanted to check the linux half of my computer, and I discovered that Airport was not working (that other thread I started), so I drug my G5 over to my router and tried to get the airport fixed.  I decided to update to 9.04, too.  This worked perfectly.  The splash screen and everything was perfectly fine.  With your help I fixed what I was doing wrong with Airport, and it worked.  However, I had like 120GB free on my Ubuntu partition so I wiped the drive, repartitioned giving double the space to the OSX partition of that drive.  I did a fresh install of 9.04 with the alt installer and upon restart after passing the 2nd stage of yaboot, it hung on the black screen where the splash should have been and I could not get a terminal (this thread).  The 'nosplash' argument fixed it, it booted fine and airport worked perfectly after installing the firmware.

Now, since the splash worked before, I know that it has to be able to work again and I want it to.

---


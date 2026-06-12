---
title: "Mac Pro Nvidea dual screen problem (nothing but desktop background)"
date: 2011-06-30
forum: Apple Hardware Users
---

### Post by Chris Richard on 2011-06-30
Finally, after a week of tripping out trying to get Ubuntu working on a secondary drive, had it running just long enough to start trying to get the second monitor running with it.

Now, all I get is the desktop background on both screens. Nothing else. *sigh*

Running the latest Ubuntu release. This is my system:

 Model Name:    Mac Pro
  Model Identifier:    MacPro1,1
  Processor Name:    Dual-Core Intel Xeon
  Processor Speed:    2.66 GHz
  Number Of Processors:    2
  Total Number Of Cores:    4
  L2 Cache (per processor):    4 MB
  Memory:    2 GB
  Bus Speed:    1.33 GHz
  Boot ROM Version:    MP11.005D.B00
  SMC Version (system):    1.7f10


 Chipset Model:    NVIDIA GeForce 7300 GT
  Type:    GPU
  Bus:    PCIe
  Slot:    Slot-1
  PCIe Lane Width:    x16
  VRAM (Total):    256 MB
  Vendor:    NVIDIA (0x10de)
  Device ID:    0x0393
  Revision ID:    0x00a1
  ROM Revision:    3011
  Displays:
DELL U2410:
  Resolution:    1920 x 1200 @ 60 Hz
  Pixel Depth:    32-Bit Color (ARGB8888)
  Main Display:    Yes
  Mirror:    Off
  Online:    Yes
  Rotation:    Supported
DELL U2410:
  Resolution:    1920 x 1200 @ 60 Hz
  Pixel Depth:    32-Bit Color (ARGB8888)
  Mirror:    Off
  Online:    Yes
  Rotation:    Supported

I used the GUI system settings in Ubuntu to activate the second monitor as "separate."

Both are on now, but no system control is visible at all anymore. 

Anyone ever encounter this and know how to fix it? :-k

Thanks in advance

BTW: I can't access anything now. Wishing I'd at least set up a keyboard shortcut to the terminal, but didn't think to do that first so....

What now?:confused:

---

### Post by Chris Richard on 2011-06-30
Some additional notes:

It's looking to me like Ubuntu does not have very good support at all for Mac Pros with dual screens.

I should have mentioned above that before I activated the second monitor I had already downloaded an update recommended by Ubuntu in the driver updates to support 2d 3d graphics, but I also just tried booting up from the CD and setting the monitors to "separate" as well (presumably with the original driver, and that just made both screens go totally wonky. No desktop there either. Just background color, but messed up on the secondary, and nothing but gray on the primary.

After a solid week of screwing around with Ubuntu on this system, I'm just about to the point of resigning myself to the probable fact that Ubuntu just should not be run on this machine with this hardware setup. I'm sure I could eventually work out the multitude of problems that must be solved to make it work, but I'm thinking now there must be a somewhat simpler solution out there.

Maybe not, and it's not really that I mind so much tackling difficult puzzles like this, but it does get kind of annoying  after years of hearing how "simple" this or that linux release is, then discovering every time (so far, since about 2006), there is always something about the system I'm on that either makes it massively difficult or impossible to get working properly.

Sorry. Didn't mean to rant.

Haven't quite given up yet, but darned close to it and ready to try yet another release. I guess I have a bad habit of picking oddball systems a lot of stuff won't play nice with. :p

EDIT: Don't take any offense at this, please. It's been a looooong week, and after many, MANY failed attempts to get Ubuntu correctly installed, I finally did, then less than thirty minutes later, THIS happened. Needless to say, I was a bit twisted in the brain. I am still open to suggestions though, because my son (the little thirteen year old &^&%&!) managed to get Ubuntu running after a few failed attempts on his iMac, and I like what I see on his computer so far. So I really do want to see it working on mine too. I'm just becoming more skeptical as to whether it's really workable and worth it.

---

### Post by Chris Richard on 2011-06-30
Okay I guess I haven't given up entirely. I did have to reinstall Ubuntu, because I didn't really know what else to do at this point. So I am back up and running, sadly though, for the time being with a forlorn blank screen on the right.

I have set up terminal keyboard shortcut, and only hope it works if I happen to lose both screen's functionality again.

For now I just hope somebody has some ideas about this problem.

Thanks.

---

### Post by Chris Richard on 2011-07-01
Now that I'm back in the system I've had some time to revisit the steps that got me into trouble:

1) Opened System Settings and clicked Additional Drivers. This is where the system recommended upgrading the Nvidia drivers. Upgraded them.

2) Went into System Settings > Nvidia X Server Settings (don't recall if that was there before upgrading the driver). 

3) Opened X Server Display Configuration, saw screen 2 was disabled. Selected it, clicked Configure.

4) Three options there. Disabled, Separate X Screen (requires X restart), and TwinView.

I assume TwinView is the same as "Cloned" on other systems (same thing on both screens), so selected Separate, and restarted. That's when I came up with nothing but desktop background  images. Nothing else whatsoever on either screen. 

I'm even nervous now to try TwinView after that, but I would like to at least know whether the other monitor can be activated at all. I'm not totally confident I'll even get the terminal even though I've got the  shortcut set up now, but I'm gonna try it anyway. 

Wish me luck! *fingers crossed*

---

### Post by Chris Richard on 2011-07-01
I don't know what it is about me and asking for help on forums. I have the weirdest luck. I swear at least 80 to 90 percent of the time I come to any forum asking for technical help on anything at all, I find the answer before anyone answers. I'm not complaining, because it almost always happens rather quickly.

Turns out TwinView not only worked fine, but wasn't what I thought it was. In fact, it's exactly what I wanted. Not "clone."

Persistence really DOES pay off! Every time!

So I'll mark this "solved" and hopefully it helps out some other Mac Pro users using dual screens.

Oh, and....

Thanks for all your help! ):P:lolflag:

---

### Post by Chris Richard on 2011-07-01
Just out of curiosity though (not that anyone would necessarily know), does anyone know what "Separate" might mean in that setting? Maybe I just didn't understand what I was looking at there? I doubt it. I mean, there should have been something showing  other than just backgrounds, I would think....

---

### Post by Untitled_No4 on 2011-07-01
> TwinView

one large screen shared between two monitors
in Compiz-Fusion, it makes the "cube" appear as one large octagon
Separate X screen

separate X screens, one on each monitor
allows your window manager (Metacity, XFWM, Compiz, etc.) to be aware that there are two screens
in Compiz-Fusion, each monitor has its own cube, controlled separately

From: [https://help.ubuntu.com/community/NvidiaMultiMonitorsi](https://help.ubuntu.com/community/NvidiaMultiMonitorsi)

It's too late now, but I feel your pain. Used to have a Thinkpad which most of the time I used with a dock and dual external screens. I found out that if your setup is not mainstream, sometimes you're just alone at it. 

My advice to you would be to keep a copy of your working xorg.conf file safe. If you have any issues in the future you can always use the one that worked to solve your problems.

---

### Post by Chris Richard on 2011-07-03
Thanks Untitled_No4.

I do think the names for these options are terrible misnomers.

"Twin" to me, and I think to most people, usually means "two identical screens." Add to that the fact that the Live CD boots to two identical screens, and the assumption that is what one will get with Twin view seems reasonable, but that isn't what Twin view is at all.

I am a Linux noobie, but certainly not a noobie to the world of mulitple displays, desktops and operating systems.  "Twin" was a bad choice as a name for that setting IMHO.

---


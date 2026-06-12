---
title: "&quot;iMac G3 for Dummies&quot;"
date: 2013-04-02
forum: Apple Hardware Users
---

### Post by rsavage on 2013-04-02
This post is for users struggling to get Ubuntu/Lubuntu/Xubuntu/Kubuntu working with an iMac G3.  For more detailed information see here [https://wiki.ubuntu.com/PowerPCFAQ#Troubleshooting](https://wiki.ubuntu.com/PowerPCFAQ#Troubleshooting) .

1.  Download an 'alternate' iso or 'mini' iso and install as normal.
2.  After installation, make sure you have an ethernet cable connected and boot into single user mode.  So at the yaboot prompt type:
```

Linux single

```
    This will boot you into a root prompt so be careful what you type next!

3.  If you have used a 12.04 alternate iso then you need to update the kernel:
```

apt-get update
apt-get install linux-image-powerpc-smp

```
4.  Now you need to create an xorg.conf.  This is a basic one:
```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "ati"
    Option        "ForcePCIMode"    "True" 
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync    58-62
    VertRefresh    75-117
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
EndSection

```

The following will download the above file and move it into the right place for you:
```

wget -O /etc/X11/xorg.conf http://ubuntuone.com/0npbpgYS6r521c5YAIoxMn

```
5.  You can now reboot into a desktop:
```

reboot

```
6.  If you are using 12.04 then you can download the mesa legacy package to give you 3D acceleration.  You can find a pre-compiled version here [http://ubuntuone.com/379TLoe7yo2IAiOijAsOjQ](http://ubuntuone.com/379TLoe7yo2IAiOijAsOjQ) 

Lots more information in the FAQ and Known Issues pages:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by Lars Noodén on 2013-04-02
It would be good to attach the xorg.conf file here or to show it inline.

---

### Post by rsavage on 2013-04-02
Done

---

### Post by str8bs on 2013-04-02
Hey! You forgot to include 100 lines of voodoo nonsense in that config. :P

Kidding aside, I for one appreciate your contributions. Thanks

---

### Post by Svetlana Tovarisch on 2013-04-03
I don't know if I'm supposed to post here or make a new thread, but when I try installing the Xubuntu 12.04 PPC (32bit) mini.iso it halts on "Calling quiesce..." and doesn't do anything. Couldn't get any info on this issue. What am I doing wrong?

---

### Post by str8bs on 2013-04-04
Svetlana,

Is that at the initial boot of the mini iso? Or after the initial CLI install? I have used that ISO successfully on G3 500 and G3 600 and don't recall that error. Been a while though. I will try to test it this weekend and see if I can replicate.

The mini should give you the lastest kernel if CLI install completes. Any search references related to hang on calling quiesce seem to point to kernel image problem. (I think it has something to do with a call to open firmware. not sure)  Did you check md5 sums? Sure the image download is good?

Also, I think I better understand your earlier question after looking back at the downloads. It is most confusing. The "alternate" iso of the full Ubuntu ppc 12.04 (or whatever version) will allow you to perform your choice of L,X,K, or Ubuntu install in the same way the mini does. CLI followed by sudo apt-get-update, then sudo tasksel

---

### Post by rsavage on 2013-04-04
After the "Calling quiesce..." the screen is controlled by the framebuffer.  As str8bs says, a very few people have reported this before, but I'm not sure they have figured out what was wrong.  It is either a dodgy iso, but my money is on the openfirmware framebuffer.

Some things you can try (from the official documentation):

> 
**Display-visibility on OldWorld Powermacs. ** Some OldWorld Powermacs, most notably those with the &#8220;control&#8221; display driver, may not reliably produce a colormap under Linux when the display is configured for more than 256 colors. If you are experiencing such issues with your display after rebooting (you can sometimes see data on the monitor, but on other occasions cannot see anything) or, if the screen turns black after booting the installer instead of showing you the user interface, try changing your display settings under MacOS to use 256 colors instead of &#8220;thousands&#8221; or &#8220;millions&#8221;.


Have you tried resetting the pram?

If you were using 12.10 then I would suggest:

> 
Many older Apple monitors used a 640x480 67Hz mode. If your video appears skewed on an older Apple monitor, try appending the boot argument **video=atyfb:vmode:6** , which will select that mode for most Mach64 and Rage video hardware. For Rage 128 hardware, this changes to **video=aty128fb:vmode:6** .


The problem is you don't have aty128 available on the 12.04 mini iso.

I think you currently have debian installed which has the atyfb128 framebuffer built-in.  12.10 also has this built-in from the start so you could give that a try.  You could follow the 12.04 live iso instructions in the Known Issues page on a lubuntu iso to modprobe atyfb128.  It should be possible to do this on the mini.iso, but it is a bit of a pain (particulalrly being a framebuffer module which makes it even harder) - [https://wiki.ubuntu.com/PowerPCFAQ#A_kernel_module_is_missing_from_the_alternate.2BAC8-mini_isos.3B_what_can_I_do.3F](https://wiki.ubuntu.com/PowerPCFAQ#A_kernel_module_is_missing_from_the_alternate.2BAC8-mini_isos.3B_what_can_I_do.3F) .

If you really want xubuntu 12.04 then I'll give you a link to a download, but please try the above first.

---

### Post by rsavage on 2013-04-04
According to my iBook the next line after the "Calling quiesce..." should be

```

returning from prom_init

```

and then the splash screen kicks in (or the kernel text starts scrolling if you don't have a splash screen).

---

### Post by Svetlana Tovarisch on 2013-04-04
> **str8bs said:**
> Svetlana,

Is that at the initial boot of the mini iso? Or after the initial CLI install? I have used that ISO successfully on G3 500 and G3 600 and don't recall that error. Been a while though. I will try to test it this weekend and see if I can replicate.

The mini should give you the lastest kernel if CLI install completes. Any search references related to hang on calling quiesce seem to point to kernel image problem. (I think it has something to do with a call to open firmware. not sure)  Did you check md5 sums? Sure the image download is good?

Also, I think I better understand your earlier question after looking back at the downloads. It is most confusing. The "alternate" iso of the full Ubuntu ppc 12.04 (or whatever version) will allow you to perform your choice of L,X,K, or Ubuntu install in the same way the mini does. CLI followed by sudo apt-get-update, then sudo tasksel

This is at the initial boot of the mini iso. Install process never starts.

> **rsavage said:**
> After the "Calling quiesce..." the screen is controlled by the framebuffer.  As str8bs says, a very few people have reported this before, but I'm not sure they have figured out what was wrong.  It is either a dodgy iso, but my money is on the openfirmware framebuffer.

Some things you can try (from the official documentation):

Have you tried resetting the pram?

I haven't. My PRAM is being stored properly since I replaced the iMac's battery just a few months ago, and Debian PPC installed fine (I'm just not using it for a lack of good video drivers which make even a bare desktop unpleasantly sluggish to use). Do I still have to reset the PRAM? I would rather not lose the monitor geometry settings in it.

> **rsavage said:**
>  If you were using 12.10 then I would suggest:

The problem is you don't have aty128 available on the 12.04 mini iso.

I think you currently have debian installed which has the atyfb128 framebuffer built-in.  12.10 also has this built-in from the start so you could give that a try.  You could follow the 12.04 live iso instructions in the Known Issues page on a lubuntu iso to modprobe atyfb128.  It should be possible to do this on the mini.iso, but it is a bit of a pain (particulalrly being a framebuffer module which makes it even harder) - [https://wiki.ubuntu.com/PowerPCFAQ#A_kernel_module_is_missing_from_the_alternate.2BAC8-mini_isos.3B_what_can_I_do.3F](https://wiki.ubuntu.com/PowerPCFAQ#A_kernel_module_is_missing_from_the_alternate.2BAC8-mini_isos.3B_what_can_I_do.3F) .

If you really want xubuntu 12.04 then I'll give you a link to a download, but please try the above first.

I thought 12.04 was the latest PPC "stable" version, or at least the one being worked on the most. I'll take whatever has a working video driver with decent acceleration working. People using similar iMac G3 models report 300+ FPS on glxgears (not that I'm using it as an end-all benchmark, but, y'know) just by using older Mesa packages while no matter what I do the best I can get is about 25-30, all because apparently I have half the VRAM other people have, but that doesn't seem to stop Mac OS X from running smoothly (even on the Flurry screensaver, which should be pretty GPU-intensive), so I'd like to believe I can get a modern linux OS running on it. I don't mind what version as long as it has such a working driver on it, and I'd be very thankful if you could lead me to it.

EDIT: The fact that I have half the VRAM than newer models being an issue is due to the fact that this stops Linux from loading GLX, and could be solved by using a depth lower than 24, but X simply refuses to start properly set to 16, leaving a half-locked system (extremely delayed SSH until X is killed) and a garbled screen, and GLX refuses to run at 15bpp. This is probably besides the point, however, since these are problems experienced in another Linux distro entirely. Sorry for sidetracking.

---

### Post by str8bs on 2013-04-05
I would agree PRAM not likely culprit if other installs are booting fine. But, I have seen stranger things.
Just a guess, but I would suspect something with ISO or the burn to cd or DD to usb. 

12.04 is LTS which many prefer because once you get it working, you will get security updates and such without having to worry about much breakage.
12.10 includes EXA patch for R128 or you can easily add to 12.04 which will get you 2D acceleration. (nothing to do with GLXgears) It has some issues, but there are workarounds to make it quite useable as mentioned in the testing thread.

As for Mesa/GL and 3D acceleration, you may be hitting [this bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-r128/+bug/1023975"). (apparently, not many people other than you or I care if GL works on a G3 iMac R128) :) 
 I don't think Ubuntu or any of its variants will be different than Debian in that regard. There may be a way to force it to work at lower res with R128 at 8 Meg.
[Old thread discussing issue.]("http://ubuntuforums.org/showthread.php?t=2013307") I will try giving it a go on a 333 G3 with Rage Pro 6Meg this weekend if I can find time and scrounge some RAM for it.

---

### Post by str8bs on 2013-04-06
@Svetlana,

I was able to boot the 32-bit PowerPC  Precise cli install from [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) on iMac G3 600 and iMac G3 333. Haven't gotten to the video testing on the 333 yet.

---

### Post by este.el.paz on 2013-04-06
> **rsavage said:**
> According to my iBook the next line after the "Calling quiesce..." should be
```

returning from prom_init

```
and then the splash screen kicks in (or the kernel text starts scrolling if you don't have a splash screen).

@ST, et al:

Not to be a doom-sayer of darkest negativity, but having recently gone through a spate of paroxysmal kernel panics in my G4 iMac, I got to see this "calling quiesce" or stalling at "returning from prom_init" . . . which was the sign that . . . there was a "panic attack" . . . .  Intermittent at first, then becoming more and more of a problem, rebooting from OSX back into Xubun, or trying to boot install discs . . . .  maybe try to check if "the disk is healthy" in DU?  Or run Apple Hardware Test, although AHT didn't find any problems even though the KPs continued, and KPs do other damage to, uh, stuff . . . .  Much of my travails trying to deal with the KPs can be found in various forums . . . .

e.e.p.

---

### Post by rsavage on 2013-04-06
> **str8bs said:**
> @Svetlana,

I was able to boot the 32-bit PowerPC  Precise cli install from [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) on iMac G3 600 and iMac G3 333. Haven't gotten to the video testing on the 333 yet.

The 333 has a rage card (not rage 128).  You need to have "ati" in the xorg.conf not "r128".

---

### Post by str8bs on 2013-04-06
@rsavage - Edited. Thanks. I usually leave them all at ATI anyway, but doubtful this HW will tell us much regarding Svetlana's gpu.
Just a thought: wouldn't having "ATI" in your sample config in the original post make it more universal? On the very few I've tested, it auto detects R128 fine. There may situations where it doesn't though.

---

### Post by Svetlana Tovarisch on 2013-04-06
> **este.el.paz said:**
> @ST, et al:

Not to be a doom-sayer of darkest negativity, but having recently gone through a spate of paroxysmal kernel panics in my G4 iMac, I got to see this "calling quiesce" or stalling at "returning from prom_init" . . . which was the sign that . . . there was a "panic attack" . . . .  Intermittent at first, then becoming more and more of a problem, rebooting from OSX back into Xubun, or trying to boot install discs . . . .  maybe try to check if "the disk is healthy" in DU?  Or run Apple Hardware Test, although AHT didn't find any problems even though the KPs continued, and KPs do other damage to, uh, stuff . . . .  Much of my travails trying to deal with the KPs can be found in various forums . . . .

e.e.p.

I'm not booting from a hard drive, I'm booting from USB, which worked fine with Debian mini.iso but it doesn't seem to be working with the Ubuntu ones, I've tried DD'ing 12.04 LTS twice onto it now with the same results, stuck at "Calling quiesce...", no "prom_init", no splash screen. Is there any other ISO I should try or do I really have to burn a whopping 29mb onto a full blank CD-R?

---

### Post by str8bs on 2013-04-06
@Svetlana,

The alternate PowerPC install from [here]("http://cdimage.ubuntu.com/releases/precise/release/") and then type "cli" at boot: prompt. Follow same install steps as mini.iso and then follow rsavage instructions in first post. This is how I usually install L or X ubuntu.
 With the mini.iso, have you tried booting "cli video=ofonly" ?

---

### Post by Svetlana Tovarisch on 2013-04-06
> **str8bs said:**
> @Svetlana,

The alternate PowerPC install from [here]("http://cdimage.ubuntu.com/releases/precise/release/") and then type "cli" at boot: prompt. Follow same install steps as mini.iso and then follow rsavage instructions in first post. This is how I usually install L or X ubuntu.
 With the mini.iso, have you tried booting "cli video=ofonly" ?

Just wrote that ISO to my USB and booted off it, tried booting with "cli video=ofonly" to the same effect.

---

### Post by str8bs on 2013-04-06
> **Svetlana Tovarisch said:**
> Just wrote that ISO to my USB and booted off it, tried booting with "cli video=ofonly" to the same effect.
Other than what rsavage mentioned in post #7, I am out of ideas. If you download the Debian 7 mini.iso, that one boots cli fine still? I tested my 600 from usb and I've done a 500 previously, both of which use aty128fb but also both have same video, ATI Rage 128 Ultra 16M. To rule out missing aty128fb, you could try 12.10 mini or alternate. There must be something specific about your hardware that my three tested don't have in common with yours. The only real difference looking at the specs is CPU and yours has ATI Rage 128 Pro 8M and DVD. Wish I had a better answer for you.

---

### Post by Svetlana Tovarisch on 2013-04-07
> **str8bs said:**
> Other than what rsavage mentioned in post #7, I am out of ideas. If you download the Debian 7 mini.iso, that one boots cli fine still? I tested my 600 from usb and I've done a 500 previously, both of which use aty128fb but also both have same video, ATI Rage 128 Ultra 16M. To rule out missing aty128fb, you could try 12.10 mini or alternate. There must be something specific about your hardware that my three tested don't have in common with yours. The only real difference looking at the specs is CPU and yours has ATI Rage 128 Pro 8M and DVD. Wish I had a better answer for you.

The latest Debian businesscard ISO boots into the install procedure fine. Is there a mini.iso for 12.10? I can only find a full 700mb ISO.

---

### Post by rsavage on 2013-04-07
> **Svetlana Tovarisch said:**
> The latest Debian businesscard ISO boots into the install procedure fine. 
Have you tried it after you installed from it?

> I haven't. My PRAM is being stored properly since I replaced the iMac's  battery just a few months ago, and Debian PPC installed fine (I'm just  not using it for a lack of good video drivers which make even a bare  desktop unpleasantly sluggish to use). Do I still have to reset the  PRAM? I would rather not lose the monitor geometry settings in it.

Up to you.  If installing debian mucked something up then it will clear that up.  It will also presumeably reset you to a default video mode that may just work.  

> 
Is there a mini.iso for 12.10? I can only find a full 700mb ISO.
In the wisdom of the lubuntu testers they pushed for it to be tested only to fail it (and passed lubuntu even though it has the same problems).  So it is not with all the others, but I put a link for it on the downloads page [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by rsavage on 2013-04-07
> **str8bs said:**
> 
Just a thought: wouldn't having "ATI" in your sample config in the original post make it more universal? On the very few I've tested, it auto detects R128 fine.

Yep, to be honest I had forgotten there were non r128 imacs until yesterday.  Will change when I get around to uploading a new file.  Do you know if the other bits have to stay the same?

Btw, the aty framebuffer is not built in so you have to manually modprobe it [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F) .  Dunno if that will make a difference performance wise?

---

### Post by este.el.paz on 2013-04-07
> **Svetlana Tovarisch said:**
> I'm not booting from a hard drive, I'm booting from USB, which worked fine with Debian mini.iso but it doesn't seem to be working with the Ubuntu ones, I've tried DD'ing 12.04 LTS twice onto it now with the same results, stuck at "Calling quiesce...", no "prom_init", no splash screen. Is there any other ISO I should try or do I really have to burn a whopping 29mb onto a full blank CD-R?

@ST:

I'm not sure that the source of what you are trying to boot from would matter in terms of hardware issues. a KP is a KP by any other name.  But, let's say I'm wrong and all is well in your hardware, there still might be room for comment on the procedure front; i.e., if something isn't working, repeating it with expectation of different outcome . . . is not likely to result in anything more than . . . what you got before . . . and might indicate the need for trying something else.  Personally the USB approach seemed to have more steps than the CD/DVD way, since you've tried the USB way a number of times, yes, why not burn a CD--but, note that str8bs has given the link to the ALTERNATE installer a few times, I would suggest trying that way and see if you get a different outcome.  I've used the CD-RW and I've burned and erased a number of times, better than CD-R . . . .  I don't know the details, but if the data isn't on the CD it would have to be downloaded and installed anyway, the more stuff that is on the CD the better I feel???  But it also seems that the alternate installer seems to have better installs, I did the recent Xubuntu 12.04 savage .iso using the Desktop installer, and there was a glitch using "install manually" which is mentioned in the FAQ, so after a few tries and failing I tried something different and chose the "automatic" "install next to other OS" option, avenue of least resistance, requiring no skilz from me . . . I crossed my fingers, whispered a prayer to the God of my choosing . . . and it worked.  I would try the Alternate 12.04 (LTS) installer for the machine that you have . . . from CD-R(RW) and see how that goes for you . . . .

e.e.p.

---

### Post by abtabt on 2013-04-07
> **rsavage said:**
> Yep, to be honest I had forgotten there were non r128 imacs until yesterday.  Will change when I get around to uploading a new file.  Do you know if the other bits have to stay the same?

Btw, the aty framebuffer is not built in so you have to manually modprobe it [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F) .  Dunno if that will make a difference performance wise?

this model iMAC 333 256 MB RAM 

[http://www.everymac.com/systems/apple/imac/specs/imac_333.html](http://www.everymac.com/systems/apple/imac/specs/imac_333.html)

no manually probe need

and the xorg.conf is

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "ati"
    Option        "ForcePCIMode"    "True"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync    58-62
    VertRefresh    75-117
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

and i recomend DefaultDepth same as OSX or OS 9 (16 is ok too ) i had some display issue when the DefaultDepth is not same as MAC OS

this system is build from  mini iso 12.04 and  LXDE desktop etc etc
and updated 2013 04 07

---

### Post by str8bs on 2013-04-07
@abtabt Thanks! Long story short, a dremel tool will be required before I can resume testing the two 333's I currently have here. :(

If you have time, could you:
1. Check Xorg.0.log and confirm driver used. I think those use mach64 for the Rage (Not 128) series? 
2. Confirm that "forcePCImode" is necessary? If so, that would indicate the bug requiring that workaround is not driver (R128) but something in uninorth or kernel?
3. Same for monitor section. EDID scans default to wrong resolution so blank screen without restricting HorizSync and VertRefresh.
4. Curious if you are able to get old mesa DRI loaded with or without "forcePCImode". From what I've read, I don't think it was ever supported on cards with less than 9MB at color depth over 16 so you would have to test at lower depth than 24.

---

### Post by Svetlana Tovarisch on 2013-04-07
The 12.10 mini iso boots fine, but the installation halts after trying to download the release notes, leaving me with an empty purple background.

EDIT: I'm sorry, nevermind. The installation had indeed halted for several minutes without any message but after leaving it on for a while it suddenly started loading the additional components. I'll report back once the installation is finished.

---

### Post by Svetlana Tovarisch on 2013-04-08
Well.. I finally got the whole Xubuntu package installed and xorg.conf in place.. The system takes a considerably long time to boot (compared to Debian and even OS X 10.4.11), landing me in a login screen that only displays me a garbled error message for a fraction of a second before throwing me back onto it whenever i try to login, and before that the console login would also hang for longer than usual, longer than the delay it halts for when I mistype my password. So all in all, not functional.

What did I do wrong and what can I do to fix it?

---

### Post by Lars Noodén on 2013-04-08
I had mixed luck with XFCE on PPC back when I tried it.  It was a good while back, though.  The way I might recommend would be to start from the Lubuntu Alternate PPC installer for 12.04 or 12.10 and work up from that.  You can then get Xubuntu from the package xubuntu-desktop.

---

### Post by abtabt on 2013-04-08
> **str8bs said:**
> @abtabt Thanks! Long story short, a dremel tool will be required before I can resume testing the two 333's I currently have here. :(

If you have time, could you:
1. Check Xorg.0.log and confirm driver used. I think those use mach64 for the Rage (Not 128) series? 
2. Confirm that "forcePCImode" is necessary? If so, that would indicate the bug requiring that workaround is not driver (R128) but something in uninorth or kernel?
3. Same for monitor section. EDID scans default to wrong resolution so blank screen without restricting HorizSync and VertRefresh.
4. Curious if you are able to get old mesa DRI loaded with or without "forcePCImode". From what I've read, I don't think it was ever supported on cards with less than 9MB at color depth over 16 so you would have to test at lower depth than 24.


1. true mach64 is used

    39.398] (II) LoadModule: "ati"
[    39.416] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    39.417] (II) Module ati: vendor="X.Org Foundation"
[    39.417]    compiled for 1.11.3, module version = 6.14.99
[    39.417]    Module class: X.Org Video Driver
[    39.418]    ABI class: X.Org Video Driver, version 11.0
[    39.418] (II) LoadModule: "mach64"
[    39.424] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
[    39.425] (II) Module mach64: vendor="X.Org Foundation"
[    39.426]    compiled for 1.11.3, module version = 6.9.0
[    39.426]    Module class: X.Org Video Driver
[    39.426]    ABI class: X.Org Video Driver, version 11.0
[    39.426] (II) MACH64: Driver for ATI Mach64 chipsets
[    39.426] (++) using VT number 7

[    39.459] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
[    39.462] (II) MACH64(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
[    39.462] (**) MACH64(0): Depth 24, (--) framebuffer bpp 32
[    39.462] (**) MACH64(0): Option "force_pci_mode" "True"
[    39.463] (==) MACH64(0): Using XAA acceleration architecture


2. "forcePCImode" is not necessary

3. if no   HorizSync  VertRefresh in xorg.conf  then black

4, haven't tried yet

---

### Post by Svetlana Tovarisch on 2013-04-08
> **Lars Noodén said:**
> I had mixed luck with XFCE on PPC back when I tried it.  It was a good while back, though.  The way I might recommend would be to start from the Lubuntu Alternate PPC installer for 12.04 or 12.10 and work up from that.  You can then get Xubuntu from the package xubuntu-desktop.

That's what I did, although with Xubuntu 12.10 alternate (which didn't install X or any other package at all because the package selection screen skipped a few seconds after i just started reading it for no reason and I had to apt-get the packages later, and the system was already quite sluggish boot-wise by then), and it isn't usable at all. Xubuntu isn't working properly and the login times are annoying, while Debian 6 worked fine except for no hardware acceleration.

---

### Post by str8bs on 2013-04-08
@rsavage - aty128fb added to modules and init didn't change performance, but the splash screen tip works great.

@abtabt - Thanks for taking the time. 

@Svetlana - We need to make sure we are looking "apples to apples." (pun intended) When you were at low GLXgears numbers in Debian, what color depth were you at? Was DRI enabled? Not likely as the numbers you gave are likely software rendering. We could try looking at some logs. Just a suggestion, you may want to start a thread with your machine and video card in the title. I only say that as it might help others with the same hardware more easily find the information. You could post them here too if you want. Look for the same dmesg and Xorg.0.log information as in the other thread I linked. Specific to getting Mesa 3d (glxgears increase) working on yours, I only have ideas of some things to try and can't guaranty getting you to that goal. There is obviously something in the 12.04 kernel (mini iso) that doesn't agree with your hardware that is not present in 12.10 or current Debian testing.

---

### Post by Svetlana Tovarisch on 2013-04-08
> **str8bs said:**
> @Svetlana - We need to make sure we are looking "apples to apples." (pun intended) When you were at low GLXgears numbers in Debian, what color depth were you at? Was DRI enabled? Not likely as the numbers you gave are likely software rendering. We could try looking at some logs. Just a suggestion, you may want to start a thread with your machine and video card in the title. I only say that as it might help others with the same hardware more easily find the information. You could post them here too if you want. Look for the same dmesg and Xorg.0.log information as in the other thread I linked. Specific to getting Mesa 3d (glxgears increase) working on yours, I only have ideas of some things to try and can't guaranty getting you to that goal. There is obviously something in the 12.04 kernel (mini iso) that doesn't agree with your hardware that is not present in 12.10 or current Debian testing.

24 bpp. 16 didn't work (pseudo-halt with garbled or no screen) and 15 isn't supported by DRI. At 24 bpp, there isn't enough VRAM.

If there was only something to X to start properly at 16 bpp, that should be the ticket to getting DRI to work (even though X didn't work, it was the one mode that didn't throw a DRI/GLX error) and consequently having a faster graphical experience.

About what's in the kernel, I've no idea, but I'll probably have to reformat the 12.10 partition anyway as it is completely unusable in this state (slow boot, slow login, broken xubuntu/xfce), and if there's more development going on in 12.04 that would probably be better suited here once it works. I'm not good at finding hidden stuff by myself, so if you guys can guide me towards what I should install in my machine to get it working properly I'd be more than willing to try it and report back.

---

### Post by gioloi66 on 2013-05-09
Hi there.
I followed the guide verbatim and all worked perfectly. Thanks.
The only problem is that the system is veeeeery slow. Much more than the Panther 10.3.9 that was previously installed.
I immediately wiped out Unity and went back to Gnome, with no material improvement.
My machine is a G3 350 MHz with HD 6.8GB, RAM 512 MB, no firewire.
Now I'm trying with Lubuntu 12.4 Alternate, hoping that the guide is still valid.

EDIT: Just installed Lubuntu. Much better. My iMac has come to new life!
Thanks again for the very useful guide.

---

### Post by imacg3ppc on 2013-05-13
> **rsavage said:**
> After the "Calling quiesce..." the screen is controlled by the framebuffer.  As str8bs says, a very few people have reported this before, but I'm not sure they have figured out what was wrong.  It is either a dodgy iso, but my money is on the openfirmware framebuffer.

Some things you can try (from the official documentation):



Have you tried resetting the pram?

If you were using 12.10 then I would suggest:



The problem is you don't have aty128 available on the 12.04 mini iso.

I think you currently have debian installed which has the atyfb128 framebuffer built-in.  12.10 also has this built-in from the start so you could give that a try.  You could follow the 12.04 live iso instructions in the Known Issues page on a lubuntu iso to modprobe atyfb128.  It should be possible to do this on the mini.iso, but it is a bit of a pain (particulalrly being a framebuffer module which makes it even harder) - [https://wiki.ubuntu.com/PowerPCFAQ#A_kernel_module_is_missing_from_the_alternate.2BAC8-mini_isos.3B_what_can_I_do.3F](https://wiki.ubuntu.com/PowerPCFAQ#A_kernel_module_is_missing_from_the_alternate.2BAC8-mini_isos.3B_what_can_I_do.3F) .

If you really want xubuntu 12.04 then I'll give you a link to a download, but please try the above first.

its the offb. I had the same problem when experimenting with different vmodes and yaboot parameters. The only that worked was video=aty128fb:1024x768-60

Once you get the xorg.conf edited (or created) in nano just write out (ctrl+O) to /etc/X11/xorg.conf and "shutdown -r now". reset the pram by holding apple+option+p+r when you hear chime... and then let yaboot load ubuntu automatically. do not add parameters. X should boot. This may take some trial and error.

---

### Post by imacg3ppc on 2013-05-13
> **gioloi66 said:**
> Hi there.
I followed the guide verbatim and all worked perfectly. Thanks.
The only problem is that the system is veeeeery slow. Much more than the Panther 10.3.9 that was previously installed.
I immediately wiped out Unity and went back to Gnome, with no material improvement.
My machine is a G3 350 MHz with HD 6.8GB, RAM 512 MB, no firewire.
Now I'm trying with Lubuntu 12.4 Alternate, hoping that the guide is still valid.

EDIT: Just installed Lubuntu. Much better. My iMac has come to new life!
Thanks again for the very useful guide.

Hey, usuing Lubuntu 12.04 and lxde.. unity is so ugly to me, i hate smart phones and tablets. ew.
Isn't it awesome?? I remember when i was in 9th grade it was 1999/2000... and the cpu lab in school was filled with all these colorful imacs... i couldn't afford an apple until 2006.. and it was part of a student loan so i got an aluminum MBP core 2 duo. loved it. But i got 2 of these g3 machines really cheap. Special edition "Flower Power" 600mhz 684mb ram airport and yesterday picked up an "Indigo" 500mhz 300something? mb ram amd it has osx 10.4.1 and os 9.2.2...

conclusion: OSX sucks on these boxes. Ubuntu kicks it in the tail speed wise. OSX definatly has a faster boot time.. even the 500mhz machine, but the speed is worth the extra minute wait once you get to log in. Everything works.. haven't tested audio yet. I want to preserve these cpus as fully functional workstations and kudos to anyone else who wants to do the same.

---

### Post by Svetlana Tovarisch on 2013-05-13
Just got alternate Lubuntu 13.04 for powerpc. Amazingly sluggish and not working at all, simply using the file manager causes it to stop responding, and I simply have no idea what's wrong with my computer.

I have a seemingly standard 450mhz Ruby iMac G3, so what am I doing wrong? Looks like OS X is still the best bet speed-wise..

---

### Post by imacg3ppc on 2013-05-14
so have you tried 12.04 on the ruby? i have not had time to read this whole thread. were you unsuccessful with 12.04? 

i have a second imac i'm going to use to dual-boot, i was going to try 12.10 on that machine to see the difference. But i have read that 12.10 has lost support for some of the features that these g3 slot loading machines need???

---

### Post by Svetlana Tovarisch on 2013-05-16
> **imacg3ppc said:**
> so have you tried 12.04 on the ruby? i have not had time to read this whole thread. were you unsuccessful with 12.04? 

i have a second imac i'm going to use to dual-boot, i was going to try 12.10 on that machine to see the difference. But i have read that 12.10 has lost support for some of the features that these g3 slot loading machines need???

12.04 does not boot at all, hangs at "Calling Quiesce".

---

### Post by rkmugen on 2013-05-16
> **Svetlana Tovarisch said:**
> 12.04 does not boot at all, hangs at "Calling Quiesce".

Svetlana!  We meet again!  And you're still having problems with your iMac... :(

Well, not to steer you away from your Ubuntu adventure, but with Debian 7 (wheezy) now out of "testing", have you considered trying to install that (essentially just plain Debian, no MintPPC or Ubuntu repos)?  Also, just for the sake of completeness and so that we're all on the same page, could you list the most recent distros you've tried and give us an idea of what worked (or didn't work) on your particular iMac G3?  I find it very difficult to understand why it seems like your iMac G3 is the seemingly the only one I've heard of that can run OSX Tiger acceptably well, while seemingly no other version of Linux would even succeed to fully boot into the GUI.

This might be a long shot, but is there any physical damage to the machine or perhaps even the mobo?  Or at least, any that you can determine visually?

---

### Post by str8bs on 2013-05-17
> **imacg3ppc said:**
> so have you tried 12.04 on the ruby? i have not had time to read this whole thread. were you unsuccessful with 12.04? 

i have a second imac i'm going to use to dual-boot, i was going to try 12.10 on that machine to see the difference. But i have read that 12.10 has lost support for some of the features that these g3 slot loading machines need???

AFAIK
Mesa support was dropped (upstream) beginning in 12.04(3.2) for several cards which include Rage 128 and Rage on iMacs. This is 3D(OpenGL) support.
XAA was removed I think beginning in 12.10 which may have resulted in new bugs for many of the same old cards. They should fall back to shadowfb.
EXA (2D) acceleration support for Rage 128 was added beginning with 12.10 thanks to a determined loan developer and it works quite well IMO.
Support for the card drivers themselves has not been dropped.

---

### Post by str8bs on 2013-05-17
> **Svetlana Tovarisch said:**
> Just got alternate Lubuntu 13.04 for powerpc. Amazingly sluggish and not working at all, simply using the file manager causes it to stop responding, and I simply have no idea what's wrong with my computer.

I have a seemingly standard 450mhz Ruby iMac G3, so what am I doing wrong? Looks like OS X is still the best bet speed-wise..

Have you compared performance using FBDEV? Remove the forcePCImode line from the config in post 1 and change "Driver" to FBDEV to see.

As for 12.04 "calling quiesce" hang on yours, I would expect to see the "returning from PROM init". However, it is possible to boot with no framebuffers active and the display  will just stay on that screen until you modprobe a frame buffer.

---

### Post by str8bs on 2013-05-17
Attached is my attempt at getting iMac G3's working with as few steps and typing as possible based on my tests. RSAVAGE's excellent first post is still applicable to 12.04 and that config will still work with R128 in 13.04. I found forcing PCI mode workaround no longer necessary in 13.04. 

This applies to **iMac G3 with Rage 128** video. (All Slot-Loading iMac G3's)
*Ubuntu 13.04 Raring Ringtail but should work with 12.10 as well.
 
 
 
1. To boot the live desktop iso:
```
boot: live video=offb:off video=aty128fb:1024x768@75
```
 
The splash screen will display and then the screen will go blank.
 
2. Press <ctl><alt><F1> to get to a command prompt.
3. ```
sudo nano /etc/X11/xorg.conf
```
4. Enter the following lines. *If you can't see the cursor off to the left, just tab key until you can see it.
```

  Section "Monitor"
  Identifier "SillyImac"
  HorizSync 58-62
  VertRefresh 75-117
  EndSection
 
  Section "Screen"
  Identifier "Mine"
  Monitor "SillyImac"
  EndSection

```
 
5. <ctl> o and enter to save
6. <ctl> x to exit back to prompt
7.```
 sudo stop lightdm
```
8.```
 sudo start lightdm
```
 
If unsuccessful, <ctl><alt<F1> to go back to prompt and check steps 3 and 4
for type errors.
 
 ______________________________________________________________________________
 
This applies to **iMac G3 with Rage or Rage Pro video**. (All Tray-Loading iMac G3's)
*Ubuntu 13.04 Raring Ringtail but should work with 12.10 as well.
 
 
 
1. After performing netboot/mini or altnerate install:
```
boot: linux snd-powermac.blacklist=yes
```
 
Allow SEVERAL minutes for the machine to finish booting.
The screen will be blank or have some garbled messages.
 
2. Press <ctl><alt><F1> to get to a command prompt.
3. ```
sudo nano /etc/X11/xorg.conf
```
4. Enter the following lines. *If you can't see the cursor off to the left, just tab key until you can see it.

                ```

Section "Device"
Identifier "GoofyApple"
Option "NoAccel" "True"
EndSection
 
Section "Monitor"
Identifier "SillyImac"
HorizSync 58-62
VertRefresh 75-117
EndSection
 
Section "Screen"
Identifier "Mine"
Monitor "SillyImac"
EndSection
```

5. <ctl> o and enter to save
6. <ctl> x to exit back to prompt
7. ```
sudo stop lightdm
```
8. ```
sudo start lightdm
 
```
If unsuccessful, <ctl><alt<F1> to go back to prompt and check steps 3 and 4 for type errors.
The "NoAccel" option is necessary since XAA was dropped 12.10 and this card does not currently fall back properly on its own.
Blacklisting snd-powermac isn't necessary to boot, but a LOUD shrill will be heard instead of sound if any sound is played without this.

Str8

---

### Post by gioloi66 on 2013-05-19
> **rsavage said:**
> 
6.  If you are using 12.04 then you can download the mesa legacy package to give you 3D acceleration.  You can find a pre-compiled version here [http://ubuntuone.com/379TLoe7yo2IAiOijAsOjQ](http://ubuntuone.com/379TLoe7yo2IAiOijAsOjQ)

Despite the fact I correctly installed the package, when I check the rendering engine with

```
[COLOR=#111111][FONT=courier]glxinfo | grep render[/FONT][/COLOR]
```

the result is:

```
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
```

That makes the graphical interface quite sluggish, definitely less reactive than OSX 10.3.9.

My iMac is a 350 MHz slot loading with no firewire and ATI Rage 128 VR 2D/3D.
The SO is Lubuntu 12.04.

In the xorg.conf I tried both Driver "ATI" and "r128", without success. I even re-installed the mesa package twice.

Is there a way to work out the problem?
Thanks.

---

### Post by rkmugen on 2013-05-19
If you want, you can try to just make do with an older version of MESA that lacks EXA acceleration....  just downgrade MESA by using the following files.  Keep in mind, however, that once you do this, you'll get constant nagging from the update manager to update these files.  To get around this, there's a way to "pin" these files in the Synaptic package manager (which isn't installed by default).

Download these items to a folder:
[LIST]
[*=1][http://ports.ubuntu.com/pool/main/m/mesa/libgl1-mesa-dri_7.11-0ubuntu3.2_powerpc.deb](http://ports.ubuntu.com/pool/main/m/mesa/libgl1-mesa-dri_7.11-0ubuntu3.2_powerpc.deb) 
[*=1][http://ports.ubuntu.com/pool/main/m/mesa/libgl1-mesa-glx_7.11-0ubuntu3.2_powerpc.deb](http://ports.ubuntu.com/pool/main/m/mesa/libgl1-mesa-glx_7.11-0ubuntu3.2_powerpc.deb) 
[*=1][http://ports.ubuntu.com/pool/main/m/mesa/libglapi-mesa_7.11-0ubuntu3.2_powerpc.deb](http://ports.ubuntu.com/pool/main/m/mesa/libglapi-mesa_7.11-0ubuntu3.2_powerpc.deb) 
[*=1][http://ports.ubuntu.com/pool/main/m/mesa/libglu1-mesa_7.11-0ubuntu3.2_powerpc.deb](http://ports.ubuntu.com/pool/main/m/mesa/libglu1-mesa_7.11-0ubuntu3.2_powerpc.deb) 
[*=1][http://ports.ubuntu.com/pool/main/m/mesa/libosmesa6_7.11-0ubuntu3.2_powerpc.deb](http://ports.ubuntu.com/pool/main/m/mesa/libosmesa6_7.11-0ubuntu3.2_powerpc.deb) 
[/LIST]
 
Then open up a terminal and navigate to the folder where you saved the above files.

Then type this in the terminal to install them all at once.
```
dpkg -i *.deb
```

After that, you can either reboot or log-out and log-in (probably better if you just reboot).  Then test glxgears to see if that'll improve things...

---

### Post by gioloi66 on 2013-05-19
Just did it, but at the end of the installation it returns an error on package processing:
```
libgl1-mesa-dri_7.11-0ubuntu3.2_powerpc.deb
```

---

### Post by rkmugen on 2013-05-19
Well, if all the other packages installed fine, you should retry to download and install that one package.... (it might have been a corrupted or incomplete download).

---

### Post by este.el.paz on 2013-05-19
> **rkmugen said:**
> Well, if all the other packages installed fine, you should retry to download and install that one package.... (it might have been a corrupted or incomplete download).

@rkmugen:

Nice to see you over on this list . . . adding your support here is great news for ppc users . . . but just wanted to say that "corrupted or incomplete downloads" don't happen on this site . . . .  : - ))))

e.e.p.

---

### Post by Svetlana Tovarisch on 2013-05-19
> **rkmugen said:**
> Svetlana!  We meet again!  And you're still having problems with your iMac... :(

Well, not to steer you away from your Ubuntu adventure, but with Debian 7 (wheezy) now out of "testing", have you considered trying to install that (essentially just plain Debian, no MintPPC or Ubuntu repos)?  Also, just for the sake of completeness and so that we're all on the same page, could you list the most recent distros you've tried and give us an idea of what worked (or didn't work) on your particular iMac G3?  I find it very difficult to understand why it seems like your iMac G3 is the seemingly the only one I've heard of that can run OSX Tiger acceptably well, while seemingly no other version of Linux would even succeed to fully boot into the GUI.

This might be a long shot, but is there any physical damage to the machine or perhaps even the mobo?  Or at least, any that you can determine visually?

I got the machine a few months ago obviously used and with the front feet broken. The CRT makes a weird spring-like noise when turning on and after a while overly dark screens (like a full-on black-background console) appear slightly blue in hue (overloaded CRT?) while anything with less black on it appears fine. The speakers had deteriorated and I replaced them with much cheaper ones (the only I could find that fit the slots after a little bit of etching) and the drive took some lubrication to get working, but other than that the machine seemed to be working fine. The motherboard has no signs of damage to it, and it came with 10.2.8 installed. For a frame of reference, Bugdom (that came with it) and the Flurry wallpaper both run at pretty much the full speed expected from this machine and I can browse the internet with TenFourFox in 10.4.11 without much hassle.

Installing Debian (6 or 7) from scratch then getting the required XFCE packages worked okay-ish but the desktop still suffered from bad lag, it was evident that all rendering was being done in the CPU and Linux just refused to recognize the r128. MintPPC worked a little slower but was a more forward installation, given it comes with packages already installed and ready to work. Ubuntu was the slowest of all, even logging in took a considerable longer time than the other distros (and for some reason logging in from SSH was faster). No settings I changed in the Xorg.conf made it recognize the r128 except for setting the color depth to exactly 16bpp, which made the screen refuse to draw anything but either a black or garbled (static) screen, and SSH while running that seemingly garbled and frozen X session was also very very laggy until I killed the process. (DRI however seemed to accept the card and load AIGLX properly, from the logs.)

I'll try str8bs' guide for the live 13.04 version next time.

---

### Post by Svetlana Tovarisch on 2013-05-19
> **str8bs said:**
> Have you compared performance using FBDEV? Remove the forcePCImode line from the config in post 1 and change "Driver" to FBDEV to see.

As for 12.04 "calling quiesce" hang on yours, I would expect to see the "returning from PROM init". However, it is possible to boot with no framebuffers active and the display  will just stay on that screen until you modprobe a frame buffer.

I have not, but wouldn't that force me to have no acceleration at all? Between acceleration-less (3D or 2D) Linux and OS X 10.4.11, I'll keep the latter.

"returning from PROM init" never happened and the computer just hung there.

Why was Mesa support dropped? Will it ever return, or are we simply forced to use old versions forever? I'd rather have 3D acceleration wherever possible for the Rage 128.

---

### Post by str8bs on 2013-05-20
> **Svetlana Tovarisch said:**
> I have not, but wouldn't that force me to have no acceleration at all? ... Yes
1. I haven't seen anyone report mesa 3d working with 3.2 or later on a PPC with a R128 having less than 16 Meg VRAM. I'm curious if it is all your graphics or separate issues.
2. It could be a bug or related to "thrashing." Just as systems with low ram can have swap/disk thrash issues, the same can happen with "thrashing" in and out of VRAM to system RAM.
3. You mentioned multi-boot. Any chance you are auto-mounting multiple volumes and swap?

> ...Why was Mesa support dropped? Will it ever return, or are we simply forced to use old versions forever? I'd rather have 3D acceleration wherever possible for the Rage 128. [Discussion here.]("http://lists.freedesktop.org/archives/mesa-dev/2011-August/010959.html") Looks like it was causing additional work and the developers didn't see much demand for it. On PPC, the norm seems to be downloading xorg.conf files that make no sense and disable multiple functions. It is reasonable that no demand was seen for PPC at least. I doubt developers spend much time on user forums. I can' t speak with authority on the subject, but here is my take:
It is open source. No one can dictate where a developer spends his/her donated time. There may be some exception to that where FOSS devs are employed by a manufacturer with cards currently on the market such as AMD. I don't know. I would speculate some things that might go into a dev's decision on where to spend time:
1. They have a personal interest in that hardware.
2. They see a large demand and opportunity to serve the community.
3. They have intimate experience with a given hardware set and can easily make changes.

Ironic that R128 is currently better off than newer Radeon and Nouveau cards on PPC. All the current workarounds have them using FBDEV and I don't see many bugs getting reported.

A couple of points:
1. Don't get hung up on GLXgears and numbers. That only tests a few functions and is not a benchmark. Just because a card gets high GLXGears numbers, doesn't mean it will magically be able to run Open Arena.

2. Comparing bugdom or flurry doesn't tell us much either. Bugdom uses QT3 which you may have noticed actually runs faster under OS9 vs. OSX. If OSX gives you what you need, then that is the right choice for you.

3. Determine if you want/need 3d support. It won't make LXDE any faster, but may allow you to run some games and apps that it couldn't otherwise. It will only help applications that use OpenGL. Kubuntu/Ubuntu desktop interfaces make use of accelerated graphics. Since Linux has the capability of "software/CPU" rendering, this can make those seem unfairly slow. OpenGL can greatly improve their performance IF the GPU is up to the task, but it isn't going to make an old G3 with R128 magically run them at speeds comparable to modern hardware. Windows users might be able to relate this analogy: Aero(fancy 3d desktop effects) will refuse to enable with older video cards. With Linux KDE / Unity, etc, you can force the equivalent "on" using software rendering which means the CPU does all the work that was intended for a GPU.

4. Mesa 3d and EXA 2d are two different things. EXA is part of the driver xserver-xorg-video-r128 (which is included with xserver-xorg-video-ati BTW so changing ati/r128 in xorg.conf won't change that fact.) You can add EXA by installing the driver from 12.10 repository or applying the patch. Whether or not you downgrade mesa will not change that. EXA will help with 2D functions like browsing. IE: My daughter runs Xubuntu 12.04 with EXA and mesa 3d on a G3 iMac. This allows it to have decent performance, and run some games/apps that require OpenGL.

@goloi66 I'm not sure why you would need to downgrade libosmesa6. I never have. [See here]("https://wiki.ubuntu.com/PowerPCKnownIssues#A12.04_Precise_Pangolin") under "No userspace.." However, you will probably run in to the same wall Svetlana is on that machine. 

My advice is to experiment with EXA or FBDEV and choose which performs the functions you need the best for you.

Hope that helps.
Str8

---

### Post by imacg3ppc on 2013-05-23
rsavage and str8bs (and others!).. you seem to be the main active authorities on  getting x/k/lubuntu installed on theses g3s. I hope i speak for everyone  in the forum when i say THANK YOU for your great netiquette and your  expertise and the time you spend experimenting and hacking for the  benefit of others and helping us all preserve this old but very capable  and functional hardware. I was very excited to get 'buntu working on my  machines!

---

### Post by Svetlana Tovarisch on 2013-05-24
> **str8bs said:**
> 1. I haven't seen anyone report mesa 3d working with 3.2 or later on a PPC with a R128 having less than 16 Meg VRAM. I'm curious if it is all your graphics or separate issues.
2. It could be a bug or related to "thrashing." Just as systems with low ram can have swap/disk thrash issues, the same can happen with "thrashing" in and out of VRAM to system RAM.
3. You mentioned multi-boot. Any chance you are auto-mounting multiple volumes and swap?


I guess I was unfortunate to get a model with half the expected VRAM, but it was the only one available to me, hrm.
About swap, I did not set a swap partition since I did not have a free partition set up for it (Apple partitioning seems finicky and resizing without formatting was only introduced in 10.5) and I was told since I have 1 GB SDRAM I shouldn't need it that much. I would still prefer not to lose my current OS 9 and OS X installs, so if I really need a swap partition and you could help me resizing the partitions somehow, I'd gladly go through the process. My current partitioning is OS 9, OS X, Linux and Files, give or take the padding Apple's partitioning generates, about 6 GB for each system plus 20 GB for the files partition (40 GB HDD).

> 
 A couple of points:
1. Don't get hung up on GLXgears and numbers. (...)
2. Comparing bugdom or flurry doesn't tell us much either. (...)
3. Determine if you want/need 3d support. (...)
4. Mesa 3d and EXA 2d are two different things.


I do understand that the 2D and 3D accelerations are different, and that just the FPS on a simple test shouldn't be taken as end-all benchmarking, but I just figured my iMac should be able to support -some- sort of 3D/OpenGL, given its performance on similar applications under OS X. I want to move from OS X to avoid being stuck with old, unsupported software, but I'd still like to be able to use my machine's hardware to the fullest. At the moment I haven't been able to run a Linux DE which didn't slow down when I did so much as dragging a big selection rectangle on the desktop (XFCE and LXDE), while the same machine is able to run OS X smoothly, so there doesn't seem to be anything that should be keeping me from having a reasonable Linux experience with it.

If you have any more questions about my machine feel free to ask, and thank you very much for taking the time to help me.

---

### Post by rkmugen on 2013-06-08
I'm currently alternating between 12.04 and 13.04 (doing complete wipes and reinstalls on my hard drive.... for simplicity's sake, I don't bother with dual-boot configs).

Is there any way to get the newest version of the xserver-xorg-video-r128 (version 6.9.1) with -both- EXA and XXA on both 12.04 and 13.04?  I'd gladly compile it myself, but i have no idea how to do it, nor do I have any idea of how to be absolutley certain that the source code I'm using would indeed include the latest additions by Connor Behan ([http://cgit.freedesktop.org/xorg/driver/xf86-video-r128/commit/?id=aca6aa127f43deeed42c4d3bef8d1e6a735b4c50](http://cgit.freedesktop.org/xorg/driver/xf86-video-r128/commit/?id=aca6aa127f43deeed42c4d3bef8d1e6a735b4c50)).  I really wish there was a step-by-step guide of how to install it since I get stuck after downloading the .tar.gz file and decompressing it.... i'm like, "now what?"  I have no idea why ```
sudo ./configure
``` didn't work.... maybe I'm missing files or even some other intermediate steps that I don't know about?

Also, could anyone here tell if the package provided in the first post by rsavage is compiled with the EXA and XXA flags both enabled?
[QUOTE=rsavage]6.  If you are using 12.04 then you can download the mesa legacy package  to give you 3D acceleration.  You can find a pre-compiled version here [http://ubuntuone.com/379TLoe7yo2IAiOijAsOjQ](http://ubuntuone.com/379TLoe7yo2IAiOijAsOjQ)[/QUOTE]

---

### Post by vinyl_2000 on 2013-12-07
[SIZE=2]I have the exact same computer a [Svetlana Tovarisch]("http://ubuntuforums.org/member.php?u=1801859")[COLOR=#000000] and exactly the same problems, (i have read the hole thread)

What should we do now? 

Thanks in advance![/COLOR][/SIZE]

---

### Post by Chris_Tillman on 2014-03-07
I finally got my iMac G3 working with the 3.2 kernel, and wantd to share my xorg.conf. Key settings, I believe, are DefaultDepth 16 (didn't work with 24), NoAccel "true", and UseFBDev "true".

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "extmod"
    Load  "record"
    Load  "dbe"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
        HorizSync 58-62
        VertRefresh 75-117
        ModeLine "1024x768" 78.5  1024 1045 1141 1312 768 769 772 796 +hsync +vsync
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
    Option     "NoAccel"      "True"
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "ForcePCIMode"           # [<bool>]
        #Option     "CCEPIOMode"             # [<bool>]
        #Option     "CCENoSecurity"          # [<bool>]
        #Option     "CCEusecTimeout"         # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>      
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "Display"                # <str>
        #Option     "PanelWidth"             # <i>
        #Option     "PanelHeight"            # <i>
        #Option     "ProgramFPRegs"          # [<bool>]
    Option     "UseFBDev"       "True"
        #Option     "VideoKey"               # <i>
        #Option     "ShowCache"              # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
    Identifier  "Rage 128"
    Driver      "ati"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
        DefaultDepth 16
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


uname -a 
Linux debian 3.2.0-4-powerpc-smp #1 SMP Debian 3.2.54-2 ppc GNU/Linux


lspci
0000:00:0b.0 Host bridge: Apple Inc. UniNorth/Pangea AGP
0000:00:10.0 Display controller: Advanced Micro Devices [AMD] nee ATI Rage 128 Pro Ultra TR
0001:10:0b.0 Host bridge: Apple Inc. UniNorth/Pangea PCI
0001:10:17.0 Unassigned class [ff00]: Apple Inc. KeyLargo/Pangea Mac I/O
0001:10:18.0 USB controller: Apple Inc. KeyLargo/Pangea USB
0001:10:19.0 USB controller: Apple Inc. KeyLargo/Pangea USB
0002:20:0b.0 Host bridge: Apple Inc. UniNorth/Pangea Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Apple Inc. UniNorth/Pangea FireWire
0002:20:0f.0 Ethernet controller: Apple Inc. UniNorth/Pangea GMAC (Sun GEM)

Chris

---


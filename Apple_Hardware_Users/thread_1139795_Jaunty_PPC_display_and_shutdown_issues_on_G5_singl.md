---
title: "Jaunty PPC display and shutdown issues on G5 single"
date: 2009-04-27
forum: Apple Hardware Users
---

### Post by casbahdk on 2009-04-27
After install, the icons, desktop were almost normal resolution. Since then, the display has deteriorated and icons, panel etc. look like a little grainy and like a nightmare cross between Kubuntu and the Ubuntu Human theme with all sorts of brown-orange all over the place, with some baby blue added. What is up with that?

Second problem. KJaunty doesn't seem to shutdown properly. Nothing happens for five minutes, everything is blacked out except for the cursor which I can still move around. Ctrl Alt Delete doesn't work either, so I have to force quit using the power button on my G5. what log do I take a peek in to find out what is going wrong?

Cheers

---

### Post by tiresia on 2009-04-27
Does your PowerPC have a Dual Processor? Can you post more info about your hardware (grafic card...)?

---

### Post by casbahdk on 2009-04-27
> **tiresia said:**
> Does your PowerPC have a Dual Processor? Can you post more info about your hardware (grafic card...)?

Hi again :-)

My G5 has a single 1.8 GHz. processor. Here is the graphics info:

```
GeForce FX 5200:

  Chipset Model:	GeForce FX 5200
  Type:	Display
  Bus:	AGP
  Slot:	AGP
  VRAM (Total):	64 MB
  Vendor:	NVIDIA (0x10de)
  Device ID:	0x0321
  Revision ID:	0x00b1
  ROM Revision:	2060
  Displays:
SyncMaster:
  Resolution:	1280 x 1024 @ 60 Hz
  Depth:	32-bit Color
  Core Image:	Hardware Accelerated
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported
Display Connector:
  Status:	No display connected
```

---

### Post by tiresia on 2009-04-27
I haven't tried it yet - also because I don't have any problem until now, but have you read this thread?
[http://ubuntuforums.org/showthread.php?t=1137500](http://ubuntuforums.org/showthread.php?t=1137500)

---

### Post by stream303 on 2009-04-27
That will make a GREAT PowerMac box for Ubuntu, as it has a single drive controller, and has an nvidia graphics card which will make configuring it a lot easier.

The most important thing is to find the specs for your Syncmaster monitor.

The first thing I'd do is to modify your existing /etc/X11/xorg.conf and make the DEVICE section look somewhat like this:

You can make a backup and edit this in a terminal with:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

sudo nano /etc/X11/xorg.conf
(or with ubuntu graphically:)
gksudo gedit /etc/X11/xorg.conf
```

```
Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:240:16:0"
        Driver         "nv"
EndSection
```

Your BUSID will probably be different than mine, if it is included at all.  If it isn't there, forget about it for now.

I like to manually specify the "nv" driver, which will make it easier if you later decide to try the "nouveau" driver instead - but for now get the standard nv driver working.

For the monitor section, find out your vertical and horizontal specs on that Syncmaster.  From what I've seen so far, you could try this:

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync      30-82
        VertRefresh    58-62
EndSection
```

Again, these values are dependent on your actual Syncmaster's specs.  Don't put quotes around the frequencies.

I'd suggest starting out at no more than 24 bit color depth and manually specifying the resolution.  Something like this may be appropriate:

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
           SubSection       "Display"
             Depth            24
             Modes             "1280x1024"
           EndSubSection
EndSection
```

Don't put quotes around the color depths.

Then logout and log back in to see the results (or just restart)

That will be a great Jaunty-ppc powermac once the external display is taken care of.

---

### Post by casbahdk on 2009-04-27
> **tiresia said:**
> I haven't tried it yet - also because I don't have any problem until now, but have you read this thread?
[http://ubuntuforums.org/showthread.php?t=1137500](http://ubuntuforums.org/showthread.php?t=1137500)

I just noticed that I only have a problem with restart. Shutdown works fine.

---

### Post by stream303 on 2009-04-27
Off the top of my head, I'd take a peek and see if there are any processes that seem to be hung with top  (or my favorite, htop)

It could be a Kubuntu thing that might get taken care of with updates.  Do you have anything hanging off the usb ports like another hard drive etc?

---

### Post by casbahdk on 2009-04-27
> **stream303 said:**
> Off the top of my head, I'd take a peek and see if there are any processes that seem to be hung with top  (or my favorite, htop)

It could be a Kubuntu thing that might get taken care of with updates.  Do you have anything hanging off the usb ports like another hard drive etc?

Everything is blacked out. I can't see anything. Would those things be in a log someplace even if I had to force quit?

---

### Post by casbahdk on 2009-04-27
> **stream303 said:**
> That will make a GREAT PowerMac box for Ubuntu, as it has a single drive controller, and has an nvidia graphics card which will make configuring it a lot easier.

The most important thing is to find the specs for your Syncmaster monitor.

The first thing I'd do is to modify your existing /etc/X11/xorg.conf and make the DEVICE section look somewhat like this:

You can make a backup and edit this in a terminal with:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

sudo nano /etc/X11/xorg.conf
(or with ubuntu graphically:)
gksudo gedit /etc/X11/xorg.conf
```

```
Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:240:16:0"
        Driver         "nv"
EndSection
```

Your BUSID will probably be different than mine, if it is included at all.  If it isn't there, forget about it for now.

I like to manually specify the "nv" driver, which will make it easier if you later decide to try the "nouveau" driver instead - but for now get the standard nv driver working.

For the monitor section, find out your vertical and horizontal specs on that Syncmaster.  From what I've seen so far, you could try this:

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync      30-82
        VertRefresh    58-62
EndSection
```

Again, these values are dependent on your actual Syncmaster's specs.  Don't put quotes around the frequencies.

I'd suggest starting out at no more than 24 bit color depth and manually specifying the resolution.  Something like this may be appropriate:

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
           SubSection       "Display"
             Depth            24
             Modes             "1280x1024"
           EndSubSection
EndSection
```

Don't put quotes around the color depths.

Then logout and log back in to see the results (or just restart)

That will be a great Jaunty-ppc powermac once the external display is taken care of.

I installed the nouveau driver as per the thread, before you replied. There is no change, as another has noted on the thread. glxgears seems to give good performance but is totally discolored. Here is what I have been able to find out about the SyncMaster 930BF.

This info came from Cnet:
General
 Display Type LCD display / TFT active matrix
 Width 16.9 in
 Depth 7.9 in
 Height 16.7 in
 Weight 11.2 lbs
 Enclosure Color Black

Display
 Diagonal Size 19 in
 Viewable Size 19 in
 Dot Pitch / Pixel Pitch 0.294 mm
 Max Resolution 1280 x 1024
 Color Support Up to 16.2 million colors
 Max Sync Rate (V x H) 75 Hz x 81 KHz
 Video Bandwidth 140 MHz
 Response Time 4 ms
 Video Output None
 Signal Input DVI-D, VGA
 Features MagicBright, MagicTune, MagicColo

Here is what an earlier version of System Profiler reported in OS X:

Displays:
SyncMaster:
  Resolution:	1280 x 1024 @ 75 Hz (refresh rate 75 H)
(canning frequency of 30-81kHz horizontal and 56-75Hz vertical)
  Depth:	16-bit Color
  Core Image:	Supported
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported
Display:
  Status:	No display connected

---

### Post by stream303 on 2009-04-27
Ok, that info is similar to the Samsung 930bf manual, but now we can fine tune it:

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync      30-81
        VertRefresh    56-75
EndSection
```

Let's take it a bit further and fine tune our own modeline bypassing hal by running this calculation and seeing what it turns out:

```
gtf 1280 1024 60
```

Manual states that 60hz is optimal, and 75 hz is maximum, so you can play with this calculation.  The above calculates a modeline value and let's put this in the Monitor section

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync      30-81
        VertRefresh    56-75
        **Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync**
EndSection
```

(Be sure to keep your + and - signs proper on the sync values!)

And now a quick change to the Screen section:

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
           SubSection       "Display"
             Depth            24
             **Modes             "1280x1024_60"**
           EndSubSection
EndSection
```

I'm also not sure if you are running straight vga, or using a vga-dvi converter.  In addition, I'd have to check that the nvidia card we're using will support 1280x1024 in the first place. :)  Oops - duh, if it is working in OSX in 1280x1024 for sure, then nevermind...

btw, for a quick edit, can you get to a virtual terminal via CTRL-ALT-F2 to login and get to an editor that way?

On a related note, is the video card in the original slot, or has it been moved?  I've heard of issues about being in the wrong slot, but since I don't own one, I can't say for sure.

---

### Post by stream303 on 2009-04-27
One other thing:

Are you booting without that Ubuntu splash screen?

Although it is still unusable for 99.999% of the ppc boxes out there, unfortunately it is not always benign and can throw some cards into a catatonic state before they even reach X.

At the second-stage yaboot boot: prompt, hit TAB and then enter

```
Linux nosplash
```

It will then continue on without that card-confusing splash screen.  You can make this change permanent in your /etc/yaboot.conf as detailed in the wikis and elsewhere, but let's see if we can also take the splashscreen out of the question.

---

### Post by casbahdk on 2009-04-28
> **stream303 said:**
> 
And now a quick change to the Screen section:

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
           SubSection       "Display"
             Depth            24
             **Modes             "1280x1024_60"**
           EndSubSection
EndSection
```

OK, I have changed everything except for the "screen" section. I haven't changed that yet as mine only has the first three lines. Are "DefaultDepth" and "Depth" the amount of bits? Everything I have states that my SyncMaster can only do 16-bit color.

BTW, "shutdown" froze this last time as well. I will try the nosplash command at next boot.

---

### Post by stream303 on 2009-04-28
I don't know why OSX is reporting only 16-bit color depths.  Both your card and monitor are easily capable of 24-bit color.  Maybe for some reason at that 1280 x 1024 resolution it thinks it can only do 16?

If you'd like you can easily change those depth values to 16 to start out with, and if it all works change them to 24.

I've seen some reports about long shutdown or lockups elsewhere here - in addition something new to me is that my backlight won't shut off, nor does it respond to my old xset commands, so there are still a few rough edges out there.

In the meantime, does it make any difference time-wise if you shutdown from the cli, ie:

```
sudo shutdown -h now
```

in either a terminal, or perhaps even try using a virtual terminal (CTRL-ALT-F2), login and issue that shutdown command.

Perhaps we can at least find a way to shut down cleanly until they find the bug...

---

### Post by casbahdk on 2009-04-28
> **stream303 said:**
> I don't know why OSX is reporting only 16-bit color depths.  Both your card and monitor are easily capable of 24-bit color.  Maybe for some reason at that 1280 x 1024 resolution it thinks it can only do 16?

If you'd like you can easily change those depth values to 16 to start out with, and if it all works change them to 24.

I've seen some reports about long shutdown or lockups elsewhere here - in addition something new to me is that my backlight won't shut off, nor does it respond to my old xset commands, so there are still a few rough edges out there.

In the meantime, does it make any difference time-wise if you shutdown from the cli, ie:

```
sudo shutdown -h now
```

in either a terminal, or perhaps even try using a virtual terminal (CTRL-ALT-F2), login and issue that shutdown command.

Perhaps we can at least find a way to shut down cleanly until they find the bug...

OK, I have completed changes to depth and driver. Unfortunately, there is no change in the way Kubuntu looks. Here is my full xorg.conf:

```
Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:240:16:0"
	Driver          "nouveau"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync      30-81
        VertRefresh    56-75
        Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth    24
           SubSection       "Display"
             Depth            24
             Modes             "1280x1024_60"
           EndSubSection
EndSection

```

Interesting. I can't get any virtual terminal at all (CTRL-ALT-F2, F3, F4, etc.). The shutdown command worked.

Cheers

---

### Post by stream303 on 2009-04-28
Wow - frustrating for sure.  At least the shutdown command helps. :)

Make sure that your pci BusID is correct for your machine and you aren't using my settings - although they might be the same.

I noticed you put in the nouveau driver instead of nv in your last example.  Did you actually install the xserver-xorg-video-nouveau driver via synaptic, or did you just change it only in xorg.conf?  That actually might be worth a shot trying, since nouveau actually works on my G5.

And it may be a total longshot, but have you tried pushing your monitor's auto-adjust button?  I normally do this anytime I change things in xorg.conf, even if it appears to be ok and I can see very minute improvements in font rendering etc.  It couldn't hurt.

And, if all else fails you can take a step back to Kubuntu Intrepid 8.10, which was actually pretty nice for ppc.  Or even go back to 8.04 LTS - at least as a possible diagnostic - perhaps there is something in the Kubuntu 9.04 ppc release that is giving you problems - you could try the regular Ubuntu 9.04 and see what turns up that way.  Hope you have a few blank cd's handy. :)

Well, I was hoping we could nail it down, but looks like more research or maybe someone else can spot something obviously wrong....whatever you do, don't throw the PowerMac through the window. :)

---

### Post by casbahdk on 2009-04-28
I used the BusID already in my xorg.conf file. Not sure how to check if the BusID is correct.

I installed the nouveau driver with aptitude. I didn't do any configuration of the driver.

I get the message that auto adjustment isn't available :-( Guess I'll try Ubuntu 9.04 and then Kubuntu 8.10 Intrepid PPC if I can find the link. I found Hardy, but no Intrepid link.

If I was going to throw the G5 through a window, I would have done it a long time ago ;-)

Thanks for taking the time to walk me through all of this :-))

---

### Post by casbahdk on 2009-04-28
I opted for installing Debian Lenny with KDE as I know there will be an upgrade path to KDE 4. Now to figure out how to get the "restricted extras" installed that 'buntu makes so easy :-(

---

### Post by stream303 on 2009-04-28
Trying Debian Lenny is an excellent choice!

I've run it very successfully on my G5.  What makes it even nicer is that if one is interested in a binary blob-free kernel, they are now available for PPC as well as the usual X86 and AMD64 architectures!

[http://lists.debian.org/debian-devel-announce/2009/04/msg00010.html](http://lists.debian.org/debian-devel-announce/2009/04/msg00010.html)

Considering that on our PPC boxes, we aren't running any proprietary video drivers, and now with nouveau sweetening the deal over the old nv driver, along with a new libre-kernel, it's the closest thing we'll get to a free setup (as in FSF guideline), as long as one doesn't activate the restricted or non-free repos.

I'm running the above on my Lenny Testing X86_64 box actually as of last night.

Anyway, Debian is a very good choice and you can take what you've learned here and apply that to Debian if need be.

---

### Post by casbahdk on 2009-04-29
> **stream303 said:**
> Considering that on our PPC boxes, we aren't running any proprietary video drivers, and now with nouveau sweetening the deal over the old nv driver, along with a new libre-kernel, it's the closest thing we'll get to a free setup (as in FSF guideline), as long as one doesn't activate the restricted or non-free repos.

I'm running the above on my Lenny Testing X86_64 box actually as of last night.

Anyway, Debian is a very good choice and you can take what you've learned here and apply that to Debian if need be.

How did you get nouveau in Lenny? I haven't been able to find it. As for the libre kernel, it is something to consider, but it would be nice to know what capabilities PPC users loose with the libre kernel and how the kernel needs to be installed.

---

### Post by stream303 on 2009-04-29
> **casbahdk said:**
> How did you get nouveau in Lenny? I haven't been able to find it.

Actually it is in SID, and I'm only running Testing/Squeeze at the moment - on an amd64.  When Nouveua arrives in Testing, I'll put it on my G5 and dual boot with Ubuntu 9.04.  It works just fine with Arch Linux too.

> As for the libre kernel, it is something to consider, but it would be nice to know what capabilities PPC users loose with the libre kernel and how the kernel needs to be installed.

I don't think we'd lose much unless you have some hardware that relies on those binary blobs.  Looking through the list of what is culled, a standard ppc user won't be using them anyway!  And installation (as far as Debian goes) is to just add the repo to your software sources, download the kernel with apt-get or synaptic, and reboot - perhaps keeping an eye on /etc/yaboot.conf to make sure.

PPC boxes make fine free-software environments because by it's very nature, we don't have proprietary video drivers, we don't rely on flash, nv was ok for nvidia, but now there's an option with nouveau, wireless can be taken care of with usb wireless sticks, and you can run a clean kernel.  Pretty close to ideal, although the mere ease with which one can activate non-free repos may put off fsf-purists.  At least we're making progress.

(Of course doing all this and enabling non-free repos makes the whole exercise pointless - but I'm smart enough not to do this, a big fear amongst fsf-purists that some aren't bright enough to discern the difference. :) )

I'd love to see a libre-kernel for Ubuntu PPC at least just made available.  I'd drop one in right now, but I'm too lazy to scrub it myself and the other repos only have i386 versions usually.

---

### Post by casbahdk on 2009-04-30
Are the Kubuntu Jaunty PPC display issues a known bug?

---

### Post by stream303 on 2009-04-30
That would be hard to say until more reports start filing in.  You'd have to scour Launchpad bug reports for Kubuntu ppc.

Here's a thought - as unofficially-supported ports go like ppc, Ubuntu gets the most resources devoted to it, as thin as they are.  Kubuntu and Xubuntu ppc get even less.  In fact, you'll see that both Kubuntu and Xubuntu have skipped some releases altogether.

So, in this instance for a quickie test, would be to install Ubuntu to see if you can gain control of your graphics.  Then, install the kubuntu-desktop and switch to it at the gdm session login option and see.  If all is well, you could then remove ubuntu-desktop (usually with some scripts, not just removal via synaptic) and be back at a working Kubuntu.  It's a long way around to be sure.  BUT, you might have better leverage stating that the exact same setup for graphics works with Ubuntu and something may be different with Kubuntu's default.

It is a lot of legwork, but doing stuff like this is part and parcel of U/K/Xubuntu life. :)

Does your system currently work with Debian Lenny?  If so, does it still work with Testing/Squeeze?  Then, does it work with SID?  The reason I mention this is that Ubuntu relies heavily on Debian upstream, so there might be some relationship there.

Example - when the nv driver offset issue first surfaced for me, I reported it to Launchpad.  Which led me to upstream Debian.  Which then led me all the way up to freedesktop.org.  It took awhile to discover that the bug for me is a fix for others with geometry problems, and will most likely not be reverted.  So it has nothing to do with Ubuntu or Debian but goes all the way upstream.

So you may end up doing a lot of legwork only to discover that with your particular combination of hardware, it may be due to xorg issues - but with ppc hardware, bug reports have to be very detailed, otherwise they can be dismissed as not doing the proper post-configuration manually as is usually needed with Apple hardware.  So one ends up in a loop so to speak, and you just scour the net and forums for solutions from other users.

Whew.  Long way to say don't hold your breath and jump in and repartiton that box 50 times until you find the right combo. :)

---

### Post by casbahdk on 2009-04-30
I was just being civic minded. If you don't know the bug is there it is kind of hard to fix it :-))

I am a newbie, so if it isn't broken, I usually don't try to fix it :-) If there are serious problems like there were in the past with G5's and the windfarm modules, then I usually try to move on to another distro.

I just uninstalled gnash and got my sound back (don't ask, I don't know), so if I can get the other things sorted out, I will probably just stick with Lenny, at least until the Kubuntu issue gets sorted. What can I say, I am a 'buntu fan.

On the sound front, I just put on some old Crosby, Stills and Nash and discovered that my G5 sounds muuuuch better with Lenny than under OS X Leopard. Who would have thought?

---

### Post by stream303 on 2009-04-30
Yeah, sorry about that.  I can get very long-winded at times.  I have to watch it so that passion for Linux on ppc doesn't turn into obsession. :)

---

### Post by casbahdk on 2009-04-30
> **stream303 said:**
> Yeah, sorry about that.  I can get very long-winded at times.  I have to watch it so that passion for Linux on ppc doesn't turn into obsession. :)
No worries :)

---

### Post by stream303 on 2009-05-02
BTW, back to the shutdown issue, there might be an issue with the new shutdown delay dialog (or perhaps something else,) but for now this may prove useful when shutting down via the gui to go back to the old way:

In the user-switcher applet where one now initiates a shutdown, right-click it to bring up the preferences.

Uncheck "confirm dialogs for logout, restart, or shutdown".

The only problem is that if this shutdown delay is now being relied on to shutdown cleanly while waiting for some other process to finish, it may not be advisable in the long term.  Hard to say, but for now appears to be a viable short-term solution other than going into a cli and doing the shutdown command manually.

I'll have to keep an eye on how this develops.

---

### Post by casbahdk on 2009-05-04
> **stream303 said:**
> Here's a thought - as unofficially-supported ports go like ppc, Ubuntu gets the most resources devoted to it, as thin as they are.  Kubuntu and Xubuntu ppc get even less.  In fact, you'll see that both Kubuntu and Xubuntu have skipped some releases altogether.

So, in this instance for a quickie test, would be to install Ubuntu to see if you can gain control of your graphics.  Then, install the kubuntu-desktop and switch to it at the gdm session login option and see.  If all is well, you could then remove ubuntu-desktop (usually with some scripts, not just removal via synaptic) and be back at a working Kubuntu.  It's a long way around to be sure.  BUT, you might have better leverage stating that the exact same setup for graphics works with Ubuntu and something may be different with Kubuntu's default.

One thing I could try is to download the Ubuntu PPC Alternate Install CD, do an F4 and choose to install a command-line system. Then when I reboot the computer I will just have to do a

```
$ sudo apt-get install xorg kwin kubuntu-desktop kscreensavers
```

and there should be a Kubuntu system.

---

### Post by stream303 on 2009-05-04
> **casbahdk said:**
> One thing I could try is to download the Ubuntu PPC Alternate Install CD, do an F4 and choose to install a command-line system

That's an outstanding way to install if one wants to build up their system with total control!  Highly recommended for low-memory macs 64-128mb too.  This might prove useful for those who want to do it that way:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Even though it seems specific to the X86 architecture, the overall instructions work for ppc as well.  Might need a little bit of updating, but the basics are there.

AND if one want to go that route, the **netinstall** method is pretty nice, where you download only a minimal ppc boot iso, and grab the latest from the net during installation:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It looks like a link is missing for 64-bit Jaunty ppc, but there is one available if you go to the repo and directory structure yourself.

---

### Post by casbahdk on 2009-05-06
OK; this is what I did. I installed a system using the "minimal server" option on the Minimal Install CD. When the system booted for the first time, I did the following, it may have been a little pedantic, but anyway:

```
sudo aptitude update

sudo aptitude upgrade

sudo aptitude install xorg

sudo aptitude install --without-recommends kdm

sudo aptitude install --without-recommends lxde

startx
```

Then in LXDE I did a:

```
sudo aptitude install konqueror
```

Everything looks fine so far (except for the system not rebooting from the GUI). What should my next step be?

---

### Post by stream303 on 2009-05-06
Well, just know that you are now using the server-kernel - which is ok for casual use, but later on you might want to switch to the desktop kernel.  Not a big issue at this point.

Since you started out with aptitude rather than apt-get to install your packages from the commandline, stick to aptitude and don't mix aptitude and apt-get.  Flamewars about the pros/cons of both can be found elsewhere. :)

Since you are bringing up LXDE with *startx* that means that you are not using a login-manager such as KDM.  Startx looks for a hidden file in your home directory on what to start. (~/.xinitrc)  Look inside it.

If you were to install KDM, GDM, XDM or some other login manager, you won't need to use the older startx method.  Since your goal is KDE, perhaps KDM would be the best choice.

But the real question is that you say everything looks good in LXDE right now???  If so, that's great - just add a login manager like KDM and set KDE for the default.  You may want to add *synaptic* to start adding packages back from a gui instead of using aptitude in a terminal.

If the display still doesn't look good that means that you'll have to manually configure X, and in this case I'd recommend using a window-manager until you get xorg.conf figured out, but first is your display really ok now?

---

### Post by casbahdk on 2009-05-06
I only used startx the first time. KDM is installed and now the GUI starts automatically.

Noted about aptitude.

KDE is not installed. Only the bits that I have mentioned. I first tried installing "kubuntu-desktop the first time I ran the minimal install and the problem was still there. I have been thinking that maybe I should try to continue adding KDE bits until the display starts messing up, but I am not sure how to do that and still run LXDE.

Maybe I should start by switching to a desktop kernel to see if the problem lies there? How do I do that?

Cheers

---

### Post by stream303 on 2009-05-06
Before you do anything else - do not pass go:

Write down or save your existing /etc/X11/xorg.conf file OFF THE MACHINE.  :)

It wouldn't be a bad idea to write or save your /etc/yaboot.conf too.

At the very minimum, make backups:

```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak

and

sudo cp /etc/yaboot.conf  /etc/yaboot.conf.bak
```

As for finishing up with installing the rest of KDE, check out this faq:

[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

Looks like you may need kubuntu-default-settings installed also.

Since I'm not a KDE fan, I don't have experience with those, but this should really help I'm sure.

I'd save the desktop kernel issue until you have everything else up and running nicely.  You can find the kernel in synaptic by searching for linux-image.  You'll also see linux-headers too.

What I have checked off in synaptic for my single-cpu G5 is:

linux-image-2.6.28-6-powerpc64-smp
and
linux-image-powerpc64-smp

You may also want to get the matching linux-headers too.

But for now, get the rest going. :)

---

### Post by casbahdk on 2009-05-07
Interesting. I just did a

```
sudo aptitude install kde-core
```

rebooted, chose a KDE session and the icons, theme, etc. are all messed up again as with a Kubuntu PPC Jaunty install. A KDE/Openbox session has the same problem. A reboot into an LXDE session gives me a normal looking display again. Weird.

---

### Post by stream303 on 2009-05-07
Oh man that's frustrating.

While you are testing, be sure to install **cpudyn** as a cpu-frequency scaler, since none come installed by default in Jaunty, and you actually save about 10 watts at the ac outlet (as measured here on my box that is.  Lopp another 2 watts off by not having a blinking cursor by going into keyboard prefs and unchecking the blink.  12 watts may not seem like much at first, but anything to keep your power supply happy....

At this stage, if you can't find a resolution to the KDE issue with Kubuntu - you may want to try Debian Lenny's KDE:

[http://debian.org/distrib/](http://debian.org/distrib/)

Look for the powerpc distro - stable is "Lenny", although you might just want to start off with "testing".  Either a full download of the KDE-1 cd, or netinstall (you just need the first cd, not the whole series)

Everything you've done here is just as applicable to Debian, and perhaps their KDE offering won't have this weird problem.

---

### Post by casbahdk on 2009-05-09
> **stream303 said:**
> Trying Debian Lenny is an excellent choice!

I've run it very successfully on my G5.  What makes it even nicer is that if one is interested in a binary blob-free kernel, they are now available for PPC as well as the usual X86 and AMD64 architectures!

[http://lists.debian.org/debian-devel-announce/2009/04/msg00010.html](http://lists.debian.org/debian-devel-announce/2009/04/msg00010.html)

Considering that on our PPC boxes, we aren't running any proprietary video drivers, and now with nouveau sweetening the deal over the old nv driver, along with a new libre-kernel, it's the closest thing we'll get to a free setup (as in FSF guideline), as long as one doesn't activate the restricted or non-free repos.

I'm running the above on my Lenny Testing X86_64 box actually as of last night.

Anyway, Debian is a very good choice and you can take what you've learned here and apply that to Debian if need be.

OK, I have installed Synaptic and have added the repository. I downloaded the key, but am unsure how to install it.

---

### Post by stream303 on 2009-05-10
As for the authentication key, I just highlighted all the lines starting and ending with:

> ---BEGIN PGP PUBLIC KEY BLOCK ---
..
..all the rest here.....
..
---END PGP PUBLIC KEY BLOCK ---

Now that it is highlighted, right click to copy the highlighted selection.

Fire up an editor like gedit (text-edit), and paste.

Save this file as something like *debkey*

Now in your software sources authentication tab, just IMPORT that file.

You've already added the deb repo so you should be all set to go if you RELOAD the repositories, or just do an apt-get update from the terminal (as root in Debian of course)

Fire up Synaptic again, and look for:

linux-image-2.6.26-libre2-2-powerpc64

Install and reboot.  Run uname -a afterwards to see the change.

I didn't install the matching headers since for some reason I still have a dependency issue, and I'd need those for custom compiles - but for now it is a nice quick fix.

I sure wish UBUNTU would just put a free kernel in the repos.  I tried this Debian libre kernel in 9.04 and for the most part it worked, but didn't seem ideal as I ran into some small problems with it.

C'MON UBUNTU - some of us would love to add a free kernel if it was made available!!!  I'm already running a mostly free system anyway what with nouveau, 2D nv driver etc - ..

Ok, rant over. :)

---

### Post by casbahdk on 2009-05-10
> **stream303 said:**
> Fire up an editor like gedit (text-edit), and paste.

Save this file as something like *debkey*

Now in your software sources authentication tab, just IMPORT that file.

You've already added the deb repo so you should be all set to go if you RELOAD the repositories, or just do an apt-get update from the terminal (as root in Debian of course)

Fire up Synaptic again, and look for:

linux-image-2.6.26-libre2-2-powerpc64

Install and reboot.  Run uname -a afterwards to see the change.

OK, how to get the key wasn't a problem, I should have specified that I downloaded it. My problem is that I can't find any "software sources authentication tab" or anything else, in either Synaptic or Kpackage to add the key to. Clicking the file brought up Kgpg, but that didn't seem to make the error message that I get go away.

I still wish there was some information about what functionality is lost when using the libre kernel. I seem to remember that there is a new Ubuntu derivative that runs only software bits and bobs that are cleared by Richard Stahlman's org. Just found the URL:

[http://www.gnewsense.org/]("http://www.gnewsense.org/")

---

### Post by stream303 on 2009-05-10
We don't actually miss anything typically with the libre-kernel, since the code removed is for the hardware that isn't usually on our machine.  However, it is an ethical thing.  Actually, yes, you will NOT have Broadcom-drive airport and airport extreme wireless support.  One must use a usb-stick wireless or other replacement.

I run quite a few distros on ppc attempting to roll my own free-as-in-freedom distro, especially since we are already 99% there just due to our hardware alone. :)

Hang tight for a gNewSense ppc.  Work is being done.

---


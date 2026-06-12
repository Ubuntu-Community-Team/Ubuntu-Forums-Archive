---
title: "Last ditch attempt before I switch off Ubuntu for good."
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Inquisitr on 2007-11-05
More or less this is the last thing I'm going to post, if I can't get help this time, I'm sorry but I can't stay with Ubuntu.

I've been trying to get dual monitors working since 7.10 came out.  I have a Radeon 9700 pro.  It's a dual head video card and getting dual monitors working shouldn't be something I have to fight with for days and days, this is something that should just work out of the box .

I digress tho.

I've followed every howto I can find in these forums, like 4 by Xire, The official how to, 3 ways to get proprietary drivers working, Xinerama, big desktop, I've googled it, more or less everything I can try.

I posted in the multimedia forums, but I was ignored quite vigorously.

I've reinstalled Ubuntu 10 times now from messing it up trying this, and if I have to reinstall an OS again it will not be Ubuntu.

More or less, I'm begging here.  I've enjoyed Ubuntu since I installed Fiesty, but if I really can't get dual monitors working I can't keep it.

Here is the relevant section of my xorg.conf

[http://ubuntuforums.org/showthread.php?t=602555](http://ubuntuforums.org/showthread.php?t=602555)
```

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

All I hear about is how awesome the Ubuntu community is.  Well so far I've been ignored and ignored and ignored.  So yeah, I'm begging here,

It's been a frustrating time.

---

### Post by jfinkels on 2007-11-05
Have you tried getting it working with the proprietary ATI driver, "fglrx"? Here's some info: [http://ubuntuforums.org/showthread.php?t=301941&highlight=ATI+x800XL](http://ubuntuforums.org/showthread.php?t=301941&highlight=ATI+x800XL) and [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Inquisitr on 2007-11-05
I have tried both of those methods, and they did not work.  With fglrx I load the restricted driver, reboot the computer, and get put in crappy graphics mode.  I forget the exact text but it's something alogn the lines of it can't detect something and I need to enter in the setting manually.  Then I can't change the resolution or get dual monitors working

Ziox's method literally just made linux freak out and I had no choice but to redo it.

---

### Post by jfinkels on 2007-11-05
I suppose it must be some specific, outlying hardware bug. Have you searched to see if your other hardware has given people problems, maybe the motherboard, chipset, various other controllers (although these shouldn't affect this problem in any way...)?

The exact text of the error messages will be VERY helpful to potential problem-solvers on these forums, if you can get them.

---

### Post by jfinkels on 2007-11-05
Also, have you tried the most recent drivers at ati.amd.com? There should be some for your card here [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by Inquisitr on 2007-11-05
I don't think I buy that.

I had both compiz and dual monitors working in fiesty.  Compiz broke when I upgraded to 7.10, but dual monitors worked so I didn't mind as compiz is nice but just fluff really.

Then one day You tube broke, I could watch other movie sites, but for some reason youtube would come up as a white blank space, which was really freaky because barely an hour before I had watched a movie fine in it.

So I broke down and figured I'd do it over, and ever since I haven't been able to get dual monitors working at all.

It's not hardware because when I boot into XP everything works fine, dual monitors, WoW (only reason I kept XP), vent, you tube everything works awesome in windows.  Yes I just said windows is working far better than Linux ATM, and yes it made me feel dirty.

It's definately a Linux only problem.

I'd have to enable the restricted drivers to get the error message, and if I do that I'm going to have to redo linux again

---

### Post by HermanAB on 2007-11-05
If you have more than two serious problems then you should switch to a different distribution.

"If at first you don't succeed, try and try again.  Then give up.  It is no use being a damn fool about it." - A. Nonymous.

---

### Post by mridkash on 2007-11-05
If Ubuntu Fiesty (7.04) was good then why on earth you want to upgrade to gutsy (7.10).

---

### Post by Digitallysick on 2007-11-05
I think you should make sure the ati driver was installed correctly i had the same problem, it would say it was installed, but when i rebooted, i got the :"failsafe" mode, try envy to get the latest ati driver

---

### Post by Dr Small on 2007-11-05
I saw alot of people upgrade because of peer pressure. (They saw alot of other folks doing it, so they did it too.)

As for me, I am uneffected by peer pressure :p

Dr Small

---

### Post by Inquisitr on 2007-11-05
Because it's an upgrade.

An OS shouldn't break because you upgraded it.  If this is something common than Linux has way more catching up to do than I always gave it credit, I shouldn't be afraid to upgrade.

I just did the restricted drivers again, and I'm stuck in 800X600 resolution now and I'm unable to make it any bigger.

The error I got when I booted was this, on a all black screen with a big black X for a cursor

Ubuntu is running in low graphics mode

Your Screen and Graphics card could not be detected correctly.  To use higher resolutions, visual effects, or multiple screens, you have to configure the display yourself.

Then there's a checkbox for "always run in low graphics mode"

And under that is 3 choices, configure, shut down, and continue.

When I try to configure there is no option for anything higher than 800 X 600.  And I have the choice for dual monitors, but it tells me I need to reboot, and when I do I go right back to that error.

Here's my xorg.conf now

```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

---

### Post by Evil Wayz on 2007-11-05
I don't know about him but i upgraded to gutsy because i was TOLD it supported dual monitors and i couldn't get feisty to do it, even after reading a dozen or so how tos. I think they fuxxored this one good and proper, cuz if you have an ATI card, it's 50/50 that you can get dual head to work.

I show two monitors connected. I can enable one or the other, but not both. IF i try to force it, i get that shitty failsafe thing and have to do a bunch of reconfiguring. And i am using the newest proprietary drivers WITH the stupid CCC. And I agree with the OP, sometimes , maybe due to the volume of posts, these forums can be remarkably unhelpful. 

I guess I am going to wait for ATI or the next distro to fix the problem. Cuz like the man says if i want to watch a movie on one screen and work on the others i have to boot to WIndows. And I hate Windows with the deadly intensity of a thousand white dwarf suns. 

And I like gutsy better than feisty. IF i could get dual monitors to work I'd strip windows off every computer in my house. AS it stands my main desktop with dual monitors is the only box left that isn't running Gutsy.

---

### Post by jfinkels on 2007-11-05
> **Inquisitr said:**
> 
It's not hardware because when I boot into XP everything works fine, dual monitors, WoW (only reason I kept XP), vent, you tube everything works awesome in windows.  Yes I just said windows is working far better than Linux ATM, and yes it made me feel dirty.

When I say "hardware problem", I don't mean that your hardware is physically damaged, I mean that your hardware is not supported well on Linux because manufacturers such as ATI and nVidia don't release specs for their cards, and don't release open source drivers for their devices, making it *extremely* difficult for developers to work with. Send ATI a message letting them know how upset you are that they don't cooperate with open source software developers!

> **Inquisitr said:**
> 
An OS shouldn't break because you upgraded it.  If this is something common than Linux has way more catching up to do than I always gave it credit, I shouldn't be afraid to upgrade.
You are absolutely correct. I agree that you should be able to upgrade to the newest version of your operating system without concern for the safety of your system. However, this is far from common. It just happens that your particular combination of hardware gives Ubuntu a problem.

Again, this is not the problem of Linux, it is the problem of ATI, who manufactures specifically with Windows in mind and fails to release open specs and drivers. The range of success that Linux has had is truly remarkable considering such obstacles! A testament to its greatness :D

Aaanyway, the point is, see if your problem has come up before in the form of a bug at [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs) , post a bug report if it has not, and try a different distribution.

---

### Post by Flying caveman on 2007-11-05
> **Inquisitr said:**
> ...

I just did the restricted drivers again, and I'm stuck in 800X600 resolution now and I'm unable to make it any bigger.

The error I got when I booted was this, on a all black screen with a big black X for a cursor

Ubuntu is running in low graphics mode

Your Screen and Graphics card could not be detected correctly.  To use higher resolutions, visual effects, or multiple screens, you have to configure the display yourself.

Then there's a checkbox for "always run in low graphics mode"

And under that is 3 choices, configure, shut down, and continue.

When I try to configure there is no option for anything higher than 800 X 600.  And I have the choice for dual monitors, but it tells me I need to reboot, and when I do I go right back to that error.

Here's my xorg.conf now... 

 I started having that happen to me after I installed VirtualBox, but I uninstalled it and was able to get my proper resolutions working,  

I think there could be something in your /boot/grub/menu.lst that can cause some weirdness too.

---

### Post by Arthur Archnix on 2007-11-05
I got this from a stick talking about installation and known issues with Gutsy specifically referring to what you're trying to achieve:

> Other known bugs
Blank screen with some ATI hardware

* People with ATI display adapters may get a blank screen when loading X due to the driver being unable to initialize certain hardware. Upstream is working on it, and hopefully we'll be able to release an update for 7.10 soon after the release. In the meantime, add 'Option "LVDSBiosNativeMode" "false"' to the driver section of xorg.conf. Bug #132716

Dual-head (multi-screen) setups
 
*** The ati driver has dropped MergedFB / Xinerama support in favour of xrandr 1.2 support, and old multi-head xorg.conf setups will break. To set up dual-head see the guides at [http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html) or [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)**
    
* As xrandr and xinerama are incompatible, you cannot mix some graphics cards using xrandr-enabled drivers with others that are still limited to using xinerama. In this case, you will need to revert to pre-xrandr versions of the respective drivers: for Intel cards, use the old "i810" driver instead of "intel", for ATI cards, use the old 6.6 version.

* With xrandr, it is now possible to use Compiz in a multi-screen setup, however it is dependent on available video card memory. The workaround for this issue is to switch to a lower virtual resolution.

Compiz and session management

* Users who enable desktop effects will find that they are unable to use the "Remember currently running applications" feature. The workaround for this issue is to disable the use of the Compiz compositing window manager by turning off desktop effects in the System -> Preferences -> Appearance menu.

Suspend to RAM with fglrx

* Attempting to suspend to RAM using the proprietary fglrx ATI video driver from the restricted component will hard-lock the system due to changes in the kernel's memory allocator (which will be the default in Linux 2.6.23) that have not been followed by ATI in a timely fashion; this is the vendor's responsibility and is beyond our control due to the proprietary nature of the driver. Workarounds include using Ubuntu 7.04, avoiding suspending to RAM, or using the free ATI driver. Bug #121653


---

### Post by corowakid on 2007-11-06
This might be a last ditch site for you to try:

[www.albertomilone.com](www.albertomilone.com)

I had major issues with graphics etc on my nVidia card, and finally got given this site to look at. Printed out the instructions, waited until all was quiet, and got on with it.

Worked first time, and all the instructions were easy for a newbie like me. Might be worth your while.

On the issue of you dropping Ubuntu - I've thought that a lot of times, but then I remember I thought the same of Windows when it was first released. We forget that we spent a lot of time learning the weird ways of MS, so its not unreasonable to expect a similar learning curve. At least here you're among friends. I"d suggest more patience, you WILL get there.

---

### Post by hyper_ch on 2007-11-06
[QUOTE=Inquisitr;3714371]An OS shouldn't break because you upgraded it.[QUOTE]
Did Windows break when you upgraded from XP to VISTA (and the had like 6 years to create the upgrade and not merely 6months ;))

---


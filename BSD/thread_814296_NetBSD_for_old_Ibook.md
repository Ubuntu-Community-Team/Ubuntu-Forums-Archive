---
title: "NetBSD for old Ibook?"
date: 2008-05-31
forum: BSD
---

### Post by lemuriaX on 2008-05-31
Hi there,

am wondering if anyone has any info or advice...

I'm trying to resurrect an old Ibook (looks like it's a 300Mhz Power PC G3 with 160 MB RAM) and based on some research my best bet seems to be to put NetBSD on it? Or would any other .nix OS's work? 

Also, can't seem to get it to boot from CD, it's running Mac OS 9.2 - so any advice there would be great if anyone has had experience with that.

Thanks in advance,

~l

---

### Post by decoherence on 2008-05-31
I ran NetBSD from a Quadra 650 once. worked like a champ for years until the HD kicked it. 

to install I had to boot it from a floppy then hand over to the installer that was on a GIANT 1.2 GB hard disk. it had a cdrom but I guess I didn't have a CD caddy... those were the days...

how did i do it? i forget. read lots of docs. ;)

---

### Post by lemuriaX on 2008-05-31
Hmm..okay thanks for the reply decoherence.

Sounds like it's a good choice for OS at least if I can figure out how to install. 

Don't have a floppy drive though and I doubt I can get it to boot from USB if boot from CD is problematic...

~l

---

### Post by drcranium on 2008-06-01
Have you been stalking me?  I just bought a G3 clamshell on ebay and was looking for an OS. 

I was looking at OpenBSD myself.  Be sure to tell us how NetBSD works out.

---

### Post by cardinals_fan on 2008-06-01
I would definitely use NetBSD as my primary OS if NVIDIA would release a driver for it.  It's a great OS.

---

### Post by lemuriaX on 2008-06-03
Well so far have only had time to update the 9.0 OS (somehow lost access to the 9.2 system, it had both - have to admit I'm not too good with the Mac 9.x - doh!) to 9.1 so I could then update the Open Firmware and be able to boot from CD. 

@drcranium - would be interested to hear how it goes for you too.
@cardinals_fan - was hoping you might show up here, have seen your posts and you seem very knowledgable about BSD :)

~l

---

### Post by cardinals_fan on 2008-06-04
> **lemuriaX said:**
> 
@cardinals_fan - was hoping you might show up here, have seen your posts and you seem very knowledgable about BSD :)

Don't be fooled; if you need any serious advice, consult the mailing lists for your BSD distro.  I have a chronic condition which I call NetBSDitis - every month I feel a sudden urge and install NetBSD, then end up disappointed when I realize that ******* NVIDIA doesn't have NetBSD drivers.

---

### Post by drcranium on 2008-06-04
I'll be back here when it finally gets here.  Hopefully tomorrow.  I'm interested in adding bsd to my "credentials" so I hope it goes well.  I've got the ISO of OpenBSD just waiting.  If thats a no go, then NetBSD.  Fedora and Arch are last ditch efforts.

UPDATE:

Well, that went swimmingly. :(.  I kid.  Ok.  First:  Got a bug where CD-R's can't be booted from.  Then tried CD-RW's.  Openbsd still refused to boot.  Booted a minimal Ubuntu.  It failed.  Booted a mini iso.  About six hours later: Tada! Xubuntu.  I'm installed packages right now.  As for for NetBSD, Fedora, or Arch: Maybe when I have some more free time.

---

### Post by stream303 on 2008-06-07
Glad to hear that Xubuntu is up and running from the mini-iso install!

However, don't give up on the BSD's.  For those old ibooks, never use cdrw, only CD-R for iso boots, and burn at a very low speed, typically 4x or something lower than what your cdrom's read-speed is.

See you on the BSD side... :)

---

### Post by lemuriaX on 2008-06-07
Also had trouble getting NetBSD to boot - and didn't have the resources to prepare the partitions correctly. So have since moved on to installing Debian (which is a first for me too).  

Had some strange failures here with Debian too, where the install would fail partway through the process. Maybe due to burning my ISO's at too fast of a speed? Have yet to find where I can change that on my main 'buntu computer. Tried installing Brasero to see if that would help but the speed selector is always greyed out in my applications. Tried a burn thru commandline using cdrecord but those iso CD's completely failed to read (maybe didn't have the arguments set right).

In any case have a successful minimal install of Debian running. Yay! At least I can move forward here as I didn't have a Mac OS 9 CD or much experience with that OS, made it hard if not able to control everyting from the Boot CD. I really just want to run some kinda *nix OS on the old clamshell so while NetBSD would be awesome, am content to venture into Debian land for now. That's been on my list as well. 

Not compeletely sure if I don't have some hardware issues though. Time will tell more on that. It was odd how when installing Debian, it would fail but if I rebooted and tried again it would get a little farther into the process, fail - repeat these steps until finally was able to complete the install. The CD Rom integrity check would pass though...

-1

---

### Post by drcranium on 2008-06-07
Stream:  It was the CD-Rs that gave me trouble.  The CD-RW's worked fine.

Lemuriax:

Its weird to hear someone go through almost the exact experience as me at the same time.  I thought about Debian but I had never worked with it before.  I just wanted something quick.  Xubuntu is still pretty tough on it.  I've dropped down to Awesome.  I'm learning a lot.  Stupid only left click!  Fluxbox is out of the question and a lot more WM's until I figure that one out.  I would like to give BSD a try on the ibook but I don't have the time right now.  I've got an old pc sitting here though.  Maybe later...

---

### Post by lemuriaX on 2008-06-07
@drcranium: I thought about Xubuntu too and tried it but couldn't get the cd to boot. I'm pretty sure most of my trouble has been with not burning the ISO CD's at a low speed as I've read in a few places that the old Ibooks really have issues with that.

I like Xubuntu pretty much, I have XFCE and Fluxbox also installed on a HP (Feisty) with only 256 megs of RAM, but it tends to run Gnome okay so usually just boot into that as it doesn't really get used for much other than a little browsing and commandline. I think I'm going to look into IceWM though, for the Ibook. It really has to have lightweight stuff on it. Harddrive is a whopping 4GB.

---

### Post by lemuriaX on 2008-06-10
Well other than having some issues with the system clock/battery the Debian install is going great - using XFCE as it runs well on it. IceWM is cool though I have to say.

Thanks to Stream303 for reiterating the CD Burn speed issue, went back with a 2X burn and it reads much better - was having trouble with my other ISO as a repository disc but this one works great.

But to get back to the original topic, still hope to get back to the NetBSD eventually although will have to see if I can get a new battery...

-l

---

### Post by drcranium on 2008-06-11
LOL.

Noticed the same thing too.  A new battery is going to run about 50 bucks on ebay. :-| .  Good to hear Debian is going well though.  I want to put a BSD on mine still.  Just don't have the time.

---

### Post by drcranium on 2008-06-14
I tried NetBSD and OpenBSD again with no luck.  NetBSD all installed I think but couldn't boot.  OpenBSD refused completely.

I've got debian on it now but have trouble with X.  Would you mind posting your xorg.conf?

---

### Post by stream303 on 2008-06-15
You may want to look at this user page about installing OpenBSD on a PPC specifically.  It has some great info and should apply somewhat to NetBSD as well:

[http://plumblossom.org/openbsdinstall.html](http://plumblossom.org/openbsdinstall.html)

There are some good installation hints in the Apple forum here, even if you run BSD, such as running into 8gb / 128gb partitioning limits, xorg.conf suggestions, etc, although the focus obviously is on Ubuntu.

---

### Post by lemuriaX on 2008-06-17
> **drcranium said:**
> I tried NetBSD and OpenBSD again with no luck.  NetBSD all installed I think but couldn't boot.  OpenBSD refused completely.

I've got debian on it now but have trouble with X.  Would you mind posting your xorg.conf?

Sure I can post that, I sorta back burnered the project so will have to load it up and get back here. My Xwindows sessions are not always flawless on mine either though...what kinda problems are you having?

---

### Post by lemuriaX on 2008-06-17
> 
I've got debian on it now but have trouble with X.  Would you mind posting your xorg.conf?


```

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/X11R6/lib/X11/fonts/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/X11R6/lib/X11/fonts/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/X11R6/lib/X11/fonts/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Rage Mobility L AGP 2x"
	Driver		"ati"
	BusID		"PCI:0:16:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage Mobility L AGP 2x"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by drcranium on 2008-06-17
I've been getting this weird problem with the screen not "updating".  The root window will act really weird.  I've been testing with Icewm and whenever I open a menu, the menu stays on the root window.  And if I open an xterm, I can't see it.  Your xorg.conf doesn't look any different from mine.  I tried upgrading to Lenny but that didn't do anything so far as I can tell.

---

### Post by lemuriaX on 2008-06-17
Hmmm...hopefully someone more experienced than I am could offer some advice on that. 

Have you tried any other window managers? I also have XFCE and Fluxbox running on mine - which usually work well, a few anomalies here and there but I have also been doing a lot of experimenting with this install.

---

### Post by stream303 on 2008-06-19
Since this has turned into a Debian ppc install, you may want to post in the Debian forum or perhaps even the Apple forums here to get wider exposure and possible solutions.

For your low-mem requirements, you may want to build up a diy Debian or Ubuntu install manually:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Works great with ppc as well.

---

### Post by lemuriaX on 2008-06-19
@drcranium - if you carry this over to the Debian forum please post the link here so we can follow the progress

---

### Post by drcranium on 2008-06-20
Sorry.  I found old threads with the same problems but there didn't seem to be a solution.  I just set up a Ubuntu minimal install again and its working fine now.  Comparing the two Xorgs, the Ubuntu created one was practically empty.  Not even the Ati driver was specified.  I spruced it up and its working fine.  This has just been a summer project so I don't want to pour too much time into it.  Thanks for the help though.  I'll try and check this thread everyonce in a while in case someone ressurects this or any other issues arise since this subject (Original Ibook) seems to be unchartered territory mostly.  Thanks again for the help Lemuriax and Stream303.

---

### Post by lemuriaX on 2008-06-20
Okay thanks for the update. This also isn't a high priority project for me, maybe will get back to the NetBSD plan eventually - although am having a lot of fun learning Debian stuff that carries over into Ubuntu so I dunno. 

Main question for me now is do I want to invest in a battery since mine is completely dead. And since the system clock runs on the main battery with these old clamshells, if I ever unplug it the time goes WAY off. And never does take the time correctly when I set it in the Open Firmware either, although I can at least get it close.

---

### Post by mips on 2008-06-23
> **lemuriaX said:**
> 
Main question for me now is do I want to invest in a battery since mine is completely dead. 

If possible it would be cheaper to repack the battery with newer higher capacity cells.

---

### Post by lemuriaX on 2008-06-23
> **mips said:**
> If possible it would be cheaper to repack the battery with newer higher capacity cells.

I'm not sure how to go about that, do you have any links you could suggest?

---

### Post by mips on 2008-06-23
> **lemuriaX said:**
> I'm not sure how to go about that, do you have any links you could suggest?

If possible you would need a bit of technical expertise and know how to use a soldering iron. Basically involves opening the existing battery, removing the cells and replacing them with newer better ones.

What model iBook do you have then I will have a look to see what I can find out later on.

---

### Post by lemuriaX on 2008-06-23
Hmm..yeah I doubt that I would really want to get into opening the battery realistically but thanks for the suggestion. 

It's one of the first Ibooks I believe, a 300 Mhz CPU, only one USB port, no Firewire.

Perhaps if you know a good source for parts or where I could buy a refurbished one that would be cool.

---

### Post by drcranium on 2008-06-24
In my very limited looking, for the US, I found the cheapest to be on ebay for about 50 bucks.  However, this whole "college" thing is costing a lot.  So I'm waiting a bit.  Not afraid of a soldering iron though.  One of my other hobbies is ham radio.  Believe me, I've burnt many a hand on an soldering iron.  Note to all readers: Do not hold your hand out for an iron.

---

### Post by lemuriaX on 2008-06-24
Ok well if it really only takes a soldering iron, I'd try it.
Ham radio - that's cool, always wanted to have one of those.

---

### Post by mikjp on 2008-06-24
I have an old iBook (from 2001) with 600MHz & 384 MB, it runs fine Debian 4.0. Debian is **a lot** easier to set up than NetBSD.

Check out the PPC port of Debian: [http://www.debian.org/ports/powerpc/](http://www.debian.org/ports/powerpc/)

Mikko
[http://lightlinux.blogspot.com/](http://lightlinux.blogspot.com/)

---

### Post by lemuriaX on 2008-06-30
Hi Mikko,

Debian Etch is actually what I decided on for the timebeing, eventually hope to get back to the NetBSD one of these days.

---


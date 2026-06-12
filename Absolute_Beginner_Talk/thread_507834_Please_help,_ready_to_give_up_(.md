---
title: "Please help, ready to give up :("
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by TheAmazingDave on 2007-07-23
I saw a video of a Compiz Fusion system last week, and decided I had enough of Windows on my desktop. So for the past 5 days straight, I've been fighting rediculous battles to get my video card working and files working the way they should. But I've used Linux before, so I expected that.

This is what I didn't expect, Ubuntu is ludicrously fragile. Last night, after spending MANY hours getting my system up and running perfectly, I moved it to my friend's house to show him how Compiz works, becuase he's a Linux fan, too. A few nights before, I had bough a new monitor, and that killed the system, please don't ask me how, becuase I do not know. It took another few hours of playing with xconfig and xorg.conf to get the system booting properly again. That blew my mind, that just changing a monitor can bring the whole system down, retarded even.

So, armed with that knowledge, I brought the monitor with me. I even brought the Macintosh keyboard and mouse that I've been using on the system. I get to his place and set my computer up. I didn't use my keyboard and mouse because he already had them on the empty space on the table. So i hook up my monitor, and his keyboard and mouse. Guess what? Broken Xserver. After a few failed boot-ups I plug in my Mac peripherals again, and after an hour of tweaking with xorg.conf, I was able to get it to boot again. I rebooted it a few times just to make sure it was fixed, all was well.

So I set the MF'er back up in my room, same monitor, same keyboard and mouse. Hooked everything back up the way it has always been, and guess what? Xserver is broken again! :confused: :confused: :confused:

I just don't understand this. How can Linux be revered as such a great operating system if simply switching a mouse and keyboard brings the whole system configuration down? I am getting ready to pop Vista back in just to save the frustration, but I really don't want to. But if this goes on much longer, I'm afriad my head will explode.

:mad:

If anyone has advice, I would greatly appreciate it.

edit: the only difference in the configuration is that at my desk, the Mac keyboard and mouse plug in to a KVM switch, that has one single USB output to the computer, and at my friend's house, the keyboard was plugged directly in to the computer, and the mouse was attached to the keyboard. I wouldn't be surprised if that was somehow the issue, as lame as it sounds.

---

### Post by subaru on 2007-07-23
dude . . i came to ubuntu for the same reason . . and gave up in 2 days . . turns out ubuntu isnt the right platform to do those things . . . just getting the graphic cards configured is gonna take about 2 days . . and them berrys is  gonna take more . . i would suggest trying sabayon linux . . its comes preloaded with beryl and all graphics cards are supported . . right out of the box:guitar:

---

### Post by BETOCORELLA on 2007-07-23
Well Guess What Its Not Worth Having Linux Then. Ive Spent 48 Hours, Numerous Ubuntu Installations And I Still Cant Get Past The Boot. Ima Go Back 2 Vista.... I Love Linux But Its Working

---

### Post by KCAir on 2007-07-23
Thanks for the heads up.  I was just about to try to load the ubuntu platform.  Looks like I'll save the trouble.

---

### Post by Orochi on 2007-07-23
I've changed keyboards, mice, and monitors many times without any problems (although I don't have one of those KVM things). It's hard to tell what exactly your problem is from the description you gave, all I can suggest is posting your xorg.conf file and letting us take a look at it to see if there are any obvious problems with it.

---

### Post by TheAmazingDave on 2007-07-23
> **Orochi said:**
> I've changed keyboards, mice, and monitors many times without any problems (although I don't have one of those KVM things). It's hard to tell what exactly your problem is from the description you gave, all I can suggest is posting your xorg.conf file and letting us take a look at it to see if there are any obvious problems with it.

OK, let me get it.

---

### Post by BETOCORELLA on 2007-07-23
Dude Save Ur Pc Stick Wit Vista. Or Whateva U Got. I G2 Pop In The Live Cd N Reformat The Harddrives To Ntfs Then Install Vista Again.......ubuntu Why!?

---

### Post by MrHippocampus on 2007-07-23
Indeed this kind of thing is a problem at the moment, but hopefully when gusty comes out everything should work fine out of the box with mice and keyboards because xorg.conf wont be required anymore. So if we cant solve your problem here all I can suggest is to wait for gusty to be released :)

---

### Post by Orochi on 2007-07-23
Also when you say switching monitors or mice or keyboards "killed the system" or "broke Xserver" it would be helpful to have more specific descriptions of what actually happened. What did the screen look like? Did any error messages occur? etc.

---

### Post by subaru on 2007-07-23
trust me guys . . i had the same  experiences when i was toiling with ubuntu . .   and  sabayon has the best installer than any other linux distro . . . it istalls your graphics card during installation and asks you if you want to use beryl . . but it is quite resource heavy . . should have 2 gigs ram . . and it has a live dvd . . so you can imagine it huge . . . :lolflag:

---

### Post by Orochi on 2007-07-23
> **subaru said:**
> trust me guys . . i had the same  experiences when i was toiling with ubuntu . .   and  sabayon has the best installer than any other linux distro . . . it istalls your graphics card during installation and asks you if you want to use beryl . . but it is quite resource heavy . . should have 2 gigs ram . . and it has a live dvd . . so you can imagine it huge . . . :lolflag:

Thats wonderful, unfortunately its not very helpful. This is an Ubuntu support forum, saying "forget Ubuntu and install this other distro" isn't exactly a solution.

---

### Post by BETOCORELLA on 2007-07-23
Whens This Gutsys Coming Out?

---

### Post by subaru on 2007-07-23
its better than going back to windows . . isnt it . . ? ? ?  . . .

---

### Post by subaru on 2007-07-23
and im just trying to give ppl fed up of ubuntu and going back to windows another linux alternative . . . .

---

### Post by TheAmazingDave on 2007-07-23
> **BETOCORELLA said:**
> Dude Save Ur Pc Stick Wit Vista. Or Whateva U Got. I G2 Pop In The Live Cd N Reformat The Harddrives To Ntfs Then Install Vista Again.......ubuntu Why!?
I have Vista Ultimate on my laptop and love it. But Vista doesn't allow me to use my desktop like I want. I've been an on and off Linux user since Red Hat 6, and I'm not intimidated that easily. You gotta keep in mind that this is free software and it won't work as well as something you've payed a few hundred for, and it has been tested by thousands to work with hundreds of hardware combinations when it's a fresh install right out of the box. I'm not giving up over a corrupt video driver. I'm giving up that moving a computer a few miles is breaking my operating system, and when I try to show someone how cool Linux can be, all I can show them is how rediculous the xconfig is.

This thread is not to bash Linux, so please don't. 

As requested, here is the contents of my xorg.conf

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-60
	Vertrefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x768"      "1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x768"      "1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x768"      "1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x768"      "1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x768"      "1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x768"      "1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

The main hardware is as follows:

AMD Athlon 64 X2 5200
OCZ 2 gigs dual-channel DDR2-800
dual nVidia GeForce 7600GS cards in SLI (one has been removed for driver problems, seems Linux doesn't support them)

---

### Post by armandh on 2007-07-23
can it be hardware??problem?? 

low bios battery
loose connections
not great memory connection

ubuntu does not seem as forgiving of bad hardware 
generally just moving a computer while not running should not affect the softeare
but if moving changes the hardware....
I am happy with ubuntu since i have [I hope] sorted out the hardware
i had been having fun finding which are the working pci and mem slots on one I suspect was hit by lightning

---

### Post by subaru on 2007-07-23
dude . . . you have sli and youre banging your head against linux . . what a waste of graphic hardware . . . . .  forget linux . . go back to xp . . . (does vista support sli . . ?  ?):(

---

### Post by TheAmazingDave on 2007-07-23
> **Orochi said:**
> Also when you say switching monitors or mice or keyboards "killed the system" or "broke Xserver" it would be helpful to have more specific descriptions of what actually happened. What did the screen look like? Did any error messages occur? etc.

The first time it broke, I had configured the system with a 20" monitor at 1280x1024. It is a huge heavy monitor, and I wanted something smaller and lighter for transport. So I bought a 17" widescreen, plugged it in, computer would not boot. No Ctrl+Alt+BckSpace and no Ctrl+Alt+F1. Booted to command prompt, sudo nano /etc/X11/xorg.conf, adjusted the file to monitor specs, nothing. After playing around for a while, and I'm not sure what I changed, it came back.

Yesterday, mouse and keyboard plug in to the switch, the switch has one USB output to the PC. Everything was golden. Moved to friends house with same monitor, but PS/2 keyboard and mose. That broke it. Only after plugging the keyboard in to the PC and the mouse in to the keyboard (so both devices are on one input, just like with the switch, using Mac keyboard and mouse) and tweaking with the config again was I able to get it back.

---

### Post by TheAmazingDave on 2007-07-23
> **subaru said:**
> dude . . . you have sli and youre banging your head against linux . . what a waste of graphic hardware . . . . .  forget linux . . go back to xp . . . (does vista support sli . . ?  ?):(

yes, Vista pegs Quake 4 with my SLI cards at 60 FPS, the game's cap.

---

### Post by subaru on 2007-07-23
well . . just wanted to warn you . . . no sli here . . but then again it dosent make much sence  . . .cause there arent much games in linux anyways . . . .  linux is just anti gaming i guess . . .

---

### Post by MrHippocampus on 2007-07-23
The first thing that pops out at me when looking at your xorg.conf is the screen section, that will probably work nicely on whatever monitor you installed ubuntu with, but others might have trouble.

I suggest that you add the line

```

Option	    "metamodes" "nvidia-auto-select +0+0"

```

in the "screen" section just before the first SubSection "Display". That should tell the nvidia driver to use the EDID information from the monitor and not the defaults listed below it.

Im not sure about the input device problem though, hopefully somebody else can have a look.

> 
and when I try to show someone how cool Linux can be, all I can show them is how rediculous the xconfig is

I know exactly what you mean :(

---

### Post by TheAmazingDave on 2007-07-23
Thanks! I will most certainly give that a shot. :)

---

### Post by xpod on 2007-07-23
> You gotta keep in mind that this is free software and it won't work as well as something you've payed a few hundred for, and it has been tested by thousands to work with hundreds of hardware combinations when it's a fresh install right out of the box.

With a fresh install of XP i`d have to install ethernet drivers,soundcard drivers,graphics card drivers and motherboard drivers.Of course if i bought some pre-installed thing i`d probably get my drivers with a whole heap of other crap i dont really need ......or want.

The only driver i``ve had to install with any linux disto i`ve tried so far has been the graphics card.Even then thats only been when i`ve installed a seperate card for all the 3d stuff.All 5/6 of the pc`s i`ve had/have this last year or so have all worked fine with their basic onboard graphics chips, without having to install a thing.

Granted Vista was different in that regard but..

[-(

I`ve actually been lucky enough not to have to pay for XP or Vista really so cost dont even come into the equation....we still dont use them.

---

### Post by TheAmazingDave on 2007-07-23
> **xpod said:**
> With a fresh install of XP i`d have to install ethernet drivers,soundcard drivers,graphics card drivers and motherboard drivers.Of course if i bought some pre-installed thing i`d probably get my drivers with a whole heap of other crap i dont really need ......or want.

The only driver i``ve had to install with any linux disto i`ve tried so far has been the graphics card.Even then thats only been when i`ve installed a seperate card for all the 3d stuff.All 5/6 of the pc`s i`ve had/have this last year or so have all worked fine with their basic onboard graphics chips, without having to install a thing.

Granted Vista was different in that regard but..

[-(

I`ve actually been lucky enough not to have to pay for XP or Vista really so cost dont even come into the equation....we still dont use them.

I'm glad that you don't use Windows, but the fact is that a fresh copy of Windows XP or Vista will run on the majority of systems out there with little to no trouble. I have never had any version of windows not boot because I switched a mouse, or because of a bad video driver. It is reliable, regardless of what the Linux fanboys here think.

I purchased Vista Home Premium 32 bit the day of release. It installed perfectly the first time with **ZERO** hardware problems, on my 64 bit HP laptop. A few weeks later, I upgraded my laptop to 64-bit Ultimate, again with **ZERO** hardware problems. The only thing that didn't work was the built-in webcam, which HP gladly gave me a driver for, which installed stupid easy. I then installed Vista Home Premium 64 bit on the very machine I have Ubuntu on. Guess what? **ZERO** hardware problems, even with the SLI video (SLI didn't work, but it didn't crash the computer either, unlike my experience thus far with Ubuntu) and the machine was blazing fast. It also ran rock-solid stable with my motherboard set at 10% overclock. The CPU and memory are liquid-cooled.

Now here I am 5 days hard in to Ubuntu, on the same machine that runs 64 bit Vista on MS drivers with zero problems, trying to get the machine to boot and run stable because I bought a new monitor, and switch keyboards and mice. I also had to remove a video card and set it for normal clock rates to accomplish part of that. I don't think I need to go furher with that argument.

And I said I'm not here to bash on anything. I want this to work, so I obviously like it better than Windows as well. ;)

---

### Post by Orochi on 2007-07-23
I agree that Ubuntu definitely has some issues when compared to Windows or Mac. I feel this is largely due to the fact that a lot of drivers are 3rd-party because the actual company won't spend the time and money to put out ones themselves. For instance, on my laptop with an Intel graphics chip I had to spend days getting the monitor set up right, and I still can't get dual-screen suport working. Whereas on my desktop with an Nvidia card, everything worked perfectly with no tweaking on my part because Nvida actually releases Linux drivers itself.

Linux doesn't have enough marketshare because companies won't release drivers and software for it, and they don't release them because the marketshare is too small :P It's definitely getting better though, and I have high hopes for Gutsy improving a lot of issues. When Ubuntu works, it works far better than Windows ever did for me. When it doesn't work though... well lets just say I'm glad I have an XP partition on my laptop.

---

### Post by TheAmazingDave on 2007-07-23
Speaking of laptops, my HP dv9010us will not boot Ubuntu OR Kubuntu. I have to install them in safe graphics mode, and after that, the computer will not even boot in to command prompt. But I'm more concerned with getting my desktop stable first.

---

### Post by philter on 2007-07-23
I'm not sure if you were aware, but SLI is supported by the latest Nvidia drivers for linux. I just did a quick search and found this post. 

[http://ubuntuforums.org/showthread.php?t=506363]("http://ubuntuforums.org/showthread.php?t=506363")

Hope it helps

---

### Post by xpod on 2007-07-23
> I'm glad that you don't use Windows, but the fact is that a fresh copy of Windows XP or Vista will run on the majority of systems out there with little to no trouble. I have never had any version of windows not boot because I switched a mouse, or because of a bad video driver. It is reliable, regardless of what the Linux fanboys here think.

I very much doubt that Vista would run on the "majority" of systems out there... unless your assuming that nearly every computer user on the planet has a computer even capable of running Vista.

Many here for instance dont have pc`s capable of running XP never mind Vista.:)

Anyway, If my turning a computer on for the very first time last year and soon afterwards discovering Linux/Ubuntu....to find it far superior to  the ME,XP or Vista makes me a "fanboy" then i guess thats what i`ll be.

I just happen to have 4 little fangirls and another fanboy who would`nt have it any other way either and thats the main reason we dont use Windows now.....It`s there if they want it.

When a 6 year old prefers to reboot into Ubuntu though i dont question it:)

---

### Post by TheAmazingDave on 2007-07-23
> **xpod said:**
> I very much doubt that Vista would run on the "majority" of systems out there... unless your assuming that nearly every computer user on the planet has a computer even capable of running Vista.

Many here for instance dont have pc`s capable of running XP never mind Vista.:)

I suppose I'm a better Windows user than you then, because I have had Vista running on an Athlon XP 1700 and half a gig of RAM with no Aero running stable, but a tad sluggish, without issue. Likewise, I've had XP running strong on AMD K6-2 systems. If the people here are running 486's, then maybe they should be using Linux.

I don't understand what you're not getting. I am not here to debate the superior operating system. I am here because I need help getting my Linux system running as well as my Windows system. That is all. I want to be able to browse the internet while burning a CD (it just crashed 5 minutes ago while doing this) like I could with Vista.

As you are obviously a better Linux user than I am, I am asking for your advice based on your experience and knowledge of the system. If all you are able to provide is an argument that Windows sucks, I ask that you leave because that's not very helpful at this point in time.

Thank you.

---

### Post by TheAmazingDave on 2007-07-23
I got the system running again by plugging the keyboard directly in tot he PC, booting it, then switching it back to the KVM. All is well now, but the system is crashing intermittently.

> **philter said:**
> I'm not sure if you were aware, but SLI is supported by the latest Nvidia drivers for linux. I just did a quick search and found this post. 

[http://ubuntuforums.org/showthread.php?t=506363]("http://ubuntuforums.org/showthread.php?t=506363")

Hope it helps

It won't boot at all at this point with both cards installed. Installing the nVidia driver with Envy caused a black screen.

---

### Post by philter on 2007-07-23
Well if you installed drivers with Envy then the system is booting. I think what you're trying to say is that your Xserver isn't starting properly? What happens if you press ctrl+alt+F5 to get to a console and login and then type in startx. That should spit out an error on a line in your xorg.conf file, or at least provide more information that can possibly help us.

---

### Post by TheAmazingDave on 2007-07-23
I tried Envy a few days ago, and it left me with a black screen on boot up. If I used the command line to reconfigure xserver to boot with the vesa driver, I could get the GUI back, but if I tried to reinstall with Envy I would get the black screen again. 

So then I tried enabling the nVidia driver in the Restricted Drivers Manager or w/e it's called and it would tell me the driver was in use, but the box to enable it would be unchecked and compiz would fail due to the vesa driver. Clicking the box in the driver manager would prompt me to reboot, but it would reboot with the vesa driver again and the driver manager will still report it's in use when it wasn't. 

So I formatted and reinstalled, and just enabled the driver in the manager without trying Envy. That worked to get all of the software working, but then the computer won't boot with both cards in.

But none of that matters at the moment because it crashed again when I tried to reburn the CD, and I'm now stuck with another black screen. I can get to the command prompt and view the xorg.conf file, and it is exactly the same as I posted on page 2.

This is really blowing my mind.

---

### Post by philter on 2007-07-23
When you get that black screen after you're booted into Ubuntu can you try logging into a terminal session (ctrl+alt+F5) and type in **startx**. That will attempt to start up the GUI and if it is having problems it will tell you what the problems are. That way you can post those errors so we can figure out what is going wrong.

---

### Post by xpod on 2007-07-23
> I suppose I'm a better Windows user than you then, because I have had Vista running on an Athlon XP 1700 and half a gig of RAM with no Aero running stable, but a tad sluggish, without issue. Likewise, I've had XP running strong on AMD K6-2 systems. If the people here are running 486's, then maybe they should be using Linux.

I don't understand what you're not getting. I am not here to debate the superior operating system. I am here because I need help getting my Linux system running as well as my Windows system. That is all. I want to be able to browse the internet while burning a CD (it just crashed 5 minutes ago while doing this) like I could with Vista.

As you are obviously a better Linux user than I am, I am asking for your advice based on your experience and knowledge of the system. If all you are able to provide is an argument that Windows sucks, I ask that you leave because that's not very helpful at this point in time.

Thank you.


And i with an Athlon XP2200 with half a gig of Ram too......stable but terrible all the same.
I manged to use some third party apps that added some 3d flip etc that the System itself would`nt provide....very strange that was.
Anyway,i`m sorry if you got the impression i was starting some stupid argument with you, i was but responding to the slightly strange seeming statements you made..

Anyway,If i can help you i would but either way theres plenty good people here than can do a much better job of it than me........i`ll be a "noob" for a couple of years yet i reckon:)

I`ll read back through your thread though.

EDIT: The only advice i can give if your having this much trouble with your SLi setup and/or KVM switch(during your first days) is to try mabey sticking with a just basic setup first ....ie just one card and no switches to start out possibly??
We can use either the ps2 or usb keyboards & mice in any combination with any combination of monitors too(the ones we have anyway)
without a problem so i guess i`ve just been lucky,thankfully.

You certainly dont need the two cards if it`s just compiz you want to run.That seems to be your main reason for wanting to try Ubuntu anyway?
Like others said though if your having this much touble with any OS ........on your paticular hardware then mabey it`s better the devil you know....so to speak.Or try something else possibly?

---

### Post by TheAmazingDave on 2007-07-23
compiz is not the only reason I want to use Linux. It's light code runs fast and preserves disk space (My Vista install is around 8 gigs, my OS X 10.5 install is over 10 gigs), it is very secure, and (aside from my recent experience) gnerally very stable, amongst other reasons.

Why did compiz seal the deal? Because I waited a long time for Vista, because it was made to seem that it would be revolutionary. I love all the new fetures of Vista, but as elegant as the Aero interface is, it didn't have things that I really hoped it would, in terms of application and window management. The Aero 3D switcher is great, but that's it. Same with Leopard, I installed the latest RC over the weekend, and it is less than spectacular, but an improvement nonetheless. I love the desktop cube plugin in compiz, it makes keeping my open apps organized very easy, and all the extra eye candy is a nice touch, too.

But back on topic, I have found that whenever the xserver fails to start, all I have to do now is plug the USB keyboard directly in to the computer and restart, the GUI will load fine after that. I can then pull the keyboard off the PC, hook it back up to the KVM switch, and all is fine. Absolutely bizzare.

I'm glad it's working however.

---

### Post by anewguy on 2007-07-24
Okay, I'm new here too, but I'll toss something in.  If you can get it going with the USB keyboard, I would suggest you add another input device in xorg.conf defining a ps2 keyboard (psaux?).  If you then restart x it should work with a ps2 keyboard or a usb keyboard.:)

   Also, for all the newbie's reading this thread, keep in mind that Compiz, Compiz-fusion and the old Beryl look nice, but they are just "slick" (if you'll forgive me - I know there's a lot to them!) add-ons.  They are by no means a requirement to run LInux - they are "eye candy".  So, while this user wants Compiz and I will never judge him for going for what he wants, they aren't required for "you" to try Linux.  

   There are some things to be advised of, however.  I think the 2 hardest things for a lot of users (not all, and I'm sure they'll reply here) are getting wireless networking to work and getting video set up.  Someone illuded to this earlier in this post - the reason is that since Windows has such a huge installed base, hardware (and software) manufacturers put their efforts to where they can make money, and that is Windows.  Linux is meant to be free at it's core (the kernel), but anyone can do what they want on top of that.  For us, it's nice that there is a large community of people out there willing to donate their time and efforts to give us all of this stuff for free.  And, everyone wants to keep it free. 

   Guess what?  Unless a company says it is a non-profit, they are in business SOLELY to make money - that's the bottom line.  While many say it would be a nice gesture on the part of the manufacturers to provide either drivers for Linux or the detailed specs of their hardware so someone can write drivers, the fact is that few companies are going to do that at this time.  Things, as you know, are constantly changing in the computer world, and these companies have to change (i.e., spend money) to stay in market share and make money.  If they don't make money the investors take their money out and put it elsewhere, so for now there is a huge shortage of Linux drivers for the hardware that is changing the most, or hardware that makes more use of software to function.  What are the main things affected by that in the current market?  Video cards by far #1.  Wireless comes in second.  People are working to give you the best free version of stuff they can,  but it will require work on your part - that's just a fact of Linux for now.:)

   I'm not a Windows or Linux basher.  I believe in using whatever works best for the task at hand.  If you want to try Linux, and in particular Ubuntu, don't let these things scare you off.  You can use the default VESA driver, you just won't have some of the fancier eye-candy and some games.:)

   I like Linux, and in particular Ubuntu.  Don't be afraid to try it because of horror stories you may read or hear about.  At the same time, be advised that you most probably have to do more work than Windows to get Ubuntu (or any Linux) working on your system.  Right now that's just the way things are!:)

---

### Post by TheAmazingDave on 2007-07-24
While I agree with the above that for anyone looking to play around with Linux, you don't necessarily need to worry about the video driver. However, with the vesa generic driver, you are limited to the display resolutions available. Or at least on my system, I was not even able to set the resolution to 1280x720, my monitor's native resolution.

---

### Post by anewguy on 2007-07-24
You are exactly right - the default resolutions probably won't be good enough, especially if they have a hgiher end video card or a larger LCD, etc..  Hopefully they would install, play around, and then ask questions.:)

Sure wish we could find something for you!  Maybe we'll get there yet!:)

---


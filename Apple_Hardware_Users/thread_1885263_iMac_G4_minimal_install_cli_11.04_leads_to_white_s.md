---
title: "iMac G4 minimal install cli 11.04 leads to white screen"
date: 2011-11-22
forum: Apple Hardware Users
---

### Post by BrianWeinberg on 2011-11-22
I have followed the instructions to install 11.04 on an iMac G4 (lamp model) using the minimal install of a CLI only as spelled out on this sticky:
[http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1)

The CD has been verified, and the install process runs smoothly.  After rebooting upon completion, yaboot completes its two prompts correctly, and appears to start up when it finally results in a blank white screen.  I have tried all variations of 'Linux nosplash video=ofonly' after the second prompt, with no luck.  It still ultimately ends up on a blank white screen.  

Here is my model:
[http://www.everymac.com/systems/apple/imac/stats/imac_800_fp.html](http://www.everymac.com/systems/apple/imac/stats/imac_800_fp.html)

Also, I have access to an external firewire dvd drive, if making a liveCD will work out better (although, the instructions above seem to indicate not).

My ultimate solution would be to end up with 11.10 installed, if possible.

Any advice would be greatly appreciated.

---

### Post by rsavage on 2011-11-23
That will be the instructions I wrote then....
 
Sorry you haven't been able to get them to work. I should say first it's great to get some feedback on them as I don't know if many people have used them? You are certainly the first imac G4 to write anything. 
 
I have no experience personally with fixing screen issues or nvidia cards. The blank screen section of the instructions was written entirely from reading the manuals and bits I gleaned from other posts. It seemed to me that the advice being given on the forum and elsewhere was so unbelievably bad that some sense needed to be made of it all. That section was my attempt.
 
> **BrianWeinberg said:**
> I have tried all variations of 'Linux nosplash video=ofonly' after the second prompt, with no luck. It still ultimately ends up on a blank white screen. 

 
Nosplash and video=ofonly have been historically the two parameters that have always been suggested and that is why I say to try them first. However, since you have a nvidia card I would also try nouveau.modeset=0 like I say to do in the instructions. At the second yaboot prompt type
 
Linux nouveau.modeset=0
 
There is a link in the instructions which explains this. Basically, nvidia cards used to use a driver called nv, but now the default driver is called nouveau. That occasionally doesn't work (but it improves with every new version of ubuntu so it may work for you in 11.10) and you have to revert back to the nv driver. noveau.modeset=0 turns off the nouveau driver. To turn on the nv driver you have to setup an xorg.conf file. Do this after you are fully installed.
 
Write back if it works or if you need any further help.

---

### Post by BrianWeinberg on 2011-11-23
That seems to have worked!  Thank you.  I will continue with the rest of your instructions to upgrade to 11.10 from the command line, and then install the GUI.  Wish me luck!

Quick question - if I haven't yet installed the GUI, why are the video drivers needed, as the command prompts seem to work during bootup, up to a point.  I wasn't aware that they would be needed for a CLI only.

Also, do you know if the AirLink101 AWLL6077v2 USB wireless adapter has worked with this setup?  It was one of the few Mac OS X-compatible wireless adapters available (no airport in this one), and I would love to be able to still use it.

As to your directions, they are very much appreciated.  I found them very thorough.  I use Ubuntu every day on other PCs, however.  I could see how they might be hard to follow for a newcomer.  It is a lot of information to process.  It also requires reading completely from top to bottom a few times to pick out what is relevant for your situation, and even then, I found myself needing to reinstall a few times before I got it right.  I think as an overall resource, it is fantastic, but perhaps it could be reorganized a bit to make it easier for newbies.  I will try to put together some notes on ideas and shoot them off to you, if you would like.  I think what you are working on is one of the most important aspects of the community, making Ubuntu accessible to all.

By the way, if this works out well, you will have made my 10 year old daughter very happy.  She has always loved the looks of the "lamp" iMac (me, too), and when I found one to set up for her, it was perfect for homework with OS X 10.4.11, but it couldn't handle many websites very well, due to its lack of updates for a few years.  Thank you for all of your efforts!

---

### Post by BrianWeinberg on 2011-11-23
Upgrade installed smoothly, but after reboot, no joy. :(

I get a BusyBox prompt after it doesn't find the hard drive.  It appears that the /dev/disk is not found by default.

Following your instructions, I have so far been able to determine that it is necessary to run 'modprobe pata_macio' for my system to find the drive first (at the BusyBox prompt), and then I can boot into the system by pressing ctrl+D .

Next, I entered 'echo pata_macio | sudo tee -a /etc/initramfs-tools/modules' , as you suggested in this post:  [http://ubuntuforums.org/showthread.php?t=1861871](http://ubuntuforums.org/showthread.php?t=1861871)  
I think you should modify that post to note that you should enter 'update-initramfs -u' after the pata_macio modification is made, so that the change to the file will stick after future reboots.

I will next add the GUI, as you have outlined, and post how I fare.

---

### Post by BrianWeinberg on 2011-11-23
Using 'tasksel' , aptitude failed (100).  So, I instead entered 'sudo apt-get install ubuntu-desktop'.  This resulted in the following message:
[INDENT]Some packages could not be installed.  This may mean that you have requested an impossible situation or your are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
ubuntu-desktop : Depends: unity but it is not going to be installed
E:  Unable to correct problems, you have held broken packages.[/INDENT]

If you have any ideas, I would appreciate them.  I will keep researching and post any success I have.

---

### Post by rsavage on 2011-11-23
I wondered if you might get that.  pauljwells reported something similar [http://ubuntuforums.org/showpost.php?p=11473448&postcount=31](http://ubuntuforums.org/showpost.php?p=11473448&postcount=31) .

---

### Post by rsavage on 2011-11-23
There is a whole load of unity-common packages here [http://ports.ubuntu.com/pool/main/u/unity/](http://ports.ubuntu.com/pool/main/u/unity/) . I suppose you'd download one of them using wget and install using dpkg -i like I had to do for another package in my lubuntu script.
 
Will reply to your other post (regarding noob instructions) when I have more time, but if you'd like to start noting down how it can be improved (while it is still fresh) then please do.  As i said in the intro, it needs moving to a wiki.  Volunteers welcome!

---

### Post by BrianWeinberg on 2011-11-23
First, I ran 'sudo apt-get install unity-common', which only installed partly.  Next, I tried, as you suggested, the following:
[INDENT]wget -P/tmp [http://ports.ubuntu.com/pool/main/u/unity/unity-common_4.24.0-0-Ubuntu2b1_all.deb](http://ports.ubuntu.com/pool/main/u/unity/unity-common_4.24.0-0-Ubuntu2b1_all.deb)
sudo dpkg -i /tmp/unity-common_4.24.0-0-Ubuntu2b1_all.deb[/INDENT]
That didn't seem to help.

I then ran:
[INDENT]sudo apt-get install unity-lens-applications
sudo apt-get install unity-lens-files
sudo apt-get install unity-lens-music
sudo apt-get install indicator-appmenu
sudo apt-get install indicator-application
sudo apt-get install indicator-sound
sudo apt-get install indicator-datetime
sudo apt-get install indicator-messages
sudo apt-get install indicator-power
sudo apt-get install indicator-session[/INDENT]

All install fine.  I then again tried 'sudo apt-get install unity-common', and I received the same message as earlier:
[INDENT]The following packages have unmet dependencies:
 unity : Depends: unity-common (= 4.22.0-0ubuntu3) but 4.24.0-0ubuntu2b1 is to be installed
E:  Unable to correct problems, you have held broken packages.[/INDENT]

I then realized, I misunderstood what you meant.  I reinstalled the older unity-common:
[INDENT]wget -P/tmp [http://ports.ubuntu.com/pool/main/u/unity/unity-common_4.22.0-0ubuntu3_all.deb](http://ports.ubuntu.com/pool/main/u/unity/unity-common_4.22.0-0ubuntu3_all.deb)
sudo dpkg -i /tmp/unity-common_4.22.0-0ubuntu3_all.deb[/INDENT]

Then I ran:
[INDENT]sudo apt-get update
sudo apt-get upgrade[/INDENT]
This brought everything up to the correct versions.

Oddly, however, I am still unable to install ubuntu-desktop, as it still indicates the unity dependency.  
[INDENT]The following packages have unmet dependencies:
 unity : Depends: unity-common (= 4.22.0-0ubuntu3) but 4.24.0-0ubuntu2b1 is to be installed
E:  Unable to correct problems, you have held broken packages.[/INDENT]
And, trying to install unity states that it needs unity-common, but indicates the same version error as above.  I am not certain what I can do at this point.  Any advice would be appreciated.

---

### Post by rsavage on 2011-11-23
I can only go by what pauljwells said. He said install an old version of unity-common and then install ubuntu-desktop. Reboot. You can then upgrade the versions of packages. This will break ubuntu-desktop (and unity?) but it doesn't matter because ubuntu-desktop is just a 'meta' package and it has done it's job. At this point you can actually remove ubuntu-desktop. Sounds more complicated than it is I think! If you get awful colours then you may have to choose the unity-2d session at login.

---

### Post by rsavage on 2011-11-23
Just thought I better say don't do anything drastic like re-installing from the beginning!  Totally not necessary!

---

### Post by rsavage on 2011-11-23
Okay, found a bit more time to have a look into this. The easiest thing is probably to install a newer version of unity. There should be a newer version in oneiric-updates, but maybe it has been missed off for powerpc (EDIT: yep here is the fail [https://launchpad.net/ubuntu/+source/unity/4.24.0-0ubuntu2b1/+build/2875419](https://launchpad.net/ubuntu/+source/unity/4.24.0-0ubuntu2b1/+build/2875419), but it was built later for 12.04)? The powerpc time stamp is a few days later than for other architectures. This is what I think is causing the problems. So see if you can install the new version manually....
 
```

wget -P/tmp http://ports.ubuntu.com/pool/main/u/unity/unity_4.24.0-0ubuntu2b1_powerpc.deb
sudo dpkg -i /tmp/unity_4.24.0-0ubuntu2b1_powerpc.deb
 
```Then you will be able to install ubuntu-desktop.
 
EDIT: This fix nolonger works because the unity package in 12.04 has been upgraded. You can download it directly from launchpad instead [https://launchpad.net/ubuntu/+source/unity/4.24.0-0ubuntu2b1/+build/2882663](https://launchpad.net/ubuntu/+source/unity/4.24.0-0ubuntu2b1/+build/2882663) , or install an older version of unity-common:
 
```

wget -P/tmp http://ports.ubuntu.com/pool/main/u/unity/unity-common_4.22.0-0ubuntu3_all.deb
sudo dpkg -i /tmp/unity-common_4.22.0-0ubuntu3_all.deb

```
 
You will then be able to install ubuntu-desktop. There is also a new unity package in the proposed repository that you could alternatively enable or download as above? See [https://launchpad.net/ubuntu/+source/unity](https://launchpad.net/ubuntu/+source/unity) and [http://ports.ubuntu.com/pool/main/u/unity/](http://ports.ubuntu.com/pool/main/u/unity/) .

---

### Post by rsavage on 2011-11-23
So I'll answer your points from your second post now....
 
> **BrianWeinberg said:**
> Quick question - if I haven't yet installed the GUI, why are the video drivers needed, as the command prompts seem to work during bootup, up to a point. I wasn't aware that they would be needed for a CLI only.

As I understand it some sort of framebuffer thingy (that's the extent of my technical knowledge!) has to load as well so that things like the ubuntu splash screen can be displayed.
 
> **BrianWeinberg said:**
>  Also, do you know if the AirLink101 AWLL6077v2 USB wireless adapter has worked with this setup? It was one of the few Mac OS X-compatible wireless adapters available (no airport in this one), and I would love to be able to still use it.
No idea I'm afraid.
 
> **BrianWeinberg said:**
> As to your directions, they are very much appreciated. I found them very thorough. I use Ubuntu every day on other PCs, however. I could see how they might be hard to follow for a newcomer. It is a lot of information to process. It also requires reading completely from top to bottom a few times to pick out what is relevant for your situation, and even then, I found myself needing to reinstall a few times before I got it right. I think as an overall resource, it is fantastic, but perhaps it could be reorganized a bit to make it easier for newbies. I will try to put together some notes on ideas and shoot them off to you, if you would like. I think what you are working on is one of the most important aspects of the community, making Ubuntu accessible to all.
I know it is a cop out, but they were never written for a newcomer! Basically, the instructions started off as my bookmarked pages with a few notes inbetween. They are notes I wrote for myself to allow me to install again. I just wrote them down in a public place in the hope that they would help others. As the number of bookmarked pages have grown I appreciate the workarounds section has become a bit unwieldy. I have tried to put in more info for the newbie, but the result is they always get longer and consequently look more intimidating.  I'll be happy to listen to your thoughts.....
 
I don't own a working PPC machine (although I'm still hoping to resurrect my ibook) and so it is hard for me to maintain the instructions at the moment. It is now down to others with working PPC machines to find solutions and post them for the rest of the community. If others showed an interest in creating a new wiki or updating the existing FAQ then I'd help out, but it is pointless me doing it by myself. I know there are smart people out there using powerpc ubuntu, but (with the exception of a few) they just don't come on the forum. More people need to file bug reports too (to my shame I have never done one) so that things like the missing unity package get fixed and we wouldn't have to write workarounds for them!
 
> **BrianWeinberg said:**
> By the way, if this works out well, you will have made my 10 year old daughter very happy. She has always loved the looks of the "lamp" iMac (me, too), and when I found one to set up for her, it was perfect for homework with OS X 10.4.11, but it couldn't handle many websites very well, due to its lack of updates for a few years.
I just hope she doesn't want flash for games......
 
> **BrianWeinberg said:**
> Thank you for all of your efforts!
No problem, I enjoy the challenge of getting things to work and helping people!

---

### Post by BrianWeinberg on 2011-11-24
Post 11 above was exactly the problem.  It is interesting that the date stamp supercedes the version number.  I was able to install, and then install ubuntu-desktop.  Unfortunately, even after updating and rebooting, I am still having the crazy colored desktop.  This is the same whether I choose Ubuntu or Ubuntu 2D.  Classic is not an option, but I will install the Gnome desktop and let you know.

When I am finished with this (I will keep at it until I get this working!), I will try to put together a document on how to get 11.10 running on an iMac G4 (lamp model) geared towards newbies, and you can let me know your thoughts.  Maybe it could of some use to people.

I am hoping that with gnash and lightspark, she will at least be able to watch some stuff on YouTube.  Who knows?  I will let you know.  I can always revert back to OS X 10.4.11 if need be, but I am hoping this will be a better experience.  I will repost when I get the graphics working again.

Thanks again for all of your help.

---

### Post by rsavage on 2011-11-24
Okay well I'm glad you got ubuntu-desktop installed.  It is good to know the solution.

Maybe you have to setup an xorg.conf to fix the colours?  Are you still using nouveau.modeset=0?  

I'd be interested in the speed of unity on your imac.  When I tried it in natty it was dog slow and I much preferred xubuntu.

I should warn you gnash and lightspark have been problematic on recent firefoxes.  It would be good if you could track down the problem!!! Not that you need any more problems...... 

YouTube/Vimeo can be watched using html5 or the firefox extension FlashVideoReplacer.

Good luck!

---

### Post by jimwg on 2011-11-24
To All Americans, Happy Thanksgivings!

> @rsavage
> I should say first it's great to get some feedback on them.

Don't feel that your sweat and assistance isn't greatly appreciated, even if some are too shy/lazy to tell you. It's because of you I've just created a dual boot 10.4.11/Ubuntu 11.04 700mhz iMac -- and I am a tech-rookie just playing it by ear! Thanks.

Now I've encountered a roadblock.

To kill the white screen problem I performed the "Linux nouveau.modeset=0" trick at the second yaboot prompt as cited here and I popped into 11.04 -- however it's in psychedelic 16-bit color mode I believe, nearly impossible to navigate though I can drop a terminal screen with effort. There, I used the suggestion of "echo options i915 modeset 0 > etc/modprobe.d/i915 - kms.conf mentioned here but nothing happens.

My question is -- and I'm not lazy but just not tech savvy so am asking for the simplest path -- how can I fix this and make the fix permanent on bootup? I am withholding upgrading to 11.10 until I hear more success stories from those with my home school system.

Thanks for any help!

James Greenidge

---

### Post by BrianWeinberg on 2011-11-24
Ok.  I have found two xorg.conf files that are supposed to work for the iMac G4 (lamp model).  I have tried both, but have had no success with either.  

With the one list for that iMac at this site (under heading iMac G4 800 Mhz):  [http://www.ppcnux.com/?q=g4-macs-and-xorg](http://www.ppcnux.com/?q=g4-macs-and-xorg)  

Section "Device"
	Identifier	"Gforce2MX"
	BusID		"PCI:0:16:0"
	Driver		"fbdev"
	Option		"UseFBDev"	"true"
EndSection

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fc
	Identifier "iMacLamp"
	VendorName "APP"
	ModelName "Color LCD"
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fc
	# DPMS capabilities: Active off:yes  Suspend:no  Standby:no

	Mode 	"1024x768"	# vfreq 60.004Hz, hfreq 48.363kHz
		DotClock	65.000000
		HTimings	1024 1048 1184 1344
		VTimings	768 771 777 806
		Flags	"-HSync" "-VSync"
	EndMode
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fc
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Gforce2MX"
	Monitor		"iMacLamp"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "Default Screen"
EndSection

The video crashes and goes straight to a command line.  I get the following error message from the /var/log/Xorg.0.log file:
[INDENT](EE) FBDEV(0):  FBIOPUT_VSCREENINFO succeeded but modified mode
(EE  FBDEV(0):  mode initialization error

Fatal server error:
     AddScreen/ScreenInit failed for driver 0[/INDENT]

From what I can gather from the X.org wiki:
[INDENT]I keep getting the message: "AddScreen/ScreenInit failed for driver 0"

You get an error message like:

(EE) R128(0): (Ron = 12288) + (Rloop = 17) >= (Roff = 12012)
Fatal server error:
AddScreen/ScreenInit failed for driver 0

This kind of problem typically occurs when you're using a big monitor with an old graphics card. You can solve it by deleting some of the highest resolutions of the deepest colour mode in the Screen section of your xorg.conf, or even the whole last Display subsection.  [/INDENT]

I have tried lowering the bit depth from 24 to 16, but that seems to do nothing.  Also, this configuration does at least the correct nvidia card that is in the machine, even if it is nothing more than a label.

From the instructions under post 2 here:  [http://ubuntuforums.org/showthread.php?t=1741817](http://ubuntuforums.org/showthread.php?t=1741817) , I tried this xorg.conf:

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
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
	Load  "record"
	Load  "dbe"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV18 [GeForce4 MX with AGP8X (Mac)]"
	BusID       "PCI:0:16:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
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

Again, the video crashes and goes straight to a command line.  I get the following error message from the /var/log/Xorg.0.log file:
[INDENT](EE) Failed to load module "nv" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
     no screens found[/INDENT]

At least here, I have a clue, and tried:
[INDENT]sudo apt-get install nvidia-current[/INDENT]
but that is not available.

I am not certain what the name of the "nv" driver is, and have not had much luck locating that online.  Nor am I sure if that will resolve the problem, but it certainly looks like I need to try that next.  If anyone knows the file name for "nv", I would greatly appreciate it.  I will let you know how I fare.

---

### Post by BrianWeinberg on 2011-11-24
I found this:
[http://ubuntuforums.org/showthread.php?t=1143179](http://ubuntuforums.org/showthread.php?t=1143179)

It seems a bit old, but I will see where it takes me.

---

### Post by BrianWeinberg on 2011-11-24
No luck.  I also tried the suggestion in this thread ([http://ubuntuforums.org/showthread.php?t=1691595](http://ubuntuforums.org/showthread.php?t=1691595) ) of changing the 'nv' in the xorg.conf to 'nouveau', but that didn't help either.

I will keep trying.

---

### Post by rsavage on 2011-11-25
@BrianWeinberg Stop!
 
Okay, let's review. Are you still using nouveau.modeset=0 because that will give you poor colors I think? Have you tried it without this in 11.10?
 
If you still need nouveau.modeset=0 then what used to be the case was you setup an xorg.conf file with the driver as 'nv'. However, it looks like the 'nv' driver has been dropped from 11.10 [http://packages.ubuntu.com/natty/xserver-xorg-video-nv](http://packages.ubuntu.com/natty/xserver-xorg-video-nv) for all architectures.
 
You can download it manually
 
```

wget -P/tmp http://ports.ubuntu.com/pool/main/x/xserver-xorg-video-nv/xserver-xorg-video-nv_2.1.17-3ubuntu3_powerpc.deb
sudo dpkg -i /tmp/xserver-xorg-video-nv_2.1.17-3ubuntu3_powerpc.deb

```and see if that works with an xorg.conf file. You can try something simple like
 
```

Section "Device"
    Identifier "Card0"
    Driver "nv"
    BusID "PCI:0:16:0"
EndSection

```
I'm not a big fan of downloading xorg.conf files from random sites/threads as I think they introduce more problems than they solve.
 
It could be the case (whether you are using nouveau or nv) that you need to specify a more detailed xorg.conf file by using the output of the 'cvt' command.  I try to explain how to do this in the instructions.
 
 
@jimwg Happy thankgiving to you too! I hope you said over your turkey "I am thankful that ubuntu still compile packages for the powerpc architecture!!!". :D
 
> 
however it's in psychedelic 16-bit color mode I believe, nearly impossible to navigate though I can drop a terminal screen with effort. There, I used the suggestion of "echo options i915 modeset 0 > etc/modprobe.d/i915 - kms.conf mentioned here but nothing happens.Unity-2d in 11.04 did have a colour problem due to endian issues I believe so that could be one of the problems. You need to switch to a Ubuntu Classic session by logging out to test it. As I explained to brian above, nouveau.modeset=0 will also give reduced colours and you need to turn on the 'nv' driver. i915 sounds like an intel video card so it won't have any effect on your machine.
 
Thanks for the feedback. It seems I still need to work on my instructions to convince you guys that configuring an xorg.conf file is not scary!

---

### Post by jimwg on 2011-11-25
> @jimwg Happy thankgiving to you too! I hope you said over your turkey "I am thankful that ubuntu still compile packages for the powerpc architecture!!!". :D 

Oh I Am and DO!! Especially since Apple left all our "vintage" machines -- even just measly security updates -- in the dust! Guess they can't spare a few coffee-machine thousands of bucks out of their billions rewarding the long faithful who spent lots at a time way back when Apple was a "dying platform". I hope PPC Ubuntu and its Snow Lion equivalent features lives forever!
 
> Unity-2d in 11.04 did have a colour problem due to endian issues I believe so that could be one of the problems. You need to switch to a Ubuntu Classic session by logging out to test it. As I explained to brian above, nouveau.modeset=0 will also give reduced colours and you need to turn on the 'nv' driver. i915 sounds like an intel video card so it won't have any effect on your machine.

Forgive my naive dense mode but I didn't even know there was a Ubuntu Classic much less how to get there! Also it's actually impossible for me to manage around in 11.04 with the screwed-up colors like that making even text too f'ed to read much less CLI or Terminal up. I suppose ideally the only access to the program to fix these twin white-out and 16-bit color situation is via the boot-up prompts I guess -- but what could I put in there?? Is there any info can offer?  Please treat me like a total Linux-eager novice!!

JimWG

---

### Post by rsavage on 2011-11-26
I've done a few minor changes to the xorg.conf instructions to try and make them clearer. See what you think....

---

### Post by jimwg on 2011-11-26
> **rsavage said:**
> I've done a few minor changes to the xorg.conf instructions to try and make them clearer. See what you think....

It's going to be interesting to see how one loads them with this situation!! :)


My home school and I thank you!

JimWG

---

### Post by BrianWeinberg on 2011-11-26
@rsavage

I have tried your instructions in post #19

Using the cvt command, I have come up with the following xorg.conf file:

Section "ServerLayout"
     Identifier     "X.org Configured"
     Screen         "Screen0"
EndSection

Section "Monitor"
     Identifier     "Monitor0"
     VendorName     "Monitor Vendor"
     ModelName      "Monitor Model"

     Modeline "800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
EndSection

Section "Device"
     Identifier "Card0"
     Driver     "nv"
     VendorName "nVidia Corporation"
     BusID      "PCI:0:16:0"
EndSection

Section "Screen"
     Identifier     "Screen0"
     Device         "Card0"
     Monitor        "Monitor0"
EndSection


This resulted in the following error in the Xorg.0.log file:
(EE) module ABI major version (8) doesn't match ther server's version (10)
(II) UnloadModule: "nv"
(II) Unloading nv
(EE) Failed to load module "nv" (module requirement mismatch, 0)
(EE) No drivers available
Fatal server error:
no screens found

I did install the nv driver as you outlined in that post.  Any ideas?  I am afraid I don't know anything about xorg.conf.

Thanks.

---

### Post by rsavage on 2011-11-27
Well that is annoying! From googling that error it seems it doesn't like the older nv package with the newer xorg packages. I'm afraid this is new territory for both of us!
 
The suggested thing seems to be that you need to compile the nv driver against the newer xorg packages. [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+question/177231](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+question/177231) There are compile instructions in the 'General Workarounds' section of my instructions.
 
Before you do that you really should try it with the nouveau driver. You haven't said whether you've tried it without nouveau.modeset=0 in 11.10. I can give you more help with compiling when you have answered this.

---

### Post by rsavage on 2011-11-27
I've just realised that the modeline in your xorg.conf file is exactly the same as the one I gave in my instructions. That is a BIG fail for my instructions! (EDIT: I'm assuming the iMac and the 12" iBook wouldn't produce the same output, I apologise if they do!!) The modelines are monitor specific and you need to run the cvt command for YOUR computer/monitor. Otherwise you run the risk of damaging your monitor (especially if it is an old big chuncky one).

---

### Post by BrianWeinberg on 2011-11-27
I'm sorry if I didn't make that clear.  Yes, I have tried it without nouveau.modeset=0 .  I end up with a white screen in each of those instances.  I always tried booting with and without that parameter.

The output from my cvt command was identical, so I ended up with the same line entry.  This iMac has a 15" monitor and an nVidia GeForce2 MX video adaptor, and that line is the result from the cvt command.

Before I compile the nv driver against the newer xorg packages, I would like to take a step back and review against pauljwells method.  When I did my install, I did 11.04 command line, then upgraded to 11.04, then installed the GUI through the methods outlined earlier in this thread.  Is it possible that he installed 11.04, installed the GUI, then upgraded to 11.10?  And if so, might that account for some potential differences in his experiences and mine (such as having to install unity-common manually, and the like)?  Finally, if that was the case, might that also account for the different results he experienced?  Just a shot in the dark, but I thought I should ask.

---

### Post by rsavage on 2011-11-27
Well pauljwells certainly knows more about unity than me! He was responsible for unity-2d being fixed for powerpc. However, I think his install was roughly the same as yours although you are you using a newer version of unity I think. The main difference is he is using the nouveau driver.
 
It's wierd that a 15 inch monitor produces the same output as a 12 inch!
 
Compile instructions....
 
First remove the version of xserver-xorg-video-nv you have installed
 
sudo apt-get purge xserver-xorg-video-nv
 
then 
 
sudo nano /etc/apt/sources.list
 
Add temporarily the lines
 
```

deb http://ports.ubuntu.com/ubuntu-ports/ natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe 

```
 
Save (ctrl+o) and close (ctrl+x).
 
Then execute the commands:
```

sudo apt-get update
sudo apt-get install build-essential fakeroot dpkg-dev
mkdir nv-build
cd nv-build 
apt-get source xserver-xorg-video-nv
cd xserver-xorg-video-nv-2.1.17                        
sudo apt-get build-dep xserver-xorg-video-nv
dpkg-buildpackage -rfakeroot -b
cd ..
sudo dpkg -i ./*.deb

```
 
Open the sources.list again and remove the lines you added. Then "sudo apt-get update".
 
Good luck!

---

### Post by BrianWeinberg on 2011-11-27
I don't know enough about the cvt command, but perhaps the results were the same for 'cvt 800 600' because we specified a given resolution, and at that resolution, they might be the same for even different size monitors (stab in the dark, I really don't know anything about the cvt command).

I have tried your instructions, but am unable to proceed beyond the 'apt-get source xserver-xorg-video-nv' line.  That fails with 'E:  Unable to find a source package for xserver-xorg-video-nv' .
I have modified the sources list to add universe restricted multiverse in addition to main.  That seemed to allow me to download xserver-xorg-video-nv' .  The resulting directory was '/nv-build/xserver-xorg-video-nv-2.1.17', in case you needed to know the version number.  From that point on, your instructions worked smoothly.  After doing "Sudo apt-get update", I wasn't sure if you wanted me to run "sudo apt-get upgrade".  I checked what would be available to upgrade, and all that came up was "libv41-0".  I did not run upgrade yet.  After rebooting, I get a whitescreen without the "Linux nouveau.modeset=0".  With the command, success!  I have both the Xubuntu desktop and Ubuntu desktop installed.  Xubuntu works well, and is quite responsive.  Ubuntu seems to work, but is much slower.  Ubuntu 2d seems a little faster than Ubuntu.

I have attempted to modify my yaboot.conf file to permanently disable the nouveau driver.  I did this by modifying the append line as follows:
[INDENT]append="quiet splash video=ofonly nosplash nouveau.modeset=0"[/INDENT]
Obviously, this is incorrect, as it does not disable the driver upon reboot.  Any advice you might have on this would be greatly appreciated.

---

### Post by linuxopjemac on 2011-11-27
good work rsavage! I came across the same problem. 

```
ybin -v 
```
is the answer to yaboot, it has to be written in the Apple bootstrap page

---

### Post by rsavage on 2011-11-27
Hi Brian, sorry about the mistakes I made in the instructions. I should of tested them, but as you may appreciate not having a ppc machine it makes it a bit difficult! Nevertheless, I should of been more thorough. I see the mistake I made now - the nv driver is in the 'main' repository for lucid and maverick, but in the 'universe' one for natty. It is always catching me out that sort of thing! Note to self to remember to double check version numbers of packages!
 
I'm very pleased it worked though. If not delighted!
 
You shouldn't have to run upgrade. Just keep the system updated via the Update Manager. If you are concerned about the libv41-0 package then use sysnaptic package manager to research it a bit more (I know nothing about it). Do you know if it was installed when you insalled the nv driver?
 
I really like xubuntu, although unity in 11.10 is better than it was in 11.04. I may end up creating a hybrid version for myself with global menus in xubuntu. 
 
> 
append="quiet splash video=ofonly nosplash nouveau.modeset=0"

 
It is interesting you have video=ofonly in there. Did you put this in? I would try removing that and see if it makes a difference to the nouveau driver?
 
Other than that your append line looks fine. There are two append lines in the yaboot.conf. Have you made the changes to both? This could be the problem? EDIT: or as linuxopjemac has pointed out you have to always run "sudo ybin -v" to copy the changes across. Thank you. Things quiet in the Mint world linuxopjemac? I thought it was busy over there with MintPPC11? I see jimwg has returned to you!  EDIT2: I see your thread now [http://www.mintppc.org/forums/viewtopic.php?f=15&t=587](http://www.mintppc.org/forums/viewtopic.php?f=15&t=587) .  It seems we are mirroring each others problems!
 
I'll update the compile instructions with your feedback for any future people. Cheers.

---

### Post by linuxopjemac on 2011-11-27
rsavage: We better bundle our strengths instead of fighting... I think we make a good team, sorry about the language in the past.

---

### Post by BrianWeinberg on 2011-11-27
I did not put 'video=ofonly' in there, that is the default.  I only added 'nouveau.modeset=0'.  Just as a test, I tried removing 'video=ofonly', but that just brought back the white screen.  I had entered the 'nouveau.modeset=0' on both yaboot.conf entries before I posted before.  I have replaced the lines as posted before, and ran 'sudo ybin -v'.  By the way, funny line that runs when processing "Blessing /dev/sda2 with Holy Penguin Pee..."  I almost missed that :D

After rebooting, I successfully get a login screen and can proceed to a gui.  That seems to have worked.  I will let you know how I fare with gnash, etc., and see what I can do to compile iMac G4 instructions.  Woohoo!

---

### Post by rsavage on 2011-12-02
Hi Brian, I've finally got around to replying to you!  It's great you've got it all working.  It's been epic!  I do think it might be worth persevering a bit more with nouveau if you have some spare time to test things.  It should give you better performance and maybe necessary for lightspark.  When you enable nouveau (don't have nouveau.modeset=0 and have "nouveau" in xorg.conf) then try and see if you get any error messages in syslog/dmesg logs on boot.  You may have to disable some other framebuffers from loading or force a mode or something to get it working.  Just a few more ideas.....

---

### Post by linuxopjemac on 2011-12-02
Just to let you know that nouveau works out of the box in recent 3.1 kernels...I have nouveau working well on an iMac G5 with an NVIDIA Geforce card in it.

---

### Post by rsavage on 2011-12-02
Nouveau has been working for a long time in Ubuntu (since 10.04 for some models).   I believe it is now just the particular graphics card in Brian's iMac that is problematic.

---

### Post by metzen01 on 2011-12-18
Linux nouveau.modeset=0

 
Thank you for this command.  I'm currently running 12.04 live on my ppc G4.  I'm currently going through the install and will try implementing this when I'm done with the installation.:KS

---

### Post by rsavage on 2011-12-19
Great!  Let us know how you get on with 12.04 and if you get nouveau working properly.  If you need help compiling the nv driver then give us a shout!

---

### Post by metzen01 on 2012-01-31
> **rsavage said:**
> Great!  Let us know how you get on with 12.04 and if you get nouveau working properly.  If you need help compiling the nv driver then give us a shout!
Thanks rsavage I finally have Lubuntu Xubuntu and Ubuntu running on this G4 Quicksilver
 
What I followed:
 
1.) Installed following Rsavages guide here [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1)  up to Section 2.2
 
2.) Ran the nouveau compile instructions from posting 27
 
3.) Made a Xorg.conf file.  I had to adjust my resolution to my screen size for my Mag Innovision LCD but its working.     command      Xorg :1 -configure

 
[FONT=Courier New][SIZE=3]Section "Device"
Identifier "Configured Video Device"
BusID   "PCI:0:16:0"
Driver  "nv"
EndSection

Section "Monitor"
    Identifier    "Mag Innovision"
    Option "DPMS"
    HorizSync   31-80
    VertRefresh 60-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "MAG"
    Device        "Configured Video Device"
        DefaultDepth    24
           SubSection       "Display"
             Depth            24
             Modes             "1024x768" "800x600" "640x480"
           EndSubSection
           SubSection        "Display"
             Depth            16
             Modes             "1024x768" "800x600" "640x480"
           EndSubSection
SubSection "Display"
      Depth      15
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
SubSection "Display"
      Depth      8
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
SubSection "Display"
      Depth      4
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
SubSection "Display"
      Depth      1
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
EndSection

Section "ServerLayout"
   Identifier   "Default Layout"
   Screen      "Default Screen"
EndSection

Section "DRI"
   Mode   0666
EndSection[/SIZE]
[/FONT]
[FONT=Courier New]Placed in /etc/X11[/FONT]
[FONT=Courier New] 
[/FONT][FONT=Courier New] Notice my resolution settings go up to 1024x768.  My screen can go higher but for some reason I would always get a failed X screen and would drop me back to a terminal login window without X starting.[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]Sudo rebooted and did the ybin -v command to place nouveau boot settings into boot strap.[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]I'm pretty happy and hope that your guide helps others like myself out.[/FONT][FONT=Courier New]
[/FONT]

---

### Post by gregounours on 2012-02-03
Hi all,
This thread gets Linux working on iMac g4 but does not solve the underlying problem of nouveau failing to work properly on those machine. Using nv is just a workaround not a long term fix. We need to figure out why nouveau does not work properly.
Nouveau works on pc with nvidia card of the same vintage and the problem exist on all iMac g4 from 700 MHz to 1.25ghz even though they have different card (nv 17 to nv34). The problem is therefore in the Hardware detection and or setup.

 When I try to configure  on my imacg4 1.25 with nv34 card I get the following error: "number of created screens does not match number of detected devices."

The iMac G4 has a DVI port that can only be used to duplicate the built-in screen. Maybe somehow this creates a mix up between the screen and the DVI output. an Xorg.conf file does get created though

There is Gentoo wiki page that mentions phantom outputs creating problem with nouveau:
[http://en.gentoo-wiki.com/wiki/Nouveau#](http://en.gentoo-wiki.com/wiki/Nouveau#) ... tor_issues
That may be something similar to what is happening on iMac G4.

Also I have found a bug report that suggest this may be the issue:
[https://bugs.freedesktop.org/show_bug.cgi?id=21273](https://bugs.freedesktop.org/show_bug.cgi?id=21273)
There is mention of a patch.

Another discussion of nouveau failing on iMac G4 can be found here:
[https://www.libreoffice.org/bugzilla/sh](https://www.libreoffice.org/bugzilla/sh) ... e&id=21273
There is also mention a patch.

Also found some detailed specs of an iLamp here: [https://wiki.ubuntu.com/ILamp](https://wiki.ubuntu.com/ILamp)

Suggestion to fixing this long term problem welcome

PS: I have started a similar discussion on the mintppc11 forum here: [http://www.mintppc.org/forums/viewtopic.php?f=15&t=782](http://www.mintppc.org/forums/viewtopic.php?f=15&t=782)

---

### Post by rsavage on 2012-02-03
> **gregounours said:**
> When I try to configure on my imacg4 1.25 with nv34 card I get the following error: "number of created screens does not match number of detected devices."
 
That's nothing. See the Ubuntu PowerPC FAQ [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_configuring_an_xorg.conf_file.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_configuring_an_xorg.conf_file.3F) .  You can disable phantom outputs outside of an xorg.conf using yaboot parameters too.  It's explained in the FAQ.  
 
I think Conal installed 12.04 on his iLamp using nouveau [http://ubuntuforums.org/showpost.php?p=11651023&postcount=4](http://ubuntuforums.org/showpost.php?p=11651023&postcount=4) .

---

### Post by gregounours on 2012-02-03
How do I get a listed of detected outputs and their names so I can pass to the kernel which one to turn off  as suggested in your link?

---

### Post by linuxopjemac on 2012-02-04
have a look at /var/log/Xorg.0.log for a start...

---

### Post by rsavage on 2012-02-04
If I was looking into this then I'd be booting into single user mode to test. I'd look at the other log files like kern.log, syslog and dmesg . I can't be specific as I don't have nouveau, but one of the links in the FAQ says to look at the kernel log. The Gentoo link says to look in /sys/class/drm.
 
It could be the openfirmware framebuffer offb causing the problem so you could try disabling it [https://wiki.ubuntu.com/PowerPCFAQ#What_yaboot_parameters_should_I_use_for_graphics_problems.3F](https://wiki.ubuntu.com/PowerPCFAQ#What_yaboot_parameters_should_I_use_for_graphics_problems.3F) .

---

### Post by hsiyao on 2012-04-29
[B]Hi everybody!
[/B]
Very glad that I found this thread! I just got my hands on a 'broken' iMac G4 Lamp (700mhz, geforce 2 MX 400), that just needed a dvd and hdd replacement, and I always wanted this machine so I'm already really happy ;)

Now I wanted to get Ubuntu 12.04 to run on it, and this ended in the same graphic problems you can read on a lot of forums. I didn't find a solution yet, but researched the problem a lot but now hit a dead end, a dilemma actually, where my skill level ends. At least I got to understand the different problems with different boot options and one special problem caused by nouveau.

I hope that by sharing all the information I collected somebody with a higher skill level might get to a solution (sorry if something was already said in this thread):

- I used Ubuntu 12.04 LTS, which tries to use niveau as default driver for all nvidia cards, _the "nv" driver is gone_

- _Trying to get the "nv" driver to work would be the logical step, but it's not installable, because of dependency problems_ (breaks packages, maybe this is a point to reasarch further) - so just defining "nv" as driver in the xorg.conf wouldn't change anything

- When booting without any additional boot options, you end up in a white screen that weirdly fades to black. You can't change to a console BUT you can log in externally via ssh. In this case the system actually uses the nouveau driver, but the UI locks up. 

- Since I now kms is sometimes an issue, I deactivated it with nouveau.modeset=0 and the system finally booted, but I got to an screen with weird colors, as mentioned here: [http://ubuntuforums.org/showpost.php?p=11485837&postcount=13](http://ubuntuforums.org/showpost.php?p=11485837&postcount=13) and shown here [http://ubuntuforums.org/showthread.php?t=1917328](http://ubuntuforums.org/showthread.php?t=1917328) 

- Researching this weird problem a bit, I understood how this happened: The Xserver tries to load "nvidia", "nouveau", "nv" and if all this doesn't work falls back to "fbdev" and to make things worse uses it in only 8-bit... but why this fallback when disabling kms?

- I found out that _nouveau actually needs kms to work_ (see here: [http://nouveau.freedesktop.org/wiki/KernelModeSetting](http://nouveau.freedesktop.org/wiki/KernelModeSetting) ), when it is disabled nouveau doesn't work, that's why the Xserver falls back to fbdev in 8bit

- I tried every bootoption I came across but always ended up in fading screens, sometimes white stripes or weird colors

- the only thing people are getting to work is using fbdev with 16 or 24 bit via xorg.con, but then you don't have any acceleration 

>>>> so to make a long story short: you can either use nouveau and end up with a white screen, you can disable kms and end up with 8 bit color depth, you can't install nv. Maybe getting NV to work can be a solution if the dependency problems can be sorted out, latest version here: [http://packages.debian.org/squeeze/powerpc/xserver-xorg-video-nv/download](http://packages.debian.org/squeeze/powerpc/xserver-xorg-video-nv/download)

Hope all this helps somebody to get closer resolving this issue!

---

### Post by hsiyao on 2012-05-04
I downgraded the imac to mintppc 9 (debian based), which roughly has the driver and program versions from ubuntu 11.04. Everything worked out of the box! But I won't give up and would really like to see, that the NV driver is incorparated in Ubuntu again by default. If you think this is a good idea, support it by voting on my ubuntu brainstorm idea:

[[IMG]http://brainstorm.ubuntu.com/idea/29668/image/1/[/IMG]]("http://brainstorm.ubuntu.com/idea/29668/")

---

### Post by rsavage on 2012-05-12
> **hsiyao said:**
> 
>>>> so to make a long story short: you can either use nouveau and end up with a white screen, you can disable kms and end up with 8 bit color depth, you can't install nv. Maybe getting NV to work can be a solution if the dependency problems can be sorted out, latest version here: [http://packages.debian.org/squeeze/powerpc/xserver-xorg-video-nv/download](http://packages.debian.org/squeeze/powerpc/xserver-xorg-video-nv/download)
 

 
You can install nv.  You just need to compile it yourself.  There are instructions to do so in this thread.  These are linked in the PowerPC known issues page and FAQ.  
 
With nouveau have you tried disabling phantum outputs?  Again look at the info and links in the FAQ.
 
To get nouveau working out-of-the-box you should raise bugs with the nouveau developers.  No bug report = no fix.  This would be a better solution than relying on the unsupported nv driver.

---

### Post by hsiyao on 2012-05-13
Hi rsavage and thanks for your answer...

You are absolutely right, that a bugreport should be filed, and I actually got encouraged by one admin at ubuntu brainstorm to do so with great tips on how to do it best... Before that I just didn't know where you could file it in a situation like this... 

regarding compiling your driver on your own: csrunu wrote a great post in this thread with all steps how to accomplish this: [http://ubuntuforums.org/showpost.php?p=11929079&postcount=12](http://ubuntuforums.org/showpost.php?p=11929079&postcount=12)

Right now mintppc 9 is running on the machine, but when I've some free time I gonna try make Ubuntu 12.04 run on it with all the great tips I got in the different forums.

Cheers

Jens.

---

### Post by moore.bryan on 2012-09-03
First, thanks for all the work everyone's put into this thread. I'm running into an issue at > **rsavage said:**
> 
```

dpkg-buildpackage -rfakeroot -b

```

as it tells me "xaa.h: No file or directory."

Any ideas?

---

### Post by rsavage on 2012-09-03
From your other posts I'm guessing you are trying to compile this is 12.10?  XAA has probably been removed in 12.10 [http://www.phoronix.com/scan.php?page=news_item&px=MTA0NDg](http://www.phoronix.com/scan.php?page=news_item&px=MTA0NDg) (that's me speculating, I don't know for certain).
 
There is a new version of nv in debian sid (unstable) I believe [http://packages.debian.org/sid/xserver-xorg-video-nv](http://packages.debian.org/sid/xserver-xorg-video-nv) .  It maybe worth seeing if you can get it back into Ubuntu too?

---

### Post by moore.bryan on 2012-09-03
> **rsavage said:**
> From your other posts I'm guessing you are trying to compile this is 12.10?  XAA has probably been removed in 12.10 [http://www.phoronix.com/scan.php?page=news_item&px=MTA0NDg](http://www.phoronix.com/scan.php?page=news_item&px=MTA0NDg) (that's me speculating, I don't know for certain).
Didn't hear about that... Thanks for the link.

[quote=rsavage] 
There is a new version of nv in debian sid (unstable) I believe [http://packages.debian.org/sid/xserver-xorg-video-nv](http://packages.debian.org/sid/xserver-xorg-video-nv) .  It maybe worth seeing if you can get it back into Ubuntu too?[/QUOTE]
Unfortunately, it won't compile, claiming I don't have xorg installed.

Any other suggestions?

---

### Post by rsavage on 2012-09-04
Is there any particular reason you are using 12.10?  It is a bit of a leap from debian squeeze and your install (from your other posts) doesn't sound like it went well.  Why don't you install 12.04?  nv is supposed to compile in that.
 
The Ubuntu PowerPC FAQ has links for you to read to try and get nouveau working.  You need to investigate phantom outputs/mirroring or whatever other wierdness apple imposed on the card.  Nobody with a 700/800 iMac has done this as far as I am aware.  That is what you should be spending the time on.

---

### Post by moore.bryan on 2012-09-04
> **rsavage said:**
> Is there any particular reason you are using 12.10?  It is a bit of a leap from debian squeeze and your install (from your other posts) doesn't sound like it went well.
No particular reason, it's just what I've used on my netbook since it was alpha.

[quote=rsavage]Why don't you install 12.04?  nv is supposed to compile in that.[/quote]
I think I'll try this. Why in the world would Ubuntu and Debian pull xserver-xorg-video-nv if there are iMacs out there, like mine, which won't play nicely with the nouveau driver?
 
[quote=rsavage]The Ubuntu PowerPC FAQ has links for you to read to try and get nouveau working.  You need to investigate phantom outputs/mirroring or whatever other wierdness apple imposed on the card.  Nobody with a 700/800 iMac has done this as far as I am aware.  That is what you should be spending the time on.[/QUOTE]
That's what I'm planning to do... Debian Sid seems to be a dead-end because their version of nv is for the amd64 and i386 architectures, not powerpc.

---

### Post by rsavage on 2012-10-28
Support for Natty has ended today so I expect the instructions to compile nv in this thread will stop working pretty soon.  Can those with nvidia cards still using nv come up with some alternate instructions for future 12.04 people please?  For example, does compiling the lucid version of nv work okay in 12.04?  Or do you really need the natty/maverick version which you can still find here [https://launchpad.net/ubuntu/natty/+source/xserver-xorg-video-nv](https://launchpad.net/ubuntu/natty/+source/xserver-xorg-video-nv) (note the separate source and patch files).  Please also update the FAQ links with new instructions.

EDIT: I think you would use the dpkg-source command along with the downloaded .dsc file for nv.

---


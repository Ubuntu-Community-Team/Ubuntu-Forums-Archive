---
title: "Setting up Ubuntu 10.04 LTS on PPC G5 Mac ??"
date: 2010-07-12
forum: Apple Hardware Users
---

### Post by 828688 Ben on 2010-07-12
Okay, now that I've at least got Ubuntu 10.04 LTS installed (by the way, I am typing this in Ubuntu) I need to start modifying it to make it the best it can be. 

I was thinking the best place to start is with the display. Right now I have a 1920x1080 display, but in the monitor preferences, the highest resolution that I can do is 1024x768. How do I change/fix this.

P.S.  Keep in mind that I am not an advanced Ubuntu User (I would probably classify myself as intermediate), so keep instruction relatively simple.

Thanks,
Ben

---

### Post by linuxopjemac on 2010-07-12
specs of G5 (everymac.com) and specs of monitor please (link).

---

### Post by 828688 Ben on 2010-07-12
> specs of G5
Hardware Overview:

  Model Name:	Power Mac G5
  Model Identifier:	PowerMac7,3
  Processor Name:	PowerPC G5  (3.0)
  Processor Speed:	2 GHz
  Number Of CPUs:	2
  L2 Cache (per CPU):	512 KB
  Memory:	1.5 GB
  Bus Speed:	1 GHz
  Boot ROM Version:	5.2.4f1

ATA Bus:

PIONEER DVD-RW  DVR-109:

  Model:	PIONEER DVD-RW  DVR-109
  Revision:	A912
  Detachable Drive:	No
  Protocol:	ATAPI
  Unit Number:	0
  Socket Type:	Internal
  Low Power Polling:	Yes
  Power Off:	No

PIONEER DVD-RW  DVR-109:

  Firmware Revision:	A912
  Interconnect:	ATAPI
  Burn Support:	Yes (Apple Shipping Drive)
  Cache:	2000 KB
  Reads DVD:	Yes
  CD-Write:	-R, -RW
  DVD-Write:	-R, -RW, +R, +R DL, +RW
  Write Strategies:	CD-TAO, CD-SAO, CD-Raw, DVD-DAO
  Media:	Insert media and refresh to show available burn speeds

ATI Radeon 9600:

  Chipset Model:	ATY,RV351
  Type:	Display
  Bus:	AGP
  Slot:	SLOT-1
  VRAM (Total):	128 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x4150
  Revision ID:	0x0000
  ROM Revision:	113-A58504-112
  Displays:
HF237:
  Resolution:	1920 x 1080 @ 60 Hz
  Depth:	32-Bit Color
  Core Image:	Hardware Accelerated
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported
  Rotation:	Supported
Display Connector:
  Status:	No Display Connected


> specs of monitor

Part Code: HF237HPBEEL21
Viewable size 23 in
Native resolution 1,920x1,080
Contrast ratio 1,000:1
Brightness 300cd/m²
Horizontal viewing angle 170°
Vertical viewing angle 160°
Response time 5ms
Response time type black-to-black
Screen depth 58mm
Base (WxD) 269x182mm
Screen elevation 102mm


If you need anything else (or I just missed something), please tell me.

Thanks,
Ben

---

### Post by oldfred on 2010-07-12
I do not know if this is still current or not as I have nvidia:

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by 828688 Ben on 2010-07-12
> I do not know if this is still current or not as I have nvidia:

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
Thanks for the suggestion. But before I use this website I would like to get a second opinion from someone who may know a little bit more about ATI drivers (no offense, you may be right, but I just want to be sure).

Thanks for the reply,
Ben

---

### Post by Legal Beagle on 2010-07-12
Ben,

I have very little experience with the G5 platform, but I've been (mostly) successful with my G3 iBooks and G4 Powerbooks -- the G3 iBook had a similar problem where it wouldn't give me the full display options I knew it could support.

I had to try this:

```

sudo nano /etc/X11/xorg.conf

```

I made sure that X in "X11" is capitalized and xorg is lowercase. I then changed the xorg.conf to this:

```

Section "Device"
    Identifier    "Configured Video Device"
    BusID        "PCI:6:3:0"
    Option         "SWcursor" "true"
    Option        "ForcePCIMode" "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync 58-62
    VertRefresh 75-117
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth 24
SubSection "Display"
    Depth 24
    Modes "1024x768"
EndSubSection
EndSection

```

Ctrl-O and return to save it, Ctrl-X and return to exit back out.

It worked for me. 

My guess is that since you already have everything working, you might just need to change the subsection with modes to get the display size you need and be lucky enough that it works.

You might have to get your bus ID before you start poking around in the xorg.conf:
```

lspci | grep VGA

```

Be sure to back it up before you start experimenting. :)

BTW, if you know how to get an Airport card (original, not Express) to work in 10.04 LTS I'm still working on that one. >_<

---

### Post by cariboo on 2010-07-12
To get the proper resolution, especially if your monitor isn't being detected properly, you'll have to set the horizontal and vertical refresh rates in /etc/X11/xorg.conf, as set out on the page oldfred linked to.

Unless you've got the original owners manual for your monitor, you will have to get the correct frequency rates from the manufacturers web site.

There used to be a warning when setting up X, that if you set the refresh rates wrong your monitor could blow up. :)

---

### Post by 828688 Ben on 2010-07-12
[SIZE=1]Okay Here are the frequencies for my monitor:

[/SIZE]Horizontal Frequency[SIZE=1]: 24kHz to 83kHz
Vertical Frequency: 50Hz to 75Hz

I have the xorg.config file modified to allow 3d acceleration!
Here Is what it looks like:

Section "Device"
    Identifier    "Radeon 9600"
    Driver        "ati"
    Option        "DynamicClocks" "true"
    Option        "AGPMode" "4"
    Option        "AGPFastWrite" "true"
    Option        "UseFBDev" "false"
    Option        "DRI" "true"
    Option        "GARTSize" "64"
    Option        "AddARGBGLXVisuals" "true"
    Option        "XAANoOffscreenPixmaps"
    Option        "DisableGLXRootClipping" "true"
    Option        "AllowGLXWithComposite" "true"
    Option        "EnablePageFlip" "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Radeon 9600"
    Monitor        "Configured Monitor"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection  


However I am not able to change my monitor preferences to 1920x1080 with this. What should I add to this file to allow 1920x1080 resolution?


Thanks,
Ben 

[/SIZE]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     [SIZE=1]
[/SIZE]                                                                                                                                                                                                                                                                                              [SIZE=1]
[/SIZE]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             [SIZE=1]
[/SIZE]

---

### Post by cariboo on 2010-07-12
You need to add HorizSync and VertRefresh rates to the monitor section.

---

### Post by 828688 Ben on 2010-07-12
Okay, Great news. After several different attempts, I got my monitor working beautifully!! Here are my Settings for xorg.conf:

Section "Device"
    Identifier    "Radeon 9600"
    Driver        "ati"
    Option        "DynamicClocks" "true"
    Option        "AGPMode" "4"
    Option        "AGPFastWrite" "true"
    Option        "UseFBDev" "false"
    Option        "DRI" "true"
    Option        "GARTSize" "64"
    Option        "AddARGBGLXVisuals" "true"
    Option        "XAANoOffscreenPixmaps"
    Option        "DisableGLXRootClipping" "true"
    Option        "AllowGLXWithComposite" "true"
    Option        "EnablePageFlip" "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"    
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Radeon 9600"
    Monitor        "Configured Monitor"
    DefaultDepth 24
SubSection "Display"
    Depth 24
    Modes "1920x1080"
EndSubSection
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection  


Here is my next question:

How do I change the brightness and contrast settings in Ubuntu? 
When I searched Ubuntu Software Center for a program to do that, I found this program called Monitor Settings:
 > 
Monitor Settings
Set your monitor preferences (contrast, brightness,...) and
manage your profiles

To show information about this item, the software catalog needs updatingSo how do I download this program and what does  "the software catalog needs updating" means?

Thanks,
Ben

---

### Post by cariboo on 2010-07-12
All my monitors have onscreen controls for brightness and contrast, so I've never needed a utility to set them.

To update the repositories go to System->Administration->Synaptic Package Manager, and hit the reload button.

---

### Post by 828688 Ben on 2010-07-13
Unfortunately that did not work....

Here is what it looks like:
[IMG]http://lh5.ggpht.com/_FI33gwIVx5s/TDyL4hK-qQI/AAAAAAAAATw/uJjV7l-kBQI/Screenshot.png[/IMG]

Do you have any ideas how I can install this program? Can I use a terminal command or something else?

Thanks,
Ben

---

### Post by cariboo on 2010-07-13
Go to System->Administration->Synaptic Package manager and search for gddccontrol, and install it from there.

---

### Post by 828688 Ben on 2010-07-13
Tried it, and found nothing.
[IMG]http://lh6.ggpht.com/_FI33gwIVx5s/TDyUir9fUBI/AAAAAAAAAT4/A2f02gK3nhE/s800/Screenshot-1.png[/IMG]

Maybe it's called something else?

Thanks,
Ben

---

### Post by avtolle on 2010-07-13
Unfortunately, this may be an app that hasn't been maintained or one that is "Intel only". I would guess the latter.

EDIT: I meant "the former". Sorry.

---

### Post by 828688 Ben on 2010-07-13
Do you know of any program that will allow me to change the brightness and contrast?

Thanks,
Ben

---

### Post by 828688 Ben on 2010-07-13
Never mind that last reply, NEW TOPIC:

Do you how I can get flash to work on my computer (I'm mainly talking about for my firefox browser)?

Thanks,
Ben

---

### Post by 828688 Ben on 2010-07-13
Here's what happens when I try "sudo apt-get install flashplugin-nonfree" :
> ben@Bens-Ubuntu:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
ben@Bens-Ubuntu:~$ 
Any ideas?


Thanks,
Ben

---

### Post by cariboo on 2010-07-13
It looks like you don't have all the repositories enabled in System->Administration->Software Sources. gddccontrol is in the universe repository. Flash is in the multiverse.

---

### Post by 828688 Ben on 2010-07-13
Are you sure thats the problem?
[IMG]http://lh5.ggpht.com/_FI33gwIVx5s/TDy1k9sNbiI/AAAAAAAAAUA/91alUQSu54U/s800/Screenshot-2.png[/IMG]

What am I doing wrong?

Thanks,
Ben

---

### Post by Legal Beagle on 2010-07-13
I'll defer on the issue of brightness/contrast, but I'm almost positive that the flash plugin will not work on the PPC architecture.

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

> 
[...]There is no Adobe Flash for PowerPC Linux but there  are two free open source projects aiming to create a functional  alternative - **Gnash** and **swfdec**. Both of these work to a degree.  Most simple flash  animations work well, and sites such as  youtube.com, lulu.tv and  revision3.com have varying success. These  plugins are found in Synaptic under the names mozilla-plugin-gnash  and swfdec-mozilla.  (Note: Use konqueror-plugin-gnash  instead in Kubuntu.) [...]



My attempts to get Flash to work from the adobe site resulted in a "package is virtual" error message so I had to try one of the suggested alternatives.



 Of the two, I like Gnash better but YMMV.

---

### Post by 828688 Ben on 2010-07-13
Well it looks like this flash thing on PPC mac (G5) is a bigger, more well know problem than I thought. So, I made a whole new thread just for it:

[http://ubuntuforums.org/showthread.php?p=9585266#post9585266](http://ubuntuforums.org/showthread.php?p=9585266#post9585266)

If anyone has any solutions, ideas, or suggestions, [B]please post on the new thread listed above!

[/B]Thanks,
Ben

---

### Post by linuxopjemac on 2010-07-13
Try the xgamma -gamma number command (number=0.7-1.0; I have no experience with it though):
[http://ubuntuforums.org/showthread.php?t=301434](http://ubuntuforums.org/showthread.php?t=301434)

I also vaguely remember xbacklight:
xbacklight =50 to set the screen brightness to 50%

xbacklight +10 to increase

xbacklight -10 to decrease

---

### Post by 828688 Ben on 2010-07-13
Thanks, worked great! 

---
Ben

---

### Post by avtolle on 2010-07-13
Flash is not available for PPC Linux, sorry to say. There is a script to add (w/Greasemonkey) to allow one to view YouTube vids on Firefox; and, there is Download Helper, among other FF extensions, to d/l and convert flash videos. I seem to recall other approaches. Gnash is "under development"; there is swfdec in the repos as well, both give limited (in my experience) flash functionality, you could give either a try. Good luck.

---

### Post by linuxopjemac on 2010-07-13
Ben: which command worked for you ?

---

### Post by sha.goyjo on 2010-07-13
swfdec is pretty much unmaintained anymore, so I'd definitely go with gnash for the forseeable future. Lightspark would be great if it ever gets ported, but I'm not crossing my fingers.

Gnash works well for many pieces of simple, non-video flash. As for videos, you have to use greasemonkey scripts to play them in totem or vlc. Or just wait till youtube goes html5 ogg :-)

Not crossimg my fingers there either.

---

### Post by 828688 Ben on 2010-07-14
> Ben: which command worked for you ?
The "xgamma -gamma 0.8" command that I found in the link that you gave me. I have not yet tried "xbacklight +10 to increase

xbacklight -10 to decrease"

> Gnash works well for many pieces of simple, non-video flash. As for videos, you have to use greasemonkey scripts to play them in totem or vlc.
Could you explain to me (if its pretty complicated, try to make  it as step by step as possible) how to use greasemonkey scripts to play them in vlc?

P.S.  I am using the firefox as my web browser.


Thanks,
Ben

---

### Post by 828688 Ben on 2010-07-17
I can't get mp4 videos to play in vlc player? 
Here is the command I used to install vlc player (the installation appeared to work fine):
> sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc


I click on the program. It starts fine. I go to media > open file. The file opens and I get a black screen, but I do here sound. 

What am I doing wrong? Is there a plugin, or something else I need to install?


Thanks,
Ben

---

### Post by linuxopjemac on 2010-07-17
I guess you need an mp4 (quicktime) codec. Search synaptic package manager...

---

### Post by 828688 Ben on 2010-07-17
I tried that search for both mp4 and quicktime and I came up with quite a few results. I'm not sure exactly what I'm looking for.

Thanks for the help,
Ben

---

### Post by linuxopjemac on 2010-07-17
I will try a bit here, I never look mp4...

---

### Post by linuxopjemac on 2010-07-17
I have the following programs installed (this is Intel by the way...)

---

### Post by 828688 Ben on 2010-07-17
Same here:
[IMG]http://lh5.ggpht.com/_FI33gwIVx5s/TEJHDc999oI/AAAAAAAAAUo/R_-O1mH0xTU/s576/Screenshot.png[/IMG]

Have any idea why it's not working for me?

Thanks for the help,
Ben

---

### Post by 828688 Ben on 2010-07-17
Okay, its not just mp4 files that won't play. I have tried flv and 3gp movies on vlc player and movie player. Everything that I try ends the same way. No video (black screen) and sound (sound always works fine).

Is this because I am using a PowerPc processor?


Thanks,
Ben

---

### Post by 828688 Ben on 2010-07-17
FYI: I have made a new (more detailed) thread for this specific topic.

Thread: [http://ubuntuforums.org/showthread.php?t=1533344](http://ubuntuforums.org/showthread.php?t=1533344)


Thanks,
Ben

---


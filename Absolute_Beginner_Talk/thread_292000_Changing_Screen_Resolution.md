---
title: "Changing Screen Resolution"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by pilgrim-online on 2006-11-03
I have been searching this site for some time and discovered plenty of threads on screen resolution but I cannot find one to help.

I have an Intel 865G Chipset, in Windows I use a resolution of 1152x864.
In the screen resolution options in Ubuntu 6.06 this does not appear.
Although following some of the other posts I have read I have found that it is listed in the configuration files.

The two options either side are not really suitable 1280x1024 makes things too small and after a while causes headaches due to eye strain, 1024x768 makes things too big.

Can anyone tell me [in simple terms] how I can get to use my preffered option please?

A solution would make a considerable difference to my use of Ubuntu.

---

### Post by taurus on 2006-11-03
Backup your original /etc/X11/xorg.conf before you edit.  Then, edit it with a editor and add "1152x864" to the resolution lines in /etc/X11/xorg.conf, placing it in front of all those other resolutions...

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
gksudo gedit /etc/X11/xorg.conf
```
Reboot and see if you get what you want.

---

### Post by pilgrim-online on 2006-11-03
taurus,

Tried the first command and it refused, said something about needing a file name.
Tried the second and edited as suggested, then got the following:

[COLOR="Red"]None of the authentication protocols specified are supported and host-based authentication failed.[/COLOR]

Edited the file back to the original.

I should mention that there are 7 settings listed in the configuration file, 1152x864 being the second highest.
Only 4 of them appear in the options window.

---

### Post by pilgrim-online on 2006-11-05
I am bringing this up again because it is the biggest problem I have with using Ubuntu.

If the resolution I am looking for cannot be accessed from within Ubuntu itself does anyone know of any third party software that might do the job?

---

### Post by taurus on 2006-11-05
I assume you know that is a capital **[SIZE="4"]X[/SIZE]** with number 11 after as in /etc/X11/xorg.conf!!!

---

### Post by brummygem on 2006-11-05
Hello, I have a related problem.  My chiset is an Intel 845G and my prefered resolution, 1024 x 768, is listed.  However, when I select this and try to apply it, the screen changes briefly then flashes and returns me to the log-in page where the resolution is back at the default of 1280 x 1024.  Maybe should have started another thread but there are so many of them and none seem to answer my problem.

---

### Post by taurus on 2006-11-05
> **brummygem said:**
> Hello, I have a related problem.  My chiset is an Intel 845G and my prefered resolution, 1024 x 768, is listed.  However, when I select this and try to apply it, the screen changes briefly then flashes and returns me to the log-in page where the resolution is back at the default of 1280 x 1024.  Maybe should have started another thread but there are so many of them and none seem to answer my problem.
Have you reconfigured your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by brummygem on 2006-11-05
Just tried that and ended up with a black screen and had to switch off and re boot.  As you will see, I am a complete noob (and elderly with it) so please have patience

---

### Post by taurus on 2006-11-05
Do you get the resolution, 1024x768, when you boot your machine using the LiveCD?  If you do, perhaps you can copy the /etc/X11/xorg.conf from the LiveCD to your harddrive...

---

### Post by bodhi.zazen on 2006-11-05
You need to install and configure 915resolution.

[How to monitor resolution](http://ubuntuforums.org/showthread.php?t=269052)

Here is the how to I wrote, see the **_intel section**_ near the bottom of the post.

---

### Post by brummygem on 2006-11-05
> **taurus said:**
> Do you get the resolution, 1024x768, when you boot your machine using the LiveCD?  If you do, perhaps you can copy the /etc/X11/xorg.conf from the LiveCD to your harddrive...

To be honest, never tried to change the resolution when booting from the live CD?

---

### Post by ljpm on 2006-11-05
> **brummygem said:**
> Just tried that and ended up with a black screen and had to switch off and re boot.  As you will see, I am a complete noob (and elderly with it) so please have patience

Hi brummygem, 

I had a slightly different problem with my video settings but the solution may be the same. When I started gcompris the screen went blank. It seems the refresh rate was set to high for the gcompris default screen resolution. 


Before I reconfigured xserver-xorg as suggested by taurus I found the Hscan and Vscan ranges for my flat panel. Then when I reconfigured xserver-xorg I entered these values. Problem solved.

Additionally, when you reconfigure xserver-xorg it gives you the option of selecting the screen resolutions you would like to have available. Make sure you have selected the ones you want and don't just chose the defaults.

---

### Post by brummygem on 2006-11-05
> **ljpm said:**
> Hi brummygem, 

I had a slightly different problem with my video settings but the solution may be the same. When I started gcompris the screen went blank. It seems the refresh rate was set to high for the gcompris default screen resolution. 


Before I reconfigured xserver-xorg as suggested by taurus I found the Hscan and Vscan ranges for my flat panel. Then when I reconfigured xserver-xorg I entered these values. Problem solved.

Additionally, when you reconfigure xserver-xorg it gives you the option of selecting the screen resolutions you would like to have available. Make sure you have selected the ones you want and don't just chose the defaults.

Someone else, in another thread, suggested the refresh rate may be too high but I can't alter it in the resolution screen?  I have no idea how to find my Hscan and Vscan ranges:(

---

### Post by bodhi.zazen on 2006-11-05
> **brummygem said:**
> Someone else, in another thread, suggested the refresh rate may be too high but I can't alter it in the resolution screen?  I have no idea how to find my Hscan and Vscan ranges:(

You need to do a google search on your monitor.

---

### Post by taurus on 2006-11-05
Do you still have the manual for your monitor?  Some monitors print those number on the back of the monitors!  Otherwise, what is the manufacture and model of your monitor then?  You can look it up o the web...

---

### Post by brummygem on 2006-11-05
People, people, please forgive an old fart for being stupid.  The problem all along is that I wasn't confirming that I wanted to keep the new resolution.](*,) :( .  changed the resolution, confirmed that I wanted to keep it and everything is now spot on.  So sorry for being a dope :-? :D :D :D

---

### Post by pilgrim-online on 2006-11-06
It seems I raised an issue that interests a lot of people.

I have just spent two hours trying different changes to my xorg.conf file.
I am now back where I started.

My conclusion at the moment is that what I put in my second post is the literal truth, 1152x864 is not supported in Ubuntu.

I actually got the options menu to show that resolution, but when it is applied you have to scroll the screen in both directions, even for the Desktop.

The 7 sizes that show in the configuration are those that my graphics are capable of, not what appear to be available in Ubuntu.

Having read through what has been added to this thread since I last looked I am going to have another look at xserver-xorg, but when I checked that before I could not see anything that needed changing.

---

### Post by pilgrim-online on 2006-11-06
Back again.

I cannot see anything that I can change that I have not already tried.
I have looked in both Ubuntu and Kubuntu and everything appears the same.

Seems like my use of Ubuntu is going to be very limited unless I can find an answer to this.

---

### Post by bodhi.zazen on 2006-11-06
> **pilgrim-online said:**
> Back again.

I cannot see anything that I can change that I have not already tried.
I have looked in both Ubuntu and Kubuntu and everything appears the same.

Seems like my use of Ubuntu is going to be very limited unless I can find an answer to this.

That is odd. 915 resolution works for most with your chip set. (editing xorg.conf does not).

Did you follow my instructions on installing and configuring 915resolution?

---

### Post by mahy on 2006-11-06
> **pilgrim-online said:**
> It seems I raised an issue that interests a lot of people.

I have just spent two hours trying different changes to my xorg.conf file.
I am now back where I started.

My conclusion at the moment is that what I put in my second post is the literal truth, 1152x864 is not supported in Ubuntu.


Sorry, but that's a literal bull....  Do you have fglrx drivers installed? Can you post your xorg.conf?

Anyway, please please forget about changing resolution in some menu. Don't mention it again.

---

### Post by pilgrim-online on 2006-11-06
**bodhi.zazen,**

Yes tried 915resolution even to the point of editing /rc.local, no difference.

**mahy,**

If you can prove me wrong you will make me very happy.
In answer to your first question, I have no idea.
In answer to your second question, I may not have time to go back into Ubuntu today, [I am using Windows at the moment], but I will post the file[s] tomorrow.
I appear to have an xorg.conf file and a xorg.conf1 file that are not the same, I will try and copy both.

---

### Post by ljpm on 2006-11-06
> **pilgrim-online said:**
> 

My conclusion at the moment is that what I put in my second post is the literal truth, 1152x864 is not supported in Ubuntu.



1152x864 is supported. The first image is the resolution I normally use, 1280x1024. As you can see I can select 1152x864.

The second image is my screen at 1152x864. 

Everything works fine.

---

### Post by ljpm on 2006-11-06
pilgrim-online  

What monitor are you using.

What are the Hscan and Vscan ranges.

When you run 

```
sudo dpkg-reconfigure xserver-xorg
```

It will attempt to detect your monitor. In my case this did not work and I had to enter the Hscan and Vscan ranges manually during the reconfiguration.
(my monitor is Sony 17" SDM-HS75P)

Also, during the reconfiguration it will prompt asking which resolutions you wish to have available. Make sure you select 1152x864 (in my case this was selected).

---

### Post by pilgrim-online on 2006-11-07
Right, I have regained the default xorg.conf file which shows as follows:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"19''"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

The monitor is a Suyama 19" TFT the refresh rates are 20-80 and 50-75.

I also have three extra xorg.conf files that I would like to delete but do not know how?

I have just run sudo dpkg-reconfigure xserver-xorg and for the first time discovered 1152x864 which I ticked, but it is still not showing up as an option?

As I have said elsewhere, until two weeks ago I had never even seen a Linux OS.
So any help is greatly appreciated.

---

### Post by ljpm on 2006-11-07
> **pilgrim-online said:**
> 
The monitor is a Suyama 19" TFT the refresh rates are 20-80 and 50-75.

I also have three extra xorg.conf files that I would like to delete but do not know how?

I have just run sudo dpkg-reconfigure xserver-xorg and for the first time discovered 1152x864 which I ticked, but it is still not showing up as an option?

As I have said elsewhere, until two weeks ago I had never even seen a Linux OS.
So any help is greatly appreciated.


Don't give up. You will get it working. 

I also am new to Linux. I first tried to install Ubuntu in July. I also had problems with my video card and with xorg.conf. 

You xorg.conf looks like mine. I also do not have 1152x864 listed in my xorg.conf but I am able to set that as my resolution. 

I noticed that you have Monitor "19''" in your xorg.conf but not Hscan or Vscan ranges.  

Take a look here.
[http://xorg.freedesktop.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://xorg.freedesktop.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

> The Identifier entry specifies the unique name for this monitor. The Monitor section provides information about the specifications of the monitor, monitor-specific Options, and information about the video modes to use with the monitor. 

You have "default screen" listed for your Identifier. Your monitor was not detected. You will most likely have to run xserver-xorg again paying particular attention to the monitor configuration. (have your manual handy)

Hope this helps. (from one noob to another, it is amazing what you can learn in a couple of months of screwing around with your system)

---

### Post by pilgrim-online on 2006-11-07
Thanks for the reply.
I have looked at that link and it might as well be in Chinese for what I can make of some of it.

When I ran xserver-xorg it picked up a lot of things automatically.

"The Identifier entry specifies the unique name for this monitor."
Given that I only have one monitor I would have thought that 'default screen' was acceptable?
Everything else in that section was picked up by the system.
When I go back into Ubuntu, probably not until tomorrow, I will have a look at the Monitor Section in that file and see what that says.

Thanks.

---

### Post by pilgrim-online on 2006-11-08
Having looked at and edited the Monitor Section it now reads as follows:

Section "Monitor"
	Identifier	"19''"
	Option		"DPMS"
	HorizSync	20-80
	VertRefresh	50-75
EndSection

I am still no closer to getting the right resolution but I shall keep trying.
In the meantime if anyone has any further ideas I would be pleased to hear them.

---

### Post by polly1 on 2006-11-08
Hi

You can update to Ubuntu 6.10(Edgy) because you can adjust the the resolution to 1152 x 864 by System>Preferences>Screen Resolution. I have just done this,so it does work. You will solve your problem by doing so.

If you decide to do this I suggest you do a clean install, because from my experience, it is better than updating. This distro may not be as stable as Dapper, but I have not had any problems with it. Follow the Ubuntu tab at the top of the page to get further info. on installation etc.

---

### Post by pilgrim-online on 2006-11-09
polly,

Thank you for your post, unfortunately to do as you suggest would defeat the reason I chose 6.06 in the first place, because it is an LTS version.
Perhaps someone who is developing 6.10 might see this and come up with a way of adding whatever method they use into 6.06.

The most recent thing I have tried was to change the depth to 16, when I did 1152x864 actually appeared in the options list and I checked it, but when I rebooted the desktop was in the centre of the screen with a large black border all round it.
It looked as if the screen itself was still at 1280x1024 while the desktop image was at 1152x864?

Does anybody with 6.06 actually use 1152x864? If so I would be interested in seeing your configuration file.

---

### Post by Hubris2 on 2006-11-10
I'm having a similar problem....I have an Nvidia 6800GT card and a Dell 2405 LCD.  I've loaded the Nvidia X-server, and it does properly detect both my card and my monitor, however I have no resolutions about 1280x1024.  I've tried manually updating the xorg.conf with 1920x1200 and after a reboot my available options haven't changed.  Any ideas?

---

### Post by ruchie on 2006-11-10
[QUOTE]Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
    Driver        "nv"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "AOC Spectrum"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
    Monitor        "AOC Spectrum"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x760" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x760" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection[/QUOTE


its my first time to use a diff OS, can any one help me this is my xorg, i added 1024x760 but still i cannot change my screen resolution.. can anybody help me.. i've tried auto ditecting it.. but it doesnt work.. thnx in advance

---

### Post by bodhi.zazen on 2006-11-10
> **Hubris2 said:**
> I'm having a similar problem....I have an Nvidia 6800GT card and a Dell 2405 LCD.  I've loaded the Nvidia X-server, and it does properly detect both my card and my monitor, however I have no resolutions about 1280x1024.  I've tried manually updating the xorg.conf with 1920x1200 and after a reboot my available options haven't changed.  Any ideas?

How did you install the nvidia drivers? Here is a guide: [Nvidia drivers](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by bodhi.zazen on 2006-11-10
> **ruchie said:**
> its my first time to use a diff OS, can any one help me this is my xorg, i added 1024x760 but still i cannot change my screen resolution.. can anybody help me.. i've tried auto ditecting it.. but it doesnt work.. thnx in advance

Try installing the nvidia drivers.

---

### Post by Hubris2 on 2006-11-10
To be honest I installed the Nvidia drivers using Automatix.  Do you think I'd have different luck if I followed the guide and did it manually?

> **bodhi.zazen said:**
> How did you install the nvidia drivers? Here is a guide: [Nvidia drivers](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by bodhi.zazen on 2006-11-10
> **Hubris2 said:**
> To be honest I installed the Nvidia drivers using Automatix.  Do you think I'd have different luck if I followed the guide and did it manually?

I am not sure. Did you re-start X after installing ? You need to re-start X after editing xorg.conf.

Try this:

[list=number][*]Backup your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

[*]Then:```
dpkg-reconfigure -phigh xserver-xorg
```

[*]Last: Enable the driver in your xorg:```
sudo nvidia-xconfig
```[/list]

And see what you get.

---

### Post by Hubris2 on 2006-11-11
I get.....exactly what I wanted.  When I was reconfiguring the Xserver it allowed me to select the resolutions I wanted to use.  I'm now running full resolution, multiple windows just like I'm used to.  Thanks!!!

Now...if I can just find someone so helpful in one of my 'sound detected but no sound' threads....:)

---

### Post by bodhi.zazen on 2006-11-11
> **Hubris2 said:**
> I get.....exactly what I wanted.  When I was reconfiguring the Xserver it allowed me to select the resolutions I wanted to use.  I'm now running full resolution, multiple windows just like I'm used to.  Thanks!!!

Now...if I can just find someone so helpful in one of my 'sound detected but no sound' threads....:)

Perhpas this: [Comprehensive Sound Problems Solutions Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by Hubris2 on 2006-11-11
Yeah, I've read the first few pages of that thread....I'll have to go through it some more tomorrow.  At least my apps and video seem to be right.

---

### Post by pilgrim-online on 2006-11-11
I'm glad that someone got what they wanted.

---

### Post by Heous on 2006-11-11
Hello.  Sorry to bump this topic, but I'm having a similar problem to this one.  The problem for me is that I'm stuck at a maximum of 1024x768 screen resolution and a refresh rate of 60 hZ, which I cannot change.  I would like to be able to change my resolution to 1280x1024, and to set my refresh rate higher.  I don't really understand what was being discussed about editing configuration files, so step-by-step help would be appreciated.  Thank you.

---

### Post by bodhi.zazen on 2006-11-11
> **Heous said:**
> Hello.  Sorry to bump this topic, but I'm having a similar problem to this one.  The problem for me is that I'm stuck at a maximum of 1024x768 screen resolution and a refresh rate of 60 hZ, which I cannot change.  I would like to be able to change my resolution to 1280x1024, and to set my refresh rate higher.  I don't really understand what was being discussed about editing configuration files, so step-by-step help would be appreciated.  Thank you.

Start with this link. If ou have questions/problems, re-post: 
[Monitor resolution](http://ubuntuforums.org/showthread.php?t=269052)

---


---
title: "A stab at getting ATI to work"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-06-13
Hi!

I really struggled with this for a long time. This is info I compiled from many people. Superm1 is responsible for most of the general explanations and NemesisUK for the Edgy Stuff. Please note that the general bog standard installation follow here. If you wish to have the latest and the greatest, read the second method.

Print/write down these command. Then restart you machine, at the boot menu choose recovery mode, this will keep the X system from loading and free you to do as you please with the graphics. If you log in as root, there's no need to "sudo" anything. If you log in as yourself, "sudo" everything. Here's the drill:

[COLOR="Blue"]METHOD 1[/COLOR]

1) Add the restricted repository to your list.

This is because by default Ubuntu doesn't have anything that is nonfree/nonopensource. To get around licensing problems but easily allow users to add nonfree stuff, they created an extra repository called "restricted".

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

2) Copy and paste these Commands:
> 
sudo apt-get update

After adding restricted to your list, this will update the list of available packages to include restricted.


> sudo apt-get install linux-restricted-modules-$(uname -r) 

Install all of the restricted kernel modules. The restricted module of concern here is called fglrx. The way that linux does drivers is by removable "modules" that load into the kernel. At any time, you can pull up a Terminal and type "lsmod" to see all the loaded modules. Fglrx is the ATI propietary driver that loads into the kernel.


> 
sudo apt-get install xorg-driver-fglrx

This installs all of the opengl & x11 related items for the driver as well as any binaries that ATI distributes with the driver.

This package is seperate from the linux-restricted-modules package because if a kernel update comes out, then you don't need to reinstall all of the opengl,x11, and ati binaries. Instead, the only thing that would change is the kernel module which comes in linux-restricted-modules.
> 
sudo depmod -a


This updates the list of available kernel modules to reflect fglrx being added. It can actually be done before installing xorg-driver-fglrx.

> sudo aticonfig --initial

This reads in your initial /etc/X11/xorg.conf. It then parses it and updates it to change anything required for fglrx. aticonfig actually has lots of other options that you can set up as well including but not limited to multiple displays and power management. If your curious run aticonfig --help to see.
> 
sudo aticonfig --overlay-type=Xv

This enables the video overlay to be handled by Xv. Video overlays can be handled either by Xv, X11, or opengl. X11 is the straight X11 windowing protocol. If you use this, most higher resolution videos will play pretty horribly. Xv stands for XVideo. It is the defacto standard for video playback, so if your driver supports it, you should use it. Opengl plays back your video in an opengl texture. This can be good in some cases, but you would have to experiment with it a bit.

Restart your machine 

> sudo shutdown -r now

Verify in gnome that it has worked:

> rudolf@rudolf:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6119 (8.30.3)

rudolf@rudolf:~$ 


If you still get MESA after this, then try it again, and if still no change, then post for help and I'll try and help you sort it out!



[COLOR="Blue"]METHOD 2 (Modified for EDGY EFT)[/COLOR]

Just a couple of notices for Edgy users:

1)> 
As of driver version 8.29.6 support for the following products is no longer included:

    * Radeon® 8500/9000/9100/9200/9250
    * Mobility™ Radeon® 9000/9100/9200
    * Radeon® IGP 9000/9100/9200

Users with these products should use driver version 8.28.8


2)Originally posted by Yummy

> The fact is that edgy is aiglx compatible. Hence this cause such issue with ATI GPU.
SO for now to use fglrx you have to edit the xorg.conf to add at the end :

[QUOTE]Section "Extensions"
Option "Composite" "disable"
EndSection

Then restart X.

PS: so if you want to use compiz/beryl this will be done thru Xgl and not aiglx for ati cards.

Regards, yummy.
[/QUOTE]



Edgy users can follow Method 1 but when you want the latest and the greatest drivers, checkout the ati website and download the 50mb installer:

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

Any user, from Breezy to Edgy can use this to install the latest ati drivers, Edgy users just need to make a slight modification to there system in order for it to work.

Ati haven't made there installer Edgy compatible, when you try and run the installer you'll get an error. In order to run the installer(Only Edgy Users do this):
> 
sudo mv /bin/sh /bin/sh.backup
sudo ln -s /bin/bash /bin/sh


Now you can start the install. 

(Breezy and Dapper people begin here)

You can now set you working directory to the folder containing the ati installer, ie, 
cd /home/you/Desktop and do the following:

> sudo apt-get install debhelper build-essential module-assistant linux-headers-$(uname -r)
sudo sh ati-driver-installer*.run --buildpkg Ubuntu/dapper or edgy
sudo dpkg -i *.deb
sudo module-assistant build,install fglrx
sudo aticonfig --initial --resolution=0,1280x1024 or whatever resolutions you want seperated by commas.

Now, open your xorg.conf file(Only Edgy users):

> sudo nano /etc/X11/xorg.conf

and append the following to the end of it,

> Section "Extensions"
Option "Composite" "disable"
EndSection

Exit and save your changes by pressing CTRL+x and typing "yes".

Restart your machine and verify that it has worked:

> sudo shutdown -r now

> 
Rudolf@rudolf:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6119 [COLOR="Red"](8.30.3)[/COLOR]

Edgy users, after the install, you have to reverse the changes that you made to the sh command:

> sudo rm /bin/sh && sudo mv /bin/sh.backup /bin/sh

I hope that this will help people get there Ati cards to work!

Any troubles, post here and I'll try and help where I can! :)

Best of luck,

Cheers,

Rudolf

---

### Post by Patrick-Ruff on 2006-06-13
thanks, this helped me alot.

---

### Post by RudolfMDLT on 2006-06-14
[QUOTE=Patrick-Ruff]thanks, this helped me alot.[/QUOTE]
:D  I'm glad!

---

### Post by DonQuixote on 2006-06-15
Well, I tried this and I get the fatal double drum sound on the login screen.  When I login I get a blank screen with the mouse pointer in the center.  My computer doesn't freeze.  I can move the mouse, but that's it.

I had this happen on Breezy with the latest drivers, and had to revert to an earlier version of the ATI drivers.  I don't have that option with Dapper as the drivers that worked in Breezy require xorg 6.X.0 where Dapper uses xorg 7.0.0.

So, it looks like I'm back to Breezy for a while. >sigh<

---

### Post by RudolfMDLT on 2006-06-15
Exactly what card are you running?

---

### Post by patrick295767 on 2006-06-15
some links ... :

[http://wiki.ubuntu-it.org/Enable3DAtiRadeon%28fglrx%29#head-6513ce370fed8d5efb9fc612daa23c207614cbff](http://wiki.ubuntu-it.org/Enable3DAtiRadeon%28fglrx%29#head-6513ce370fed8d5efb9fc612daa23c207614cbff)

[http://www.ubuntuforums.org/showthread.php?t=186824](http://www.ubuntuforums.org/showthread.php?t=186824)

---

### Post by DonQuixote on 2006-06-15
Rudolf,

I have an ATI 9600 Radeon Mobility in my Sager 5680 laptop.

---

### Post by DonQuixote on 2006-06-15
Ah, Patrick,

I'm sure if I could read Italian I would understand what that instructions on that first link say.  Is there an *English* version?

---

### Post by RudolfMDLT on 2006-06-15
Hi, 

You piratically run the same thing as myself.

Firstly, did you restart into recovery mode and then apply the settings?

secondly, I went goofing around and got sort of the same symptoms when loading opengl as my overlay.

try loading X11 as your overlay, it's slower but should be more stable.

aticonfig &#8211;overlay-type=X11

Even when applying small changes like this, please restart into recovery mode and apply them there.

Hope this helps.

EDIT: the first post is a replica of the original WIKI article which is a replica of the original ATI article. The only reason that I posted it again was because superm1 explained what every line means so that people can understand what they are doing. - I believe the Italian version is a copy of the english version on the wiki.

---

### Post by DonQuixote on 2006-06-15
Did everything from "recovery" mode, rebooted, and entered "fglrxinfo".  I get this error:

"Error: unable to open display :0"

Ever get that?

---

### Post by RudolfMDLT on 2006-06-16
Error: unable to open display :0 - Yeah, when I type fglrxinfo in Recovery mode. When you type it in the terminal, in gnome, what does it say ?

---

### Post by DonQuixote on 2006-06-17
I can't even get to Gnome to try it, without changing in recovery mode the driver back to "vesa".

---

### Post by RudolfMDLT on 2006-06-18
Damn, that sucks. 

When you say you can't get to gnome, do you get the textbase, almost DOS like error that says the Xserver failed to load or still the blank desktop with only a mouse. 

This i my last resort advice, go into synaptic, search for all the packages that the guide told you to install. Right click and click mark for removal. Not complete, just remove them. once you have removed everything that you require to run the fglrx driver, move to the /etc/X11 folder. here you will find multiple xorg.conf files. xorg.conf.fglrx-1, xorg.conf.fglrx-2 ect. These are backup copies. I want you to restart into recovery mode and login as root. Once logged in, you remove your current Xorg.conf file.

rm /etc/X11/xorg.conf.  

Don't restore or rename a backup copy. Now restart, you should en up with a text base warning that gnome could not start. This is what we want.

Now restart into recovery mode again(You must be quit sick of this by now.). You follow the Guide up top to the letter as you have done before. You MUST be logged in as root. After installing all packages and configuring the fglrx driver to initial, restart the pc and see if gnome does load. If it doesn't, restart into recovery mode again, copy and rename the oldest backup of xorg.conf i.e. xorg.conf.original to xorg.conf.

redo the following after recreating the original xorg.conf file:

sudo depmod -a

sudo aticonfig --initial

sudo aticonfig –overlay-type=Xv


You now have a completely new set of drivers and xorg configuration file. If this does bot work, i do not know what else to do. Please backup you important documents and emails and anything else that is important before doing the above. It should work, and has worked on my system but I don't want to be responsible for you loosing important data. Honestly if this doesn't work and you need your 3D badly  i would revert back to breezy.

Sorry if you have tried this already, but I cannot think of anything else to try other that removing the drivers and Xorg config files and starting afresh.

Hope this helps! Good luck! 	[-o<

---

### Post by DonQuixote on 2006-06-19
Rudolf,

I really appreciate your efforts in trying to help me out.  I'll give the above a try and let you know the results as soon as I can. :)

---

### Post by DonQuixote on 2006-06-19
Alright... I got the blank screen again, couldn't get to gnome because it hung on a blank screen with the mouse pointer.  No disk activity.  No screen activity.  I could move the mouse around.

I rebooted back into recovery mode and thought I'd take a look at the logs.  I found a list of errors that occurred over and over again related to the loading of "dri" (Anyone know what THAT is?)  So I went back to the xorg.conf file and removed the line that states 'load "dri"', then rebooted.

No double drum sound.  I held my breath after entering my password.  Gnome came up!  I ran "glxgears -printfps" from the terminal.  My FPS is below 200 and the gears move like they have sand in the teeth.

I'll post the errors I'm getting in my log file in a bit...

---

### Post by RudolfMDLT on 2006-06-19
... you're running mesa again. I'm in XP now, I'll reboot into Ubuntu and see what dri is.

---

### Post by DonQuixote on 2006-06-19
I'm attaching my /var/log/Xorg.0.log and my xorg.conf files here if anyone with more experience than I would be willing to take a look at them.

The lines that I find particularly interesting are: 

518 - 523
701 - (Pretty much the same message except the last 6, there is a comment in the file, in order to shorten it)

These have to do with something called "drm"

Any help would be much appreciated.  I know there are others who are experiencing this same problem.

---

### Post by DonQuixote on 2006-06-19
I don't find "mesa" in my xorg.conf file... and frankly, I don't even know what mesa is in regard to linux...

---

### Post by RudolfMDLT on 2006-06-19
> The Direct Rendering Infrastructure, also known as the DRI, is a framework for allowing direct access to graphics hardware under the X Window System in a safe and efficient manner. It includes changes to the X server, to several client libraries, and to the kernel. The first major use for the DRI is to create fast OpenGL implementations.

The DRI is an integral part of XFree86 4.x , and integrates with Mesa

[http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/)

Below are two parts of my Xorg.conf file:

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"                             <=
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection


Section "DRI"                                       <=
	Mode         0666
EndSection

Just for the hell of it, here's my entire Xorg.conf file! :) Compare it with yours. If your feeling desperate and adventurous, mark system specific settings like monitor type for example and then copy my entire xorg.conf file to yours, save it, restart and see what happens. Note, in the console, sudo gedit /etc/X11/xorg.conf to edit it as root, this will enable you to save it. As always back it up first.

Just in asking; you did remove the drivers first? and then reinstalled them all? If you did, then don't even answer this question. :)

---

### Post by DonQuixote on 2006-06-19
All that I did was on a fresh installation of Dapper, so I don't think there was anything to uninstall...right?

---

### Post by RudolfMDLT on 2006-06-19
No, there shouldn't be, but you have been trying to install ATI drivers, so there should be some fglrx files and dep files on you machine.

Sorry, type "fglrxinfo" into the consol and you will find that it says something about mesa. This is wrong. It should sau ATI and you card model number, ie:

> rudolf@rudolf:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)


---

### Post by DonQuixote on 2006-06-19
Damn... I copied over everything that was different from your xorg.conf file to mine  (and there wasn't that much), with the exception of the system specifics, rebooted and got the double drum of death....

fglrxinfo in recovery gives me the "display cannot be found" error, and when I remove the "Load "dri"" in the xorg.conf file and boot to Gnome, fglrxinfo in the terminal gives me this:

> 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


---

### Post by RudolfMDLT on 2006-06-19
Okay! Just try these two changes.

> 
Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "fglrx"                      <==== "ati"
	BusID       "PCI:1:0:0"
EndSection



> Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "on" <========"off"
EndSection

In the above quotes, look for the <===== pionting to a problem and change it to what i suggested.

The first edit tell which driver to use and the second edit switches opengl off. I believe that openGL is what caused you're system to load into gnome,, but no window manager to load,

Try this, i'm removing my Xorg.conf from a previous post now.

---

### Post by DonQuixote on 2006-06-19
No go... I'm over here reading about the troubles others have had with this...

[http://www.ubuntuforums.org/showthread.php?t=189874](http://www.ubuntuforums.org/showthread.php?t=189874)

Maybe there is something there that will click...

---

### Post by RudolfMDLT on 2006-06-19
[QUOTE=DonQuixote]No go... I'm over here reading about the troubles others have had with this...

[http://www.ubuntuforums.org/showthread.php?t=189874](http://www.ubuntuforums.org/showthread.php?t=189874)

Maybe there is something there that will click...[/QUOTE]


Some gay in the above link posted 

I managed to get the drivers to work (sort of).

After the aticonfig --initial, you need another command. That is:

aticonfig --overlay-type=Xv

Hope that helps.


In you Xorg.conf you have both Xv and opengl set to ON?

---

### Post by DonQuixote on 2006-06-19
*sigh*

Yes, I do.  But it didn't work.  I'll keep monitoring these threads to see if anything new comes up.  In the mean time, I guess I'll game under Windows, and do everything else under Linux.

Back to the dual boot. :(

---

### Post by RudolfMDLT on 2006-06-19
[QUOTE=DonQuixote]*sigh*

Yes, I do.  But it didn't work.  I'll keep monitoring these threads to see if anything new comes up.  In the mean time, I guess I'll game under Windows, and do everything else under Linux.

Back to the dual boot. :([/QUOTE]

Yes, I do. But it didn't work. I'll - I don't think that both are supposed to be on at the same time?


DonQuixote,

Sorry man. Well, I can't think of anything else to help with. Look, i still dual boot with XP as I do someintensive video editing, it works. 

Cheers and goodluck!

PS: if i do stumble accross something i'll let you know!

---

### Post by jrjr on 2006-07-27
You can see where I was at in this post:

[http://ubuntuforums.org/showthread.php?t=222261&page=2](http://ubuntuforums.org/showthread.php?t=222261&page=2)

I followed your method above and it straightened out my video.
It was the one single command though I think as most everything was already done.

This is what did the trick for me I think but i'm not positive. Still learning!!

sudo aticonfig --overlay-type=Xv

Anyway... thanks for the input!!

---

### Post by Malac on 2006-07-27
This may not be related but when I got my 9200SE to run 3D, I read in one of the (many) howto's that due to a bug in the ati/fglrx driver. You may have to set fglrxinfo to "look at" display 1 not 0 as well as some other settings in gdm.conf .
Also libGL.1.2.so  should be replaced with an old one or something.
Sorry I can't remember where I saw this or how to do it or which files/settings to alter but maybe it will point you in the right direction.

Hope this helps.

---

### Post by RudolfMDLT on 2006-08-03
jrjr - Great! Glad I could help!

---

### Post by RudolfMDLT on 2006-08-12
Hi!

I see that the view count on this thread still goes up. If you find this usefull and it helps, post that it worked! BUT more importantly, if it did not work please say so and I'll try and help you make it work. Also if you have any tips or comments please add them! Thanks!

---

### Post by Malac on 2006-08-12
I didn't get the fglrx drivers to work for my 9200SE but by replacing the "ati" with "radeon"  in /etc/X11/xorg.conf and manually typing in a few modules I now have 3D.
The section of my xorg.conf looks like this:

```
Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "dbe"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection
``` and :
```
Section "Device"
    Identifier    "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
    Driver        "radeon"
    BusID        "PCI:1:0:0"
EndSection
``` From glxinfo command I get:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1
``` 
From glxgears command I get:
```
3628 frames in 5.0 seconds = 725.581 FPS
3671 frames in 5.0 seconds = 734.052 FPS
3673 frames in 5.0 seconds = 734.538 FPS
3670 frames in 5.0 seconds = 733.649 FPS
3681 frames in 5.0 seconds = 736.070 FPS
3676 frames in 5.0 seconds = 735.191 FPS
3678 frames in 5.0 seconds = 735.156 FPS
3679 frames in 5.0 seconds = 735.754 FPS
3675 frames in 5.0 seconds = 734.953 FPS
3674 frames in 5.0 seconds = 734.729 FPS

``` 
However XGL/Compiz run but like a very slow dog. :)

Hope this helps someone.

---

### Post by RudolfMDLT on 2006-08-20
WOW! Thanks allot man! I think it just might! Compiz is a dog on my card too!

---

### Post by Malac on 2006-08-20
Okay, just a heads up as the new 8.28.8 installer from ATI website worked perfectly for my system.
I now have fglrx working this is what I did.
[COLOR=Blue](The [COLOR=Black]**rm**[/COLOR] and [COLOR=Black]**rmdir**[/COLOR] commands are only needed if you have other driver debs in the directory from previous installs and can be missed out if you wish to keep them.)[/COLOR]
Put installer in /usr/src/ then ran following commands
In a **_root_** terminal 
```
cd /usr/src/
``` 
```
 chmod +x [COLOR=Gray][I]"name of driver installer"
[/I][/COLOR]rm /usr/src/modules/fglrx/debian/*.*
rm /usr/src/modules/fglrx/*.*
rm /usr/src/ATI/*.*
rmdir /usr/src/modules/fglrx/debian
rmdir /usr/src/modules/fglrx
rmdir /usr/src/ATI
rm fglrx.tar.bz2
rm fglrx-*.deb
rm xorg-driver-fglrx*.deb
./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/dapper
dpkg -i *.deb
module-assistant prepare,update
module-assistant build,install fglrx
depmod
``` Reboot and voila.
If you don't run this in a root terminal you will need **sudo** before each command

fglrxinfo output :
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)
``` 
glxgears output :
```
4078 frames in 5.0 seconds = 815.554 FPS
4077 frames in 5.0 seconds = 815.391 FPS
4077 frames in 5.0 seconds = 815.330 FPS
4077 frames in 5.0 seconds = 815.383 FPS
4078 frames in 5.0 seconds = 815.418 FPS
4077 frames in 5.0 seconds = 815.371 FPS
``` 
Hurrah!

---

### Post by jrjr on 2006-08-20
.

---

### Post by Malac on 2006-08-20
There faster than the 128.whatever I was getting before. :)

---

### Post by erius on 2006-08-26
I've been trying to get 3D working with my ATI Raderon 9600 XT.
But nothing I've tried has worked so far...

According to "fglrxinfo" and "glxinfo | grep rendering" everything should be OK. There are no errors in /var/log/Xorg.0.log or "dmesg | grep fglrx".

Funny thing is that without fglrx the gears are drawn correctly and fps rate is at least double ;)  Check the screenshot to see what I mean. All GL stuff is drawn incorrectly like that, not just glxgears.

3D was working normally in Windows Xp...I had WinXp on this box few months back.

---

### Post by mtn on 2006-08-30
I'm having problems with my Radeon 9600 pro on my AMD64 running Dapper with latest updates. I have tried loads of how tos etc etc, but no joy. Anyone have any idea the output below from the glxinfo command means?

Also having tried loads of how tos is that likely make it more difficult to sort as all the setting are non default? Is it worth taking of Dapper 64 and reverting to Dapper 32 bit?

Any help with any of this would be really appreciated.

mike@mike-desktop:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18

EDIT - SUCCESS!

The hardware This has worked on is an AMD64 (running Dapper 32bit) Athlon 3200, Radeon 9200 Pro with gig of RAM.

I have uninstalled Dapper 64bit and installed dapper 32bit and I seem to have had some luck. I did what this [guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25") suggested for Dapper 32bit and when I had finished and ran the command **fglrxinfo** in the terminal I got this out put (which is better as no errors)

mike@Ubuntu-Home:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

Google Earth now works like a dream and I have played BZTank (3D network game installable through Synaptic) in full 3D glory. I have to say I'm very happy.

The guide also says "You might want to install the fglrx-control package, which provides a control panel to configure graphics card options such as dual-head display (two monitors) and TV out." though I have installed the package I have not figured out how you run it, any help here would be great as I would like to put video on to my TV.

EDIT - FOUND IT!

"You may want to install the fglrx-control package as well. It gives you a nifty control panel that you can run from the terminal with the command..."

Code: fireglcontrolpanel

[From here]("http://www.ubuntuforums.org/showthread.php?t=238824&highlight=fglrx+control")

---

### Post by RudolfMDLT on 2006-10-16
I'm glad you guys gor your cards working! mtn thanks for the extra info! To anybidy else posting here:

[COLOR="Red"]Send me an email by clicking on the Orange RudolfMDLT heading or on the read dragon when you do post here![/COLOR] 

I can't monitor this post. Posts this deep into a thread tend to get ignored rather than starting a new post. I'll happily help anybody posting here!

Cheers,

Rudolf

---

### Post by nagates on 2006-10-16
hey, when i do the fgl_gears(what ever the command is extactly) i can see the 3d cube but no gears, its just blue instead, i have a 9100 128mb pci graphics card.

---

### Post by RudolfMDLT on 2006-10-22
nagate,
you need to see gears spinning.

Please email me if you ever do look back here. click on the orange Rudolfmdlt  logo thingy and select the option that says email!

Cheers,

Rudolf

---

### Post by Malac on 2006-10-22
> **RudolfMDLT said:**
> nagate,
you need to see gears spinning.

Please email me if you ever do look back here. click on the orange Rudolfmdlt  logo thingy and select the option that says email!

Cheers,

Rudolf
I think nagate is running the fgl_glxgears which is the one included in the fglrx package. This is the one that draws a blueish spinning cube.
The gears one is glxgears totally different thing.
Unless of course your supposed to see the gears on the cube in which case mine doesn't work either. :)
In which case can someone attach a screenshot or an mpeg of what's supposed to be seen when running fgl_glxgears.

---

### Post by RudolfMDLT on 2006-10-22
Hi Malmac,

good to see you on the thread again! :)

You have a cube with a "glxgears" running in each side.

---

### Post by Malac on 2006-10-23
> **RudolfMDLT said:**
> Hi Malmac,

good to see you on the thread again! :)

You have a cube with a "glxgears" running in each side.
Oh NOOOOOOOOOOOOOOO. :)
That means mine isn't working properly, #-o BOO HOO. :-(
I only get a blue spinning cube. ](*,)
[ATTACH]18034[/ATTACH]
Good to see you too, RudolfMDLT.

---

### Post by RudolfMDLT on 2006-10-24
:) 

Hi Malmac,

I don't believe that it's a problem. Take your normal glx gears fps count and devide it by 6. then run the cube thing and check that fps out. I've got a fealling that if the fps dips below 300 or 250 then the cube just won't render normally. I don't think it's a driver issue, more a hardware one, but I'm not entirley sure!

Cheers,

Rudolf

---

### Post by RudolfMDLT on 2006-10-30
Hi,

can some one maybe explain this:

rudolf@rudolf:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1839 frames in 5.0 seconds = 367.800 FPS
rudolf@rudolf:~$ glxgears
rudolf@rudolf:~$ glxgears -printfps
1233 frames in 5.0 seconds = 246.478 FPS
1229 frames in 5.0 seconds = 245.788 FPS
rudolf@rudolf:~$


In dapper, glx gears performed 6 times as good as fgl_glxgears. Since my upgrade to Edgy, my fps has plummeted, Beryl is dog slow and glx gears gives an out put of roughly 250 fps, it used to be close to the 2000 mark. Now how come fgl_glxgears gives the same output as it used to?

:-k 

This is not a problem, it just bugs me that I still don't understand how the Ubuntu display works and it has changed with edgy and i still don't understand completely!

Any comments or advice appreciated!

Thanks,

Rudolf

---

### Post by RudolfMDLT on 2006-11-01
Can someone please just have a look at this! post a smiley if you don't know, just leave your mark so that i feel better! ;)

---

### Post by podunk on 2006-11-01
Down with ATI Microsoft running dogs! :)

Hopefully now that ATI is owned by AMD some of the culture will make it's way into ATI. Until then I think we need to buy Nvidia.

What's the difference between X11 and X86free?

---

### Post by RudolfMDLT on 2006-11-02
Haven't really read through this but the heading seems to be what you are looking for!

[http://www.justlinux.com/forum/showthread.php?threadid=147363](http://www.justlinux.com/forum/showthread.php?threadid=147363)

Cheers!

---

### Post by podunk on 2006-11-02
Thanks for the link! I read some stuff and no one talks about differences in functionality, everything is about their different approach to free software.

ATI states very plainly that it's drivers are designed for xfree. I wonder what all we'd tear up by installing xfree over xorg?

---

### Post by fatneck on 2006-11-03
Thanks for this, seem to have mine working now. Averaging about 100fps on Radeon XPRESS 200M - can anyone tell me if that is about right?

---

### Post by RudolfMDLT on 2006-11-03
Hi!

Your sig says your running Dapper. If thats the case, then no, it should be over a thousand. You probally know this but:

fglrxinfo

should display something about ati and NOT mesa.

If your running Edgy then that is fine for now. The latest drivers I heard where released 2 days ago. I'll check it out and verify it. 

Cheers!

---

### Post by RudolfMDLT on 2006-11-03
As of driver version 8.29.6 support for the following products is no longer included:

    * Radeon® 8500/9000/9100/9200/9250
    * Mobility™ Radeon® 9000/9100/9200
    * Radeon® IGP 9000/9100/9200

Users with these products should use driver version 8.28.8

Edgy is released with this version:

rudolf@rudolf:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6011 [COLOR="Red"](8.28.8)
[/COLOR]

---

### Post by fatneck on 2006-11-03
Hi back !!

I'm a total noob, so any help is very welcome. I think it has worked:

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

but I also seem to be having CPU issues which may or may not be slowing it down. Unless there are any other graphic tips you might have?

Cheers

---

### Post by RudolfMDLT on 2006-11-04
Hi there

Sorry mate, I can't give you any tips! I don't know any. all I use is this:

Option "AGPMode" "4"

under my DEVICE section

You can change it for an 8 if you wish. The thing is that every new series of cards has a new bell or whistle.

If you really want to play, open the terminal and type: aticonfig

This will give you a whole list of possible commands that you can use. The top ones on the list are ones you can actually add into the Xorg.conf. Please backup your xorg.conf file first! There are saome settings, like the refresh rate or sync settings that could potentially mess with you monitor so just be careful.

Cheers,

Rudolf

---

### Post by cgrebeld on 2006-12-09
Thanks! I followed your edgy instructions and finally got my 9600pro GLX working now.  

I don't see why you need to enter recovery mode though, everything seemd to work fine from an X terminal for me.

---

### Post by RudolfMDLT on 2006-12-10
Pleasure mate! Thanks for posting! You got lucky, most people can't configure   the damn drivers in X. well done man!

Cheers,

Rudolf

---

### Post by Extrapolation on 2007-01-20
OK, I installed ATI's drivers, as well as following a really elaborate tutorial that had me recompile my kernel.  All said and done, and I have the same framerates I had before.  At least I can get to my desktop now.

glxinfo produces the following:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x26 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x29 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x2a 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2d  8 pc  0 24  0 c  y  .  0  0  0  0  0 16  0  0  0  0  0  1 0 None
0x2e  8 gs  0 24  0 c  y  .  0  0  0  0  0 16  0  0  0  0  0  1 0 None
ben@Benputer:~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
ben@Benputer:~$ glxgears --printfps
Warrning: unknown parameter: --printfps
ben@Benputer:~$ glxgears -printfps
ben@Benputer:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x26 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x29 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x2a 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2d  8 pc  0 24  0 c  y  .  0  0  0  0  0 16  0  0  0  0  0  1 0 None
0x2e  8 gs  0 24  0 c  y  .  0  0  0  0  0 16  0  0  0  0  0  1 0 None
```

Can someone please tell me what to do?  I have wasted three miserable days on following every HowTo I can find, and I'm about to just throw my hands up and go back to Windows entirely!

---

### Post by nibbo on 2007-01-28
i have the same outputs and same problem as you, have you got it solved?

---

### Post by RudolfMDLT on 2007-01-28
Hi there,

Please post the output of ¨fglrxinfo¨ and your xorg.conf file!

CHeers,

Rudolf

---


---
title: "Am I stuck upgrading my hardware b/c neither Ubuntu nor ATI will support my Vid Card?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by finny388 on 2008-02-06
I  have been trying for days each day to get drivers that will work with my Radeon 8500.

I posted in the Hardware section with no reply.

Ubuntu claims to support it but all I get is 1024x768 @ 60Hz. I can't stand it.

**Does anyone out there have Gutsy Gibbon working well with their Radeon 8500?**

Thanks all

[My hardware thread attempt]("http://ubuntuforums.org/showthread.php?t=687771")

---

### Post by finer recliner on 2008-02-07
in your thread, you're attempting to install the fglrx driver. this is ATI's proprietary driver. ATI provides very limited supported for the linux community. 

the linux community has their own video driver that supports just about every card called VESA. you wont get the best performance from it and maybe not 3d acceleration, but it will work for general computing needs.

---

### Post by Rocket2DMn on 2008-02-07
The ati binary driver (fglrx) does not support cards this old, you need to use the open source drivers - [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
That page will show you how to remove the fglrx driver and how to install the ati one.  You won't get accelerated 3d support, but rather "full" 3d support.

---

### Post by chewit on 2008-02-07
There is an official ATi driver for that card for Linux.

[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)

---

### Post by finny388 on 2008-02-07
I am aware of the ATI 8.28.8 driver - it won't even install as I describe in my other (short) thread. It supports my card - maybe it doesn't support Gutsy?

I will try the open src one you suggested Rocket2DMn - thanks for the link.

Gotta rush off to work now.  I can't wait to get Kubuntu up and running and be rid of redmond

---

### Post by Martje_001 on 2008-02-07
> **finny388 said:**
> Ubuntu claims to support it but all I get is 1024x768 @ 60Hz. I can't stand it.
Could you post your */etc/X11/xorg.conf* here?

---

### Post by finny388 on 2008-02-07
> Could you post your /etc/X11/xorg.conf here?

Gladly! I am at work right now so I can't get to it until tonight.

nice to get some replies :)

---

### Post by LowSky on 2008-02-07
have you tried Envy, it auto installs drivers

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Martje_001 on 2008-02-07
> **LowSky said:**
> have you tried Envy, it auto installs drivers

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
Don't do it. It will install the proprietary ATI drivers which don't work with your card.

---

### Post by finny388 on 2008-02-07
> Don't do it. It will install the proprietary ATI drivers which don't work with your card.

Are you saying that even the driver that ATI claims will support me won't?

The one I'm talking about is at the [ATI Driver Download(link)]("http://ati.amd.com/support/driver.html") page where after selecting Linux, the very last card on the card list is the 8500.

I select that and get the [ATI Proprietary Linux x86 Display Driver 8.28.8(link)]("http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html")

:confused:

---

### Post by finny388 on 2008-02-07
> Could you post your /etc/X11/xorg.conf here?

Here it is:

> Section "Files"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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

Could it be my monitor the trouble is with?
It's an LG Flatron 915FT Plus.

I'm going to try Rocket2DMn's recommendation of installing the opensource version.

---

### Post by finny388 on 2008-02-07
Went thru rocket's link and now rebooting

xorg.conf now looks like this:
> Section "Files"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Radeon R200 QL Radeon 8500 LE"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-110
	VertRefresh	50-200
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon R200 QL Radeon 8500 LE"
	Monitor		"Generic Monitor"
	DefaultDepth	24        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
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

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

now rebooting...   [-o<

---

### Post by R@inm@n on 2008-02-07
Just be careful .... I've had the ATI Radeon problems ever since I installed Ubuntu, and still havn't found a good solution to it.

Even in Mint Linux, the latest release, I had problems with the graphic card drivers.

I don't think ATI cares for Linux too much...:(


  If....by some chance you manage to get the ATI thing working well, could you please let me know, as I have had no luck so far with mine.


 Thanks,


   R.

---

### Post by finny388 on 2008-02-07
I will be sure to explain how I get this working IF I get it working:

just rebooted and it won't come to the GUI. I see the Kubuntu logo and the progress bar just starting, then it switches to terminal with
> KINIT: No Resume image, doing normal boot

Where I can then login to Kubuntu but I don't know how to get to "Windows" or should I say KDE?

When I editing the xorg.conf I backed the original up as xorg.conf.bak along side it in the X11 folder.

**is there a terminal command I can use to restore the conf file?**

:(

---

### Post by Rocket2DMn on 2008-02-07
To restore your backup file, run
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

I think we need to try to reconfigure X.  Lucky for you, I just finished writing a HowTo on reconfiguring X - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
You will want to follow the "b)" parts for KDE (since it seems that's what you're using).

If that doesn't work, you may need to try one or more of the following:
1) reinstall Kubuntu
2) try Gnome (regular Ubuntu)
3) get a new video card since yours is so old it may just not have full support (like high resolution)

---

### Post by finny388 on 2008-02-08
> If that doesn't work, you may need to try one or more of the following:
1) reinstall Kubuntu
2) try Gnome (regular Ubuntu)
3) get a new video card since yours is so old it may just not have full support (like high resolution)

Based on you 1,2,3 suggestions are you suggesting that my card my be too old for Gutsy Kubuntu even though Ubuntu and ATI BOTH say that they support them? 

My card and monitor support up to 1600x1200 @85Hz in WXP.

Since I have nothing to save since this has been my priority since the first minute I installed Kubuntu (60Hz drives me nuts) I think I will reinstall and try "- https://help.ubuntu.com/community/RadeonDriver" again.

because I am hoping I made a mistake in my xorg.conf changes (do you see any problems?) and that doing that right after a fresh install may be my route.

here we go again... (reinstalling)

---

### Post by shae on 2008-02-08
The old ATI driver cannot build its module against the latest kernel in gutsy, you need to build an older kernel first to install the older drivers for your card.

---

### Post by finny388 on 2008-02-08
hmm shae...

I just finished installing again

I am gone to try installing the open source driver again :???:

---

### Post by kelvin spratt on 2008-02-08
The ATI site says there is a driver for your card go to this link
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) and download Envy this program will download the correct drivers from ATI and set them up for you with a couple of clicks. hopefully that will solve your problems? I use this method I just leave every thing as it installs then use envy reboot and the screen size is 1600x1200x75hz. Hope this is helpful.

---

### Post by tosk on 2008-02-08
The trouble looks like how X handles your monitor. According to the xorg.conf you posted, the open-source ATI driver is already loaded.

For me, the open-source driver was enabled by default. Once you're inside the GUI, open a terminal and type:

```
glxgears
```

After a moment or so, it'll spit some info out into the terminal. If your FPS is in the hundreds, then your card has 3D support enabled. If not, then you should look into another driver.

Also, what does the proprietary ATI driver say when you try to run it on your system? Does it give any errors when you try to install it?

---

### Post by finny388 on 2008-02-08
> After a moment or so, it'll spit some info out into the terminal. If your FPS is in the hundreds, then your card has 3D support enabled. If not, then you should look into another driver.

Also, what does the proprietary ATI driver say when you try to run it on your system? Does it give any errors when you try to install it?

Hello Tosk,

I tried the xorg.conf edit from "https://help.ubuntu.com/community/RadeonDriver" again after a fresh install and same thing - KINIT no resume image.

In my original thread in HARDWARE I was trying to troubleshoot the ATI 8.28.8 install ([link]("http://ubuntuforums.org/showthread.php?t=687771"))

This was the error at Create .deb packages:

```
k-desktop:~$ sh ati-driver-installer-8.28.8.run --buildpkg Ubuntu/gutsy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8............................................ .................................................. .................................................. .................................................. .................................................. .................................................. .................................................. .................................................. .................................................. .........................
-e ==================================================
-e ATI Technologies Linux Driver Installer/Packager
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install
```

the other thread is just show the result of running the through the ATI driver .8.28.8 failure.

[B]now bear in mind I was replacing
'dapper' with 'gutsy'
and
'ati-driver-installer-8.33.6-x86.x86_64.run' with
'ati-driver-installer-8.28.8.run' (b/c that was the name of the file from ATI for 8.28.8)

So I have never actually gotten to try out the ATI proprietory yet[/B]

I knew my setup was old but I thought I would just be turning off the eye candy and enjoy 'owning' my computer again.

:(

---

### Post by tosk on 2008-02-08
**kinit no resume image** is normal. When the system boots, it looks for a system resume (like when you hibernate your computer) image. If one is found, then it restores that image. If not, it proceeds with normal boot.

For the driver installation, try the following and see if it succeeds in building the driver:
```
sh ati-driver-installer-8.28.8.run --buildpkg Ubuntu/dapper
```

The older driver might not have a configuration for building a package specifically for gutsy.

---

### Post by finny388 on 2008-02-08
Thanks Tosk, I'll be home in a few hours and give that a try.

THANKS FOR ALL THE HELP SO FAR EVERYONE!

):P

---

### Post by Martje_001 on 2008-02-08
It's very simple to get your hertz up (in /etc/X11/xorg.conf):
```

HorizSync 30-110
VertRefresh 50-200
```
```

HorizSync 30-**200**
VertRefresh 50-200
```
Or try higher / lower numbers. If X fails to start after this:
**1**. Press ALT + CTRL + F2
**2**. Login
**3**. Typ **sudo nano /etc/X11/xorg.conf**
**4**. Edit your file again, and press CTRL + O to save, and CTRL + X to close nano.

---

### Post by kelvin spratt on 2008-02-08
I read one of the earlier posts saying envy only installs the latest version availible that is not strictly correct. If you choose manual install you can choose any driver that is available from ATI

---

### Post by Martje_001 on 2008-02-08
> **kelvin spratt said:**
> I read one of the earlier posts saying envy only installs the latest version availible that is not strictly correct. If you choose manual install you can choose any driver that is available from ATI
Oh please! FIRST INSTALL IT, LOOK AT IT, AND THEN SAY SOMETHING!
Envy **cannot** install ANY driver from the ATI site (see my attachment). You get 3 or 4 drivers to choose from, though you could let Envy decide which fits your card.

---

### Post by finny388 on 2008-02-08
Status: Fresh install, edited xorg.conf only with refresh rate settings..

Shae - build an older kernel? Wouldn't know where to begin.

Tosk - Ran glxgears and got numbers between 1900-3500 avg'ing say 2100. So I guess I've got 3D.

Haven't tried the ATI driver again... yet.

Martje_001 - Edited xorg.conf to HorizSync to 30-200 as you advised. Rebooted. Still 60 Hz is the only option in the Monitor and Display settings. :(

Things left to try:
1. Give open source drivers another try by editing the xorg.conf file very carefully.
2. Retry ATI drive using Dapper in the script instead of Gutsy as Tosk suggested.
3. Envy
4. Keep trying/give up and upgrade hardware sooner than I was planning to (at which time I want to build a Kubuntu Hot Rod and will want suggestions on what hardware to choose)

So here it goes again with the xorg.conf edit. Will update afterwards...

thanks again

---

### Post by finny388 on 2008-02-08
Made the following edits to xorg.conf:

# Added "Display" subsection in Section "Screen"
	SubSection "Display"
		Depth	24
		Modes	"1024x768" "1280x1024"
		Virtual	1280 1024
	EndSubSection

# Additional Sections at end of file:
Section "DRI"
	Mode 0666
EndSection
Section "Extensions"
	Option "Composite" "Enable"
EndSection

Does spacing and tabbing play into the syntax here? or is it strictly to make things easy to read?

restarting...

---

### Post by JoshuaRL on 2008-02-08
What happens when you run:

```

glxinfo | grep direct

```

That should tell you if you have direct rendering (3D hardware acceleration) turned on.  Although, if you run in the thousands, it definitely should be.

---

### Post by finny388 on 2008-02-08
by the way, when I ran glxgears it ran through about 20 fps test then the screen froze, I waited... then hard rebooted.

Well, back to a fresh install. Made those edits to xorg.conf as above and got the KINIT no resume image again.

Tried to restore it from the backup I made and the cp failed.
I then tried to navigate to /x11 with no luck!?
```
cd /
```
got me to the root
```
cd /etc/x11
```
no such directory!
```
cd /etc
dir
```
from here I see the X11 folder but when I reference it with cd or cp it can't find it.

So... reinstall ](*,)

I'm going to try envy now. I think I'm done with the open source drivers.

---

### Post by Rocket2DMn on 2008-02-08
Upper and Lowercase matter in linux so you have to do 
```
cd /etc/X11
```

---

### Post by finny388 on 2008-02-08
Thanks

Wow. is this ever exhausting.

Tried envy and it told me I was missing a dependency called 'dkms' #-o

I want to believe...

---

### Post by Rocket2DMn on 2008-02-08
"dkms" is available in the universe repository, so if you have enabled, you can just run
```
sudo apt-get update
sudo apt-get install dkms
```
If you have access to the GUI but don't have universe enabled (it won't let you dl the pacakge if you don't), you can enable it from System->Administration->Software Sources.  If you DON'T have a GUI, then you need to edit /etc/apt/sources.list manually, which we can help you with if you need it.

---

### Post by finny388 on 2008-02-08
tried the ATI drivers again and failed with same error on the same command as before.

Only this time I used 'dapper' instead of 'gutsy' as Tosk suggested
```
@k-desktop:~$ sh ati-driver-installer-8.28.8.run --buildpkg Ubuntu/dapper
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

```

What is your hardware/software setup Martje? Your envy screenshot looked beautiful.

I'm starting to wave the white flag. I'd hate to compare this hardware inadequacy/lack of support to a Vista upgrade so I won't. I can't. I won't.

[-(

---

### Post by shae on 2008-02-08
First install the development files required to build the kernel:
```
sudo apt-get install build-essential bin86 kernel-package wget libncurses5 libncurses5-dev
```

Next change directory to /usr/src
```
cd /usr/src
```

Then make yourself a root user:
```
sudo -s
```

Next download and extract the source files:
```
wget -c http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.16.60.tar.bz2 && tar -xvjf linux-2.6.16.60.tar.bz2
```

Then remove old links and create a new one; then changes to the new link:
```
rm -rf linux && ln -s /usr/src/linux-2.6.16 linux && cd /usr/src/linux
```

Imports current kernel config:
```
cp /boot/config-`uname -r` .config && make oldconfig
```

Build the configuration menu and loads it:
```
make menuconfig
```

Tutorials on configuring kernel options are avaliable through google.  Defaults should be fine however.

Make clean:
```
make-kpkg clean
```

Builds kernel packages:
```
make-kpkg --initrd --revision=386 kernel_image kernel_headers modules_image
```

Install kernel packages:
```
cd .. && dpkg -i linux*2.6.16*.deb
```

After this, reboot and test your new kernel.  Then install the older drivers with the installer rather than the packages.  I do not reccomend you use envy or any other script to install.  If you need assistance with this step, please ask.  I hope this helps you clear this up.  I based these instructions on the Master Kernel Thread adapted to the 2.6.16.60 kernel.

---

### Post by finny388 on 2008-02-08
Got Envy to work (thank you Rocket) but it failed.

8.28.8 Legacy driver does not support your Oper... then rebooted and didn't know how to fix so reinstalling again.

Shae, doing that kernel deal - what impact will that have beyond my video? Will I be in an early release of kubuntu at that point?

Signing off for the night...

Thanks SO MUCH for all your support you guys.

Cheers and I'll come back tomorrow.:popcorn:

---

### Post by Martje_001 on 2008-02-09
> **finny388 said:**
> What is your hardware/software setup Martje? Your envy screenshot looked beautiful.
I've got an ATI RADEON 9550.

Edit: This is my xorg.conf as you might need it:
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
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
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generieke beeldscherm"
	Option		"DPMS"
	HorizSync	28-120
	VertRefresh	43-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"Generieke beeldscherm"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" "1024x768" "800x600"
		virtual 1152 864
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

---

### Post by kelvin spratt on 2008-02-09
Originally Posted by **kelvin spratt**                     [[IMG]http://ubuntuforums.org/images/uf/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=4294814#post4294814")                 
                 [I]I read one of the earlier posts saying envy only installs the latest version availible that is not strictly correct. If you choose manual install you can choose any driver that is available from ATI

MARTJE_001 Says
[COLOR=Red]Oh please! FIRST INSTALL IT, LOOK AT IT, AND THEN SAY SOMETHING!
Envy **cannot** install ANY driver from the ATI site (see my attachment). You get 3 or 4 drivers to choose from, though you could let Envy decide which fits your card.[/COLOR]

Firstly I think there is a miss understanding where did I say [COLOR=Red]any driver[/COLOR] [COLOR=Red]from the ATI site[/COLOR], Any driver available from ATI = using the program !  AND they happen to be compatible with most Supported cards. I was merely pointing out that it does give you a choice of manually installing available drivers
Yes I have ENVY INSTALLED ON MORE THAN 1 COMPUTER
and the same ATI 9550 card as you and Nvidia 

finny388
If Feisty works with your vid card then you can install and lock the vid drivers and do a distro ugrade to gutsy that will give you a very fast Gutsy. I've done that myself when Gutsy first came out and it works on my setup 4 drivers had to be locked just a thought. I now use the latest drivers as they now work better than previous drivers. BUT you can't go from Dapper straight to Gutsy?
[/I]

---

### Post by Martje_001 on 2008-02-09
> **kelvin spratt said:**
> Firstly I think there is a miss understanding where did I say [COLOR=Red]any driver[/COLOR] [COLOR=Red]from the ATI site[/COLOR], Any driver available from ATI = using the program !  AND they happen to be compatible with most Supported cards. I was merely pointing out that it does give you a choice of manually installing available drivers
[/I]
I apologize ;)

---

### Post by kelvin spratt on 2008-02-09
It's partly my fault I sometimes miss things out. I spend so much time correcting that I delete and Miss things. Unfortunately spell check can't correct word blindness.

---

### Post by finny388 on 2008-02-09
> If Feisty works with your vid card then you can install and lock the vid drivers and do a distro ugrade to gutsy that will give you a very fast Gutsy. I've done that myself when Gutsy first came out and it works on my setup 4 drivers had to be locked just a thought. I now use the latest drivers as they now work better than previous drivers. BUT you can't go from Dapper straight to Gutsy?

I can't upgrade to Gutsy from Dapper?

I think the ATI drives work with Dapper.

I want to try this: Install Dapper, "lock the video drivers" and upgrade to Gutsy.

Is this possible and how do I do it?

---

### Post by tosk on 2008-02-10
You might also need to lock in dapper's xserver as well. Else then the xserver module won't work because it's for an older version.

---

### Post by kelvin spratt on 2008-02-10
I don't think you can go from Dapper to Gutsy? as far as I know you can only distro up one at a time have you tried Edgy in a lot of ways was similar to Dapper?

---

### Post by shae on 2008-02-10
You would not be using an older version.  You will just be using an older version of the kernel.  For the most part, you should not experience any other problems, but sometimes they do occur.  The reason they work in dapper is because it uses an older kernel.  Locking the version in dapper will not work and will result in breakage.  Simply building the kernel in gutsy should work fine.

---

### Post by finny388 on 2008-02-11
well I had no luck with Dapper.

plus if I can't go to Gutsy smoothly then I will try the kernel adjustment first.

probably tonight I'll give your instructions a spin Shae, thanks.

---

### Post by finny388 on 2008-02-12
Hello Shae,

I got the following error during your instructions.

Any ideas?

```
root@k-desktop:/usr/src# rm -rf linux && ln -s /usr/src/linux-2.6.16 linux && cd /usr/src/linux
bash: cd: /usr/src/linux: No such file or directory
root@k-desktop:/usr/src#     
```

---

### Post by finny388 on 2008-02-12
:)

---

### Post by finny388 on 2008-02-13
do I need to create this directory and that's it or did is something missing in the steps?

Pardon me, my terminal expertise includes 'cp' 'pwd' and 'cd' so far. Pretty new to this.

---

### Post by finny388 on 2008-02-13
i typed
```
mkdir /linux
```
and it returned without error
then I cd'd to /usr/src/linux
```
cd /usr/src/linux
```
but it says the directory doesn't exist
if I try to create it with Dolphin, it says Creating of folder failed.
:confused:

what the?

---

### Post by finny388 on 2008-02-14
please help:(

---

### Post by SunnyRabbiera on 2008-02-14
Mybe you wont have a choice as ATI is notorious for being anti linux, even with it owned by AMD now it is still ages behind nvidia and intel

---

### Post by macogw on 2008-02-14
The xorg.conf you originally showed uses the open source driver.  That's the driver that is meant for your card.  You can try adding higher resolutions to xorg.conf (see the part where it says about Modes), but it's not guaranteed they will work.  The open source drivers cannot force a resolution that the card itself does not have in its firmware.  

At least you can get 1024x768.  My ATI Rage II can only do 800x600 with ATI's Linux drivers (open source, it won't work with the binaries at all), even though it's supposed to get 1024x768 because for some reason ATI didn't see fit to inform the card itself that it can do 1024x768!

---

### Post by finny388 on 2008-02-14
maybe I am stuck but it doesn't explain why I can't proceed with Shae's kernel edits (create the linux folder)

also I have put this card through the paces in windows - as I posted earlier:

> My card and monitor support up to 1600x1200 @85Hz in WXP.

I just want 1280x1024@75Hz.

Guess I'm back with Windows until I upgrade. I thought linux was much more accepting of older hardware than MS Windows.

---

### Post by Burbruee on 2008-02-14
Actually, my father used to have a Radeon 8500 card as well and I went through the same hell as you to get it working like it should in his machine. I tried Envy, driver from ATi's website, propierty driver etc.. NOTHING worked, nothing enabled 3D-acceleration..

Then I tried to install Ubuntu 7.04 fresh (feisty) and appearantly there was 3D-acceleration from the start! But the resolutions didn't match up. (1024x768@53 Hz or something weird like that on a 21" CRT..) So I edited his xorg.conf. (the Horizontal and Vertical frequency). Then after a CTRL+ALT+Backspace all worked.

At least, this is how I remember it, it might not be 100% accurate though since this was a back in August and my memory is not the best. :o

---

### Post by stevejesus on 2008-02-14
I think your best bet would be to install a program called "ENVY".
I will install the proper video drivers for your card.  In Dapper even.

---

### Post by finny388 on 2008-02-16
I'm starting to get repeat suggestions, I don't expect everyone to read through 52 posts, and I think this is just about a lost cause so below I have tried to summarize. #numbers represent the post number in this thread:

**In a few words**
Open source driver doesn't handle my Rad8500, ATI doesn't support Gutsy with this card, editing to old kernel may allow ATI's driver to work but I keep getting a create folder error when doing so

**Goal:**
Kubuntu GG 7.10 to interact with my Radeon.
I don't care about 3D at this point.
Just let me have 1280x1024 @85Hz.

**Problem:**
When I go to Devices I see my card recognized as a Radeon 8500 LE.
But when I go to change res/refresh rate it won't budge from 1024x768 @60Hz.

**Hardware:**
Asus P4S 333 (SIS 645) PENT. 4 (478 ) 333MHZ DDR / ATX (6PCI/1ACR/1AGP/UP TO 6 USB/UDMA100/3DDR)
Intel Pentium 4 (Northwood - 512K Cache) (1.6A GHZ) Socket 478 (W/ CPU Cooler (Retail)
1024 +  256MB (1.28GB) Crucial PC2100 184pin DDR RAM
ATI Radeon 8500 (capable of 1280x1024 @85Hz or 1600x1200 @75Hz on my current WinXP setup)
4:3 19" Monitor (up to 1600x1200 @85Hz)

So here are the steps I've taken throughout this thread with full thanks to all of you for all your contributions:

**FIX/REINSTALL OPENSOURCE DRIVER**
   1.
   Followed: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
   #3
   Error: "KINIT no resume image" - never gets to GUI.
   #14, #21 (2nd try)

**INSTALL ATI 8.28.8 DRIVER (found at ATI under my cards name)**
   1.
   Followed " Method 2: Generating/Installing Ubuntu packages for the new drivers in Ubuntu Dapper Manually"
   at
   [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_drivers_in_Ubuntu_Dapper_Manually")
   Error: "./ati-installer.sh: 165: Syntax error: Bad substitution"
   #1 at [http://ubuntuforums.org/showthread.php?t=687771]("http://ubuntuforums.org/showthread.php?t=687771")

   2.
   Tried it using "Dapper" instead of "Gutsy"
   Same Error
   #34

   3.
   Envy failed (8.28.8 Legacy driver does not support your Oper... )
   #36

**USE OLDER KERNEL SO THAT ATI'S DRIVER WILL INSTALL AS ATI SAYS IT WILL (#35)**
   Failed on creating Linux folder during process (#46-#49)
   No response on why I can't create this folder

if notable:
Ran glxgears and got numbers between 1900-3500
#27

**Conclusion**
 1. ATI doesn't support this card AS THEY SAY THEY DO.
 2. The open source driver allows this card to run at some basic level but cannot work with its capabilities.
 3. Changing to old kernel failed so I never got to test whether the ATI driver would work with it.

Cheers all. I am going to get a new rig this year; I understand that even in an open source global community, there needs to be enough users with this old card to create the demand for programmers to work on it.

Too bad though, I was hoping Kubuntu would breath some life into my PC before retired it.

Anyway, I hope this thread gives anyone out there with this card some insights and saves them some unnecessary frustration.

Thank you everyone for your contributions and may opensource OS's live strong and free.:guitar:

---


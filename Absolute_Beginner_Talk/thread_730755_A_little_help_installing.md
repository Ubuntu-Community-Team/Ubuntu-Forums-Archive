---
title: "A little help installing?"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Dudditz on 2008-03-21
Good day to you all.

I am totally new to this so your patience would be appreciated.

I have downloaded the Ubuntu 7.10 iso, checked with winMD5Sum and all appears to be OK.

I have then made the CD, lowest speed possible to avoid any errors.

Once rebooting, the Ubuntu screen loads up and once I select Run/Install Ubuntu a lot of text appears (kinda like the MSDos prompt screen).  This runs through for a couple of seconds then stops (From memory on loading boot files? this could be wrong I will check shortly and take note).

Now, I have left this for hours, thinking that it may take a while but nothing happens, it's like it has frozen.  

Looked at a few tutorials but to no avail.

I am on a Samsung R60+ Laptop.
Intel Dual Core 1.60GHz Processor.
2Gb RAM
ATI Radeon XPRESS 1250 Graphics Card
180Gb Hard drive, which came pre split into two equal partions.

Hopefully this will make sense and if there is anything further you need to know, just give me a shout.

Any help much appreciated.

Cheers.

---

### Post by jakupl on 2008-03-21
hmmm.. can you tell men what exactly you see??
how does the final screen look?

---

### Post by Dudditz on 2008-03-21
Oh and Ichecked the disk integrety before attempting to run/install and it was fine.

---

### Post by ilrudie on 2008-03-21
Have you tried starting is Safe Graphics mode?

---

### Post by Dudditz on 2008-03-21
> **jakupl said:**
> hmmm.. can you tell men what exactly you see??
how does the final screen look?


The final screen is basically a long list of actions that the system appears to have run, all of which have [OK] at the right hand side.

Stops at this point, leaving me needing to hold down my power switch to re-boot and get back into Vista.

---

### Post by Dudditz on 2008-03-21
> **ilrudie said:**
> Have you tried starting is Safe Graphics mode?

Yeah, same problems.

Have even attempted to use WUBI but this brings up pretty much the same problems.

Assuming my system just isn't going to install Ubuntu, meaning i'm stuck with Windows :(

---

### Post by Jimmyfj on 2008-03-21
The problem seem to be your graphics card. ATI cards, or most of them require the alternate install cd to install flawlessly. Go to the [http://www.ubuntu.com](http://www.ubuntu.com)  - chose to download Ubuntu once more and check the field saying "Click here to download the alternate install cd version" or something like that. Burn another cd and make the install without the fancy GUI.

---

### Post by ByteJuggler on 2008-03-21
Random/wild idea: Try editing the kernel boot line and adding "nolapic noapic" on the end. (without the quotes)

---

### Post by ilrudie on 2008-03-21
> **Jimmyfj said:**
> The problem seem to be your graphics card. ATI cards, or most of them require the alternate install cd to install flawlessly. Go to the [http://www.ubuntu.com](http://www.ubuntu.com) - chose to download Ubuntu once more and check the field saying "Click here to download the alternate install cd version" or something like that. Burn another cd and make the install without the fancy GUI.
 
 
I agree.  I had a problem running the live cd on my Mac and I suspect the ATI graphics was the problem.  The alternate install is probably your best bet at this point.

---

### Post by Dudditz on 2008-03-21
Ok about to get the alt file.

Is it basically the same proccess to install?

---

### Post by Jimmyfj on 2008-03-21
> **Dudditz said:**
> Ok about to get the alt file.

Is it basically the same proccess to install?

The install is the same in that way that you get the same questions to answer. You just don't have the fancy desktop behind the installer.

---

### Post by Dudditz on 2008-03-21
OK cheers for your help all, I will check the Alt Version when it's done.

---

### Post by Jellman on 2008-03-22
HI there, ive got the same laptop as you, to get it working under 8.04 you need to do the following.

download the ubuntu alt CD
at the cd boot prompt press F6 and type in noapic.
once installed to your liking and you have rebooted, let the os load up, once its stoped at loading local scripts press alt F2 and login.

you need to install and configure the xorg-driver-fglrx via envyng.

Type (each line individually separated by return)
```

sudo bash [COLOR="Lime"]***//..and then enter your password, this logs you in as root.**[/COLOR]
update-pciids
apt-get update
apt-get install build-essential 
apt-get install envyng-core [COLOR="Lime"]***// Installs Video Driver Install system.**[/COLOR]
envyng-t
Select option 3 to install the ATI Preparatory video driver.
shutdown now [COLOR="Lime"]***// shuts down the computer, reboot and let it load.**[/COLOR]

```

The xserver should load up.

To get the wirless working with your card, if its the same as mine, Atheros AR5007EG you need to download and patch the madwifi kernel modual.

Loadup the terminal (applications > accessory's > terminal) and type..
```

sudo bash [COLOR="Lime"]***//Same as before.**[/COLOR]
apt-get install build-essential [COLOR="Lime"]***//Installs a build inviroment.**[/COLOR]
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
tar zxvf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
sudo make uninstall
sudo make clean
sudo make
sudo make install
sudo modprobe ath_pci [COLOR="Lime"]***//loads the patched ath_pci module.**[/COLOR]

```
...and then reboot.

The only problem i have now is that in games and such i get 3d flicker for sum reason, im looking for a resolution to this ([thread for this problem]("http://ubuntuforums.org/showthread.php?t=803412")), also some times wireless doesn't work (something to do with the patched ath_pci modual) so i just go through the wireless setup above again and it works... again, quite annoying.

I got all this information from trawling the forums trying to get  ubuntu to work on my laptop (samsung r60 plus), ill try and put references when i can.
hope that helps, all the best,
Scott

---

### Post by yisun on 2008-05-20
Hi, Jellman

I have the same laptop. When I followed your instructions to 

ati-config --initial

there is some problem reads

"Device section "configured video Device" must have a driver line
aticonfig: Parsing the configuration file failed..."

Do you know how to fix this? And could you please post your file "/etc/X11/xorg.conf" onto this message. I am thinking maybe I can replace my file with your right one.

Many thanks.
> **Jellman said:**
> HI there, ive got the same laptop as you, to get it working under 7.10 you need to do the following.

download the ubuntu alt CD
at the cd boot prompt press F6 and type in noapic.
once installed to your liking and you have rebooted, let the os load up, once its stoped at loading local scripts press alt F2 and login.

you need to install and configure the xorg-driver-fglrx.

Type (each line individually separated by return)
```

sudo bash [COLOR="Lime"]***//..and then enter your password, this logs you in as root.**[/COLOR]
update-pciids
apt-get update 
apt-get install xorg-driver-fglrx [COLOR="Lime"]***// Installs you video driver.**[/COLOR]
depmod -a
ati-config --initial
ati-config --overlay-type=Xv
shutdown now [COLOR="Lime"]***// shuts down the computer, reboot and let it load.**[/COLOR]
startx
```
The xserver should load up.

To get the wirless working with your card, if its the same as mine, Atheros AR5007EG you need to download and patch the madwifi kernel modual.

Loadup the terminal (applications > accessory's > terminal) and type..
```

sudo bash [COLOR="Lime"]***//Same as before.**[/COLOR]
apt-get install build-essential [COLOR="Lime"]***//Installs a build inviroment.**[/COLOR]
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
tar zxvf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
sudo make uninstall
sudo make clean
sudo make
sudo make install
sudo modprobe ath_pci [COLOR="Lime"]***//loads the patched ath_pci module.**[/COLOR]

```
...and then reboot.

NB. this doesnt work for 8.04 as for sum reason the xorg-driver-fglrx install fails to install the correct settings to xorg.conf,  i installed 8.04 beta by running update-manager -d in the terminal. I think you could just copy over the xorg.conf (etc/X11/xorg.conf) to a fresh hardy install in the terminal to get x to load.

I got all this infomation from trawling the forums trying to get  ubuntu to work on my laptop (samsung r60 plus), ill try and put references when i can.
hope that helps, all the best,
Scott

---

### Post by Jellman on 2008-05-20
Hi there, i have an easer way to get video to work in 8.04 LTS, with the alt cd install (same procedure as described in previous post). 

Forget the bit about the xorg-driver-fglrx, insted just type

```

sudo apt-get install envyng-core
sudo envyng -t

press 3 to install the ati driver and there you go all the x11 stuff should  be done for you. I don't think you even have to touch the sources list, but if you have to just uncomment the universe and multiverse lines *.. i think*.

sudo nano /etc/apt/sorces.list
 

```

Unless you allready have installed xorg-driver-fglrx, in which case you may need to uninstall it and reinstate you previous xorg.conf.

```
 
sudo apt-get remove xorg-driver-fglrx

```

Just incase this dosent work for some reason heres my xorg.conf

```

# xorg.conf (X.Org X Window System server configuration file)
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

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Driver		"fglrx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

Sorry if this seems a little patronizing just don't wanna leave anything out :guitar:

Have fun!

Scott

---

### Post by yisun on 2008-05-21
Hi, Scott

The problem has been solved following your way.

Many thanks for your help!!!

Regards

yisun

> **Jellman said:**
> Hi there, i have an easer way to get video to work in 8.04 LTS, with the alt cd install (same procedure as described in previous post). 

Forget the bit about the xorg-driver-fglrx, insted just type

```

sudo apt-get install envyng-core
sudo envyng -t

press 3 to install the ati driver and there you go all the x11 stuff should  be done for you. I don't think you even have to touch the sources list, but if you have to just uncomment the universe and multiverse lines *.. i think*.

sudo nano /etc/apt/sorces.list
 

```

Unless you allready have installed xorg-driver-fglrx, in which case you may need to uninstall it and reinstate you previous xorg.conf.

```
 
sudo apt-get remove xorg-driver-fglrx

```

Just incase this dosent work for some reason heres my xorg.conf

```

# xorg.conf (X.Org X Window System server configuration file)
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

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Driver		"fglrx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

Sorry if this seems a little patronizing just don't wanna leave anything out :guitar:

Have fun!

Scott

---

### Post by beN..87 on 2008-05-21
exact same machine, exact same problem

this dude is on the right tract i think  

[http://warofwords.wordpress.com/2007/10/07/using-ubuntu-on-hp-6515b-ati-x1250/](http://warofwords.wordpress.com/2007/10/07/using-ubuntu-on-hp-6515b-ati-x1250/)

ive got a samsung r60 with vista on one partition - its got 2gb ram and the same 1250 chip 

when inserting the cd for ubuntu i'm getting the command line when the GUI fails
got the drivers from here 
[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

tried the command  sh ati-driver......run      -- got a return of - verifying archive integrity, all good. uncompressing.... extraction failed,,Signal caught, cleaning up

the driver is 40mb on a 128 stick - i figure maybe its trying to uncompress it in /mnt/flash and running out of space?

i tried adding --target /tmp to maybe try to get it to store it in ram  temporarily as ive got 2gb - but the --target addition doesnt work

guys - vista is the worst thing ever -  i need ubuntu on this thing bad - but i just cant get the live CD process underway - any help would be greatly appreciated

---

### Post by Jellman on 2008-05-22
Hey there, why dont you just download the 8.04 LTS *[alt]("http://mirrors.us.kernel.org/ubuntu-releases/hardy/ubuntu-8.04-alternate-i386.iso")* cd (As apposed to the desktop / live cd). install, log-in and use envyng.

```


sudo apt-get install envyng-core
sudo envyng -t


```

That seems to get the video to work on mine and yisun's systems.

---

### Post by beN..87 on 2008-05-23
> **Jellman said:**
> Hey there, why dont you just download the 8.04 LTS *[alt]("http://mirrors.us.kernel.org/ubuntu-releases/hardy/ubuntu-8.04-alternate-i386.iso")* cd (As apposed to the desktop / live cd). install, log-in and use envyng.

```


sudo apt-get install envyng-core
sudo envyng -t


```

That seems to get the video to work on mine and yisun's systems.

yeah i 'm on the r60 - no wireless to use envyNG

---

### Post by beN..87 on 2008-05-23
> **Jellman said:**
> Hey there, why dont you just download the 8.04 LTS *[alt]("http://mirrors.us.kernel.org/ubuntu-releases/hardy/ubuntu-8.04-alternate-i386.iso")* cd (As apposed to the desktop / live cd). install, log-in and use envyng.

```


sudo apt-get install envyng-core
sudo envyng -t


```

That seems to get the video to work on mine and yisun's systems.

guys how are you using envyNG ? it has to download from the internet - but heres my situation -

brand new r60 - same as you guys 
fres alt - install cd of ubuntu
alt F2 login to shell

so how can i connect to the net at this point to use envy?

---

### Post by Jellman on 2008-05-23
cant you get to a ethernet line for long enuff to install envy ng and download the patched wirless modual?

---

### Post by beN..87 on 2008-05-30
> **Jellman said:**
> cant you get to a ethernet line for long enuff to install envy ng and download the patched wirless modual?


its all good guys, solved -- install the ATI graphics drivers manually by getting them from their website - easy peasy!

---

### Post by beN..87 on 2008-05-30
> **Jellman said:**
> HI there, ive got the same laptop as you, to get it working under 8.04 you need to do the following.

The only problem i have now is that in games and such i get 3d flicker for sum reason, im looking for a resolution to this ([thread for this problem]("http://ubuntuforums.org/showthread.php?t=803412")), also some times wireless doesn't work (something to do with the patched ath_pci modual) so i just go through the wireless setup above again and it works... again, quite annoying.

I got all this information from trawling the forums trying to get  ubuntu to work on my laptop (samsung r60 plus), ill try and put references when i can.
hope that helps, all the best,
Scott


got the wifi and graphics working on the R60 - did anyone find out how to fix this flicker on the video?? same probs

---


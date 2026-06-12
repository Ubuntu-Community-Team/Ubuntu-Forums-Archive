---
title: "[SOLVED] Total n00b: x - Server not working?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Jeztastic on 2007-11-26
Hi,

I am trying my first Linux install. I am installing Ubuntu Studio, as Vi$ta will not recognise my old soundcard. 

I have burnt ISO, installed Ubuntu etc, however, when I reboot, it tells me that the X-Server is not working and my graphics hardware is not set up properly.

I have done a search on this to no avail. Please bear in mind that I have not successfully installed Linux ever!

I have a Toshiba Satellite A210, Dual Turion 64 processors, ATI Radeon Graphics. I have installed on a USB 40 GB HDD.

Please help!

Jez

---

### Post by nickpaton on 2007-11-26
Welcome to ubuntu and the forums.

Which version version have you downloaded and is it 32 or 64bit?

Also looking at the news on the [URL="http://ubuntustudio.org/home"]Studio home page
[/URL], there is an updated version available as of 23rd Nov 07 which maybe you should try.

There are also some basic checks you can do.

When installing the DVD, at the first boot prompt screen run the 'Check the CD for defects' option to make sure you have downloaded the OS and burnt the DVD correctly.

Other than that at this stage I would suggest you try a reinstall and see what happens.  If you are not sure what you are doing, have a look at this [installation HOWTO]("http://www.howtoforge.com/ubuntustudio_7.04") from the wiki.

Alternatively, if you are still having problems you may want to consider installing one of the regular packages like Gutsy 7.10.  You will still be able to install all of the programs which are available as standard in Studio quite easily.

The regular download page can be found [here]("http://www.ubuntu.com/getubuntu/download").

Then having got used to the regular distro you could switch to Studio.

Good luck and let us know how you get on.

Nick

---

### Post by Jeztastic on 2007-11-26
The file I downloaded was ubuntustudio-7.10-alternate-i386. So 32-bit. I'm assuming that 64 bit drivers and compatibility might be a problem.

I think I started downloading it just after the new version went up. I tried a re-install and it did the same thing second time round. Is it likely to be a hardware incompatibility? Am I gonna need to find other drivers for my graphics card?

Cheers,

Jez

---

### Post by Jeztastic on 2007-11-27
Hi, 

Also,

Can I run Ubuntu studio live from the DVD?

Thanks!

Jez

---

### Post by nickpaton on 2007-11-27
Hi Jez

Sorry to hear you are having problems.  the 32bit download is compatible with 64bit drivers so that shouldn't normally ever be a problem.

Also normally ATI graphics drivers are available in the core distro with the later Ubuntu versions, so I wouldn't expect that to be an issue.  
In the 'normal' Feisty and Gutsy distros, they are available via the Restricted Drivers manager which pops up at the end of the installation process and allows you to then install them.

Looking through the HOWTO link I posted above, there doesn't appear to be an option to run Studio as a live DVD.

Since you've tried installing it twice (and I hope you carried out the check CD test I mentioned too), I would advise you to download Gutsy i386 32bit alternative and try that as a live CD, and then if you are OK with that to then install it.

Then when you are OK with the base installation you can move on to adding the 'goodies' you want.  Of course we will be very happy to guide you through that at the time if needs be.

Sorry I can't be much more help.

Nick

---

### Post by Jeztastic on 2007-11-27
Thanks for yr help Nick.

I checked the DVD and it's all OK. 

I am using a pretty new laptop, so it's possible the video drivers aren't in the distro. 

The install also seemed unhappy with my network settings... Am I right in thinking I will be unable to get different drivers if I'm not on the internet?

I will try Gutsy Gibbon as you suggest, and get back to you...

Many thanks!

---

### Post by nickpaton on 2007-11-27
Jez

When you  install Gutsy make sure you have the laptop wired LAN output connected to your router.  This will help in your wired LAN port being detected and the drivers loaded.

If you are still having graphics and network problems could you post the following outputs from a terminal, which will identify the hardware being used / detected:

Wired network:

```
lspci | grep -i ethernet
``` 

Wireless network:

```
lspci | grep -i wireless
``` 

Graphics chip:

```
lspci | grep -i vga
``` 

Also for the networks, please could you post the output of

```
ifconfig
```

and 

```
iwconfig
```

That should keep you busy for a while!

Nick

---

### Post by jken146 on 2007-11-27
```
dpkg-reconfigure xserver-xorg
```

---

### Post by Jeztastic on 2007-11-27
Hey Nick,

I've successfully installed Gutsy Gibbon now (yay!) however, it's not recognising my wireless or graphics - i got your latest post a little late.

I think I'm correct in thinking that when I sort out the internet connection, gutsy will let me install the graphics drivers by downloading them. It told me I needed xorg-driver-fglrx.

Anyhow, I will follow your instructions and let you know!

Thanks for all your help thus far! Big kudos for all the support I'm getting!

Jez

---

### Post by Jeztastic on 2007-11-27
> **jken146 said:**
> ```
dpkg-reconfigure xserver-xorg
```

Thanks for the hint, but I am gonna go with Gutsy for a while and see how that goes... :)

---

### Post by nickpaton on 2007-11-28
> **Jeztastic said:**
> Hey Nick,

I've successfully installed Gutsy Gibbon now (yay!) however, it's not recognising my wireless or graphics - i got your latest post a little late.

I think I'm correct in thinking that when I sort out the internet connection, gutsy will let me install the graphics drivers by downloading them. It told me I needed xorg-driver-fglrx.
Jez

First off Jez, ignore the wireless side of things for the time being.  

Are you able to access the Internet using a LAN cable from the laptop to the router? 

If not can you post all of the terminals I requested and we'll take it from there.
When you post the wireless config, can you make sure your wireless is on, on the laptop.

Could you also tell me the make and model of your router and confirm that you do connect directly to broadband via it.

Well done so far!

Nick

---

### Post by Jeztastic on 2007-11-28
OK, I haven't been able to try the LAN cable as it's in the loft and my partner is asleep... Would not make myself popular getting it now!

lspci | grep -i ethernet 

14:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)


lspci | grep -i vga 

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series

eth0      


ifconfig

Link encap:Ethernet  HWaddr 00:1B:38:17:1A:E7  
          
UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:0 (0.0 b)  
TX bytes:0 (0.0 b)
          
Interrupt:17 Base address:0xc000 

lo        
Link encap:Local Loopback  
          
inet addr:127.0.0.1  Mask:255.0.0.0
          
UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:0 
          
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


iwconfig


lo        no wireless extensions.

eth0      no wireless extensions.

Hope this is clearer to you than me. The wireless was switched on. The router is a 2700HG-B Gateway, and it connects direct to the broadband.

Thanks again.

---

### Post by nickpaton on 2007-11-29
Thanks for all that.  Meanings:

> lspci | grep -i ethernet

14:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

Identifies the wireless hardware in your laptop.

> lspci | grep -i vga

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series


Ditto for your graphics card.

So you can see that if you go* lspci | grep -i any-bit-of-hardware*, the command will tell you what's fitted.



> ifconfig

Link encap:Ethernet HWaddr 00:1B:38:17:1A:E7

UP BROADCAST MULTICAST MTU:1500 Metric:1

RX packets:0 errors:0 dropped:0 overruns:0 frame:0

TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:1000

RX bytes:0 (0.0 b)
TX bytes:0 (0.0 b)

Interrupt:17 Base address:0xc000

lo
Link encap:Local Loopback

inet addr:127.0.0.1 Mask:255.0.0.0

UP LOOPBACK RUNNING MTU:16436 Metric:1

RX packets:0 errors:0 dropped:0 overruns:0 frame:0

TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:0

RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

'if config' tells you if your wired LAN port is working. Looking at the top section, I suspect it had ETH1 in front of it, which identifies your wired LAN port.
It says the port's working, since it can potentially send and receive data, but because it's not connected to the router, there's been no data movement.
RX means received and TX transmitted or sent.

> iwconfig


lo no wireless extensions.

eth0 no wireless extensions.

Eth0 identifys your wireless connection but because there are no drivers installed, it isn't working.

Hopefully you can see how the two sets of commands first of all identify the hardware and in the case of the LAN ports show whether they are working or not.  

Before you can do much more, you need to get hold of the LAN cable and connect to it.  There's some work to do with downloading stuff, and getting the graphics to work etc via Restricted Drivers Manager (RDM).

It could also be the case that your AR5006 wireless driver is in RDM as well, but if not we can take you through getting that working as well.

Have you ever been connected via the LAN cable since installing Gutsy?  And if so have you installed the updates that have come out after Gutsy was released etc?

Where are you at in regard to installing the various Firefox plugins, java flash etc, and the mulitmedia and video extras?

If you've done none of this, we'll point you in the right direction if you need help there. 

Nick

---

### Post by Jeztastic on 2007-11-29
OK, great.

Got the LAN cable, will give it all a try and let you know what doesn't work.

I am very conversant with Firefox addons in Windows, and I have installed Codecs etc in Windows too. If it all works the same in Linux I'll be laughing. 

Watch this space!

---

### Post by Jeztastic on 2007-11-29
OK, am now online via Ethernet. 

I've tried to enable the driver in the RDM menu, but I'm getting this message: > The software source for the package

   xorg-driver-fglrx

 is not enabled.

When I try and download anything using add/remove programs, I get this message:

> Kopete cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

Any suggestions?

Jez

---

### Post by nickpaton on 2007-11-29
Can you do the terminal command in post #8.

[I]The explanation:

dpkg stands for Debian package used to install remove and provide information about debian software packages.

reconfigure is how it reads.

xserver-xorg: easiest to quote from wikipedia - X provides the basic framework, or primitives, for building GUI environments: drawing and moving windows on the screen and interacting with a mouse and/or keyboard.
xorg is the program used to make changes to xserver.[/I]

If that does not let you install the graphics via RDM can you post the output of

```
gksudo gedit /etc/X11/xorg.conf
```

Could you put the output between  by clicking on # at the top of the posting box.  Makes it neater and easier to read!.

Re installing firefox video and multimedia plugins, it's different to Windows, but equally straight forward - have a look at this very comprehensive installation 'manual' for Gutsy:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy") 

We can go through this more slowly when you've got the graphics and wireless set up, but it makes interesting and useful reading in the meantime.

Finally, I don't like that kopete message you're getting.  Kopete is a type of instant messenger program.

When you use Add/Remove you are plugged into the LAN cable and have rebooted the laptop after you've plugged it in.  make sure you can access the Internet before using Add/Remove.

If you still have problems could you tell me if you have ever had any updates to Gutsy - shows with a big sign in the top right corner 'updates available ' and a box - you should have had some.

If you haven't, can you run

```
sudo apt-get update
```

which should download and install all the updates.

If that doesn't work and you get error messages can you post

```
cat /etc/apt/sources.list
```

This will list your available repositories which link to the various sites which provide the updates.

Nick

---

### Post by Jeztastic on 2007-11-29
> **nickpaton said:**
> Can you do the terminal command in post #8.

[I]The explanation:

dpkg stands for Debian package used to install remove and provide information about debian software packages.

reconfigure is how it reads.

xserver-xorg: easiest to quote from wikipedia - X provides the basic framework, or primitives, for building GUI environments: drawing and moving windows on the screen and interacting with a mouse and/or keyboard.
xorg is the program used to make changes to xserver.

[/I]

If that does not let you install the graphics via RDM can you post the output of

```
gksudo gedit /etc/X11/xorg.conf
```

I tried the code from post #8, and I got this error message:

```
/usr/sbin/dpkg-reconfigure must be run as root
```

Output:

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
	Option		"XkbLayout"	"gb"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
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
	InputDevice	"Synaptics Touchpad"
EndSection
```

> **nickpaton said:**
> 

Re installing firefox video and multimedia plugins, it's different to Windows, but equally straight forward - have a look at this very comprehensive installation 'manual' for Gutsy:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy") 

We can go through this more slowly when you've got the graphics and wireless set up, but it makes interesting and useful reading in the meantime.



Thanks!

> **nickpaton said:**
> 

Finally, I don't like that kopete message you're getting.  Kopete is a type of instant messenger program.


Me neither. It happened with whatever I tried to install through Add/Remove. Have   had success with some Firefox addons done through Firefox though.

> **nickpaton said:**
> 

When you use Add/Remove you are plugged into the LAN cable and have rebooted the laptop after you've plugged it in.  make sure you can access the Internet before using Add/Remove.

If you still have problems could you tell me if you have ever had any updates to Gutsy - shows with a big sign in the top right corner 'updates available ' and a box - you should have had some.

If you haven't, can you run

```
sudo apt-get update
```

which should download and install all the updates.


Done.

---

### Post by nickpaton on 2007-11-30
Thanks for the output of xorg which shows you have a generic graphics driver installed - no Radeon in site!

The Add/Remove Kopete problem - did you have the LAN cable plugged in and had previously checked that you could connect to the Internet?  The reason is that the first thing Add/Remove does is to check that your repositories are up to date.

Apologies - my bad for giving you a duff command.
The clue as to why dpkg didn't run is that is says it needs to be run as root.  So whenever you see that try putting 'sudo' in front of the command

Try 'sudo dpkg' etc again and see what happens and then RDM.

If that fails, I had a look in the forums under Radeon x1200 for any probs etc., and found the following post which I suggest you carry out step by step (copy and paste into a terminal one line at a time followed by enter key):

[http://ubuntuforums.org/showthread.php?t=414194]("http://ubuntuforums.org/showthread.php?t=414194")

It does refer to 7.04 but would still apply here.

If all seems to go well try this very general test in a terminal:

```
glxgears
```

If the driver is installed correctly you should see three gear wheels SMOOTHLY turning.

If that's OK we'll move onto the wireless driver.
So once again see if it is available in RDM and if so, with the LAN cable connected install it.  If you manage to install the driver Ok check it is there by using iwconfig, and you'll see a much bigger output than previously (no wireless installed!).

Configuration is then via System > Administration > Network > & click on Wireless Connection.
Deselect Roaming mode, and complete the Essid, password type select encryption type, and in network password your encryption key.

Configuration automatic dhcp.

Close and save etc and reboot and try wirelessly!  If that fails try temporarily removing all encryption off the router and the configuration and try that.  Remember each time you do something needs a reboot.

OK enough there for you to be getting on with!

Good luck again

Nick

---

### Post by Jeztastic on 2007-12-01
When I last booted Ubuntu, Firefox would not load. It said that access to profile files was restricted. I tried to edit them via the GUI, but they were greyed out. I then ran the sudo dpkg command and rebooted, however Ubuntu will now not boot and hung on a black screen.

Grrr.

If as I suspect I need to re-install, is there a way of installing Grub on my laptop drive and Ubuntu on the USB hard drive? Currently, vista will not load without the USB drive connected, which is most inconvenient.

Thanks

---

### Post by Jeztastic on 2007-12-02
OK, I've now re-installed, and that seems to have sorted the video drivers out - they are working OK. :-) I am working on the Grub problem.

Could you please advise me on getting the wireless working, and then I can move onto the audio side of things!

---


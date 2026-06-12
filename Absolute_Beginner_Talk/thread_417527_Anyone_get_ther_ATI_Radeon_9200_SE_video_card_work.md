---
title: "Anyone get ther ATI Radeon 9200 SE video card working with Feisty?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-04-21
With much trial and error, and finally success, I had my ATI Radeon 9200 SE video card working fine in Dapper and Edgy. Now with Feisty I am back to trying to fix it again. All the things I did to get it to work in Dapper and Edgy will not work for me in Feisty. Any suggestions will be greatly appreciated.
kh

---

### Post by riven0 on 2007-04-21
What exactly have you done already? Have you tried choosing the vesa driver when re-configuring  the xserver? And how about installing the official drivers from the ati website?

---

### Post by kittyhawk63 on 2007-04-21
> **riven0 said:**
> What exactly have you done already? Have you tried choosing the vesa driver when re-configuring  the xserver? And how about installing the official drivers from the ati website?

The official drivers is/are what I tried because they worked in Dapper and Edgy. I can boot into Feisty but I eventually have a screen freeze or a blank screen appears and I have to ctrl+alt+backspace.

Where do I get the vesa driver and how do I reconfigure the xserver?

---

### Post by riven0 on 2007-04-21
It could be a problem with the official drivers. So open the terminal and copy and paste this:

> sudo dpkg-reconfigure xserver-xorg

Then when it gets to video card drivers, you can using the open source driver, **ati**, which is what I use for my 9200SE card. Or, if that doesn't work, try Vesa. Vesa performs very slow, though, so you may want to try re-installing the official drivers again to get better performance. Try un-installing the official ati drivers and then reinstall from the repository, if you can.

---

### Post by kittyhawk63 on 2007-04-21
riven0
Thanks for the info. I ran the program. I hope that will do the trick. Thanks again.

Edit: Tried vesa...same problems of freezing or going blank screen.

Oh! Would you mind posting me your sources.list and let me look at it?
kh

---

### Post by Ferri on 2007-04-22
I've been able to get this card working.
You should take into account that your card is not supported in the latest versions from ati, and these affects also "fglrx" versions you can find in multiverse/restricted repositories. If you want your ATI 9200 SE work in Feisty, you have to use the open source driver, which has no 3D acceleration and, at least in my machine, slower general performance.

---

### Post by hibernatus on 2007-04-22
> Ferri  	I've been able to get this card working.
You should take into account that your card is not supported in the latest versions from ati, and these affects also "fglrx" versions you can find in multiverse/restricted repositories. If you want your ATI 9200 SE work in Feisty, you have to use the open source driver, which has no 3D acceleration and, at least in my machine, slower general performance.


Hi,
this is a regreation :-( this is not good!!!!

I have exactly the same issues  i have tryed with the ati and fglrx driver but it's not working. 

so is this meening that the only driver support is the vesa?

---

### Post by hibernatus on 2007-04-22
an aditional question if i put driver = vesa 

 the 1440X900 resolution does'nt work => did you succed to setup it?

thanks

John

---

### Post by kittyhawk63 on 2007-04-22
I appreciate all replies. I am hoping someone will offer a suggestion that will resolve this issue.

I think it is time that all ATI video card buyers with Linux start bothering the dickens out of ATI until they do something about this. You would think they would want to support their customer base. Maybe it is time we put the whammy on them and start passing the word to all our friends how bad ATI cards are with Linux and not to buy them. Maybe a loss in revenue may wake them up.
kh

Contact page for ATI:
[http://ati.de/companyinfo/contact/index.html](http://ati.de/companyinfo/contact/index.html)

e-mail public relations:
[EMAIL="public.relations@amd.com"]public.relations@amd.com[/EMAIL]

I e-mailed this note to [EMAIL="public.relations@amd.com"]public.relations@amd.com[/EMAIL]:
AMD/ATI: 
   I am a purchaser of a Compaq Presario computer with both AMD and ATI  hardware. I am also a Linux user. I have worked relentlessly trying to  get your ATI drivers to work with different packages of Linux. It is one  frustrating experience. 
   My question: Why doesn't the AMD and ATI partnership work together  to support their customer base of Linux users that you do with Windows users? There is an exploding  base of Linux users growing around the  globe. If you expect and especially desire that your sales profile  continue to grow in the marketplace, I would expect that you would  willingly support primarily more than one OS. As Linux becomes easier and easier to install  (it is not that hard now with the LiveCDs and their "install" button  feature) more and more people will leave MS in the dust. It is  inevitable with MS's dominance philosophy toward its customers. 
   With the advent of Vista, I have noticed many Windows users  coming into Linux forums. They are sick and tired of the dictatorial  attitude of MS over their machines. Vista was the stick that broke the  camel's back for thousands of them. There will be many more to migrate  as soon as they find out about  the freedom experienced in Linux. Run a few Linux forums and you will  see that most of them use Nvidia cards. They are advising noobies to buy  them as well. I will be doing that very soon. My ATI card has crashed at  least one since I have started writing this note to you. I don't like  that. I don't have to put up with it. There are other companies available to us Linux users. We don't need ATI cards.
   Personally, if I were AMD/ATI, I would look at the handwriting on  the wall. Support Linux or lose revenue in an ever-growing base of Linux  users. It's your call. 
Respectfully yours, 
Dr. .... .......

Edit: You're free to use this or make up your own. Just make sure you sign it personally.

---

### Post by leo287 on 2007-04-23
> **Ferri said:**
> I've been able to get this card working.
You should take into account that your card is not supported in the latest versions from ati, and these affects also "fglrx" versions you can find in multiverse/restricted repositories. If you want your ATI 9200 SE work in Feisty, you have to use the open source driver, which has no 3D acceleration and, at least in my machine, slower general performance.

could you please post how did you make this card working in feisty?

I am having 2 big issues currently with the open source driver: 1. the gdm login screen is totally corrupted (am able to login) 2. am not able to get the 1440x900 à 75Mhz working (displays only at 60Mhz)and very bad display. It works in 1280x1024 @ 60Mhz the sceen is like a 4:3 image diplayed on a 16:9 screen. Under winXP it works very well at 1440x900 @ 75.

Could you post your xorg.conf file and and if I need the ati closed source driver !

Thanks

---

### Post by WHICKS on 2007-04-24
You can try this, it should work

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

---

### Post by kittyhawk63 on 2007-04-25
None of the suggestions has worked so far.

Has anyone gotten their ATI Radeon 9200 SE to work properly? If you have, would you be so kind as to post exactly "**EVERY**" step that you took to get it to work. I have had nothing but problems in every version since Dapper. After five weeks of battling back and forth, I finally got it to work in Dapper. No luck in Edgy and now in Feisty.

Please give repositories installed.
Did you  install anything else or run any commands in Terminal?
Please post your xorg.conf file.

Thank you.

---

### Post by compmodder26 on 2007-04-25
The newest drivers from ATI do not support cards under 9500.  Their 8.28 driver that does support 9200 doesn't support Xorg 7.2 which is in Feisty.  The only other choice has to be the open source radeon driver.

What happened when you tried the steps from the link WHICKS gave?

---

### Post by kittyhawk63 on 2007-04-25
> **compmodder26 said:**
> The newest drivers from ATI do not support cards under 9500.  Their 8.28 driver that does support 9200 doesn't support Xorg 7.2 which is in Feisty.  The only other choice has to be the open source radeon driver.

What happened when you tried the steps from the link WHICKS gave?

I followed WHICKS suggestion two times with the same results. Locked completely out of Linux. Had to restore by saved xorg.conf file.

What is the open source Radeon driver and how do I find it to give it a try?

Waiting for your reply.
kh

---

### Post by Michl on 2007-04-25
I'm not sure how relevant this is, but I have an ATI Radeon x300 and had not problems installing Feisty.  The driver the installation chose (I had to do nothing, thank you) was "ati"
Michl

---

### Post by kittyhawk63 on 2007-04-25
> **Michl said:**
> I'm not sure how relevant this is, but I have an ATI Radeon x300 and had not problems installing Feisty.  The driver the installation chose (I had to do nothing, thank you) was "ati"
Michl

You've been most fortunate. I'm glad some ATI users are getting their money's worth. I bought this card late last year from Circuit City. Now I may have to go out and spend some more money to get a card that ATI should support in Linux. I wrote ATI a note and hope that they will understand they are doing their customers who use Linux a bad PR job. I won't buy another card from AMD who now owns ATI, or at least is a partner with them. :mad:
kh

---

### Post by Ferri on 2007-04-25
The guide posted above by WHICKS is very similar (or identical) to the one I used.
The drivers are the open-source ones, provided in the default installation.
My xorg.conf:
> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
	Option		"XkbVariant"	"cat"
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
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 SE]"
	Driver		"ati"
        Option          "AGPMode"       "8"
        Option          "AccelMethod"   "EXA"
        Option          "ColorTiling"   "on"
	BusID		"PCI:1:0:0"
	Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"L1710M"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 SE]"
	Monitor		"L1710M"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

However, as I said in my previous message and elsewhere in the forums, the card works worse now in Feisty than it did with Edgy, because I can't use the propietary drivers.
I was just thinking that some of the issues might be related to an attempt to upgrade from a previous Ubuntu version; I suppose the upgrade tool updates the ATI propietary drivers and X doesn't work anymore. I didn't have this issue because I did a fresh install (just kept my /home untouched in a separate partition.

---

### Post by kittyhawk63 on 2007-04-25
Ferri,
I'll try this and see what happens. I will post my results.
Thanks.
kh

---

### Post by kittyhawk63 on 2007-04-25
Ferri
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
	Option		"XkbVariant"	"cat"
EndSection

kittyhawk
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
This line is missing about  	Option		"XkbVariant"	"cat"
EndSection

Would these differences have any effect?

I have changed the other lines and will reboot to see if they work.

---

### Post by kittyhawk63 on 2007-04-25
Ferri,
I made the changes in xorg.conf to reflect yours and I was locked out of Linux. I had to reload my saved .bak of xorg.conf. Nothing gained, nothing lost. Thanks for your input.

Anybody else that would like to give this a try?

Maybe I need to go to the store and replace my CD/RW drive that crashed the other day when I accidentally hit the power switch and lost both a hard drive and my CD/RW drive. Must have had a power surge. I was able to get my hard drive working again after several hours. I've had no luck with the CD/RW drive, however. 
With a new CD/RW drive, I can reburn Feisty and do a fresh install. Maybe that will help my situation. If that doesn't help, then I can return to the store and buy a Nvidia card. However, I am also aware that some Nvidia owners are having problems.

Edit: I found out what happened with my CD/RW drive. I don't know how, but it became unplugged in the back. I plugged it in. Bingo. It is working again.

kh

---

### Post by compmodder26 on 2007-04-25
In your xorg.conf, did you change the driver from "ati" to "radeon"?  Also, try commenting out all the options except for AGPMode in the "Device" section.

---

### Post by kittyhawk63 on 2007-04-25
> **compmodder26 said:**
> In your xorg.conf, did you change the driver from "ati" to "radeon"?  Also, try commenting out all the options except for AGPMode in the "Device" section.

Ok, I will try this. Nothing tried, nothing gained. Thanks. I still had ATI, which is what Ferri has in his xorg.conf, and his card works. Trying Radeon and commenting.
kh

---

### Post by kittyhawk63 on 2007-04-25
Tried Radeon and commenting. Locked out of Linux. I am going to download Feisty's ISO and give that a try. Maybe a fresh install will do the trick. I installed Feisty doing an upgrade. It may be there are some old files that are causing the problem since I upgraded with Edgy and had the same problem there in my last install.
See you on the other side.
kh

---

### Post by guardsman85 on 2007-04-25
Not sure if this will help you or not, but my ATI card wouldn't work after I upgraded to Feisty until I followed the instructions at [http://tinyurl.com/2wv7jd](http://tinyurl.com/2wv7jd).  It seems you have to blacklist an older version of the fglrx driver to get everything to work correctly.  Hopefully it helps!  Good luck!

---

### Post by kittyhawk63 on 2007-04-25
> **guardsman85 said:**
> Not sure if this will help you or not, but my ATI card wouldn't work after I upgraded to Feisty until I followed the instructions at [http://tinyurl.com/2wv7jd](http://tinyurl.com/2wv7jd).  It seems you have to blacklist an older version of the fglrx driver to get everything to work correctly.  Hopefully it helps!  Good luck!

Guardsman,
Thanks.
I will try anything...before I have to do another install. I am downloading the ISO right now, just in case.
Thanks again.
kh

---

### Post by MWHICKS on 2007-04-25
I will admit, mine was a fresh install on a virgin hard drive, but everything has worked just fine so far, and I can utilize all the eye candy in beryl so far.

---

### Post by 007Bond on 2007-04-25
KH
Try using Envy yet?
If so reinstalling desktop (Gnome/KDE) then your graphics driver.

---

### Post by kittyhawk63 on 2007-04-25
> **007Bond said:**
> KH
Try using Envy yet?
If so reinstalling desktop (Gnome/KDE) then your graphics driver.

Yes. I tried it in Dapper, Edgy and Feisty.  Never worked except in Dapper.
kh

---

### Post by hibernatus on 2007-04-26
> kittyhawk63  	
Quote:
Originally Posted by 007Bond View Post
KH
Try using Envy yet?
If so reinstalling desktop (Gnome/KDE) then your graphics driver.
Yes. I tried it in Dapper, Edgy and Feisty. Never worked except in Dapper.
kh

I have actualy the same issues tham you, as allrady post in this thread.

For my part I have tryed 

1 : fglrx driver => don't work
2 : ATI driver => don't work
3 : radeon => don't work

I had spend a lot of time in draper to succesfully used this card 
in edgy the card was still working fine after the upgrade.

but since my new upgrade this wasn't working correctly. i thing that with all threads and the historical of issues with ATI Card, before making a new realese of Ubuntu they should take care of this. I 'm not really sure that they did ](*,) 

I have to allso upgrade my laptop (DELL D620) but i don't thing i will do it i supposed that their are allso a lot of issues with the intel chipset.

so all of this doesn't help us. my suprise with my 9200 SE card on my desktop is when i start my xserveur it work for few second and then it freeze exept with the flgrx driver => don't sart.

Is it possible to find "an expert" of the xorg to 

1 : help us to configure your xorg.conf
2 : help us to setup step by step your graphique card

---

### Post by Ferri on 2007-04-26
> **kittyhawk63 said:**
> Ferri
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
	Option		"XkbVariant"	"cat"
EndSection

kittyhawk
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
This line is missing about  	Option		"XkbVariant"	"cat"
EndSection

Would these differences have any effect?

I have changed the other lines and will reboot to see if they work.

These differences just reflect differences in our keyboards and language settings. You use a standard us-english keyboard and mine is spanish keyboard with suport for catalan.

After reading the  [[COLOR="Blue"]tutorial proposed by WHICKS[/COLOR]]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon") I've changed some things and I've been able even to run Beryl quite successfully, which is a great improvement for me from edgy.

I'm sorry to see that what works for me doesn't apparently help in your case.

---

### Post by philbert on 2007-04-26
Hello KittyHawk,
I am running a ATI 9200 on a DFI board with a Samsung 940MW monitor. I have not had a problem with my card on several Linux distros, including Feisty Fawn. )I have had more problems with the monitor than the card with Fiesty Fawn and had to settle for 1280 X 768 until I can get Fawn to think it is a SyncMaster.) Anyhow, Since you may be using a board with an onboard video, it is possible the problem is the inability for Feisty Fawn to to ignore the onboard video, perhaps disabling  the onboard video in BIOS and forcing Feisty Fawn to recognize the 9200 as the only video?

Maybe this will help
Philbert

---

### Post by kittyhawk63 on 2007-04-26
[quote=philbert;2541760]Hello KittyHawk,
I am running a ATI 9200 on a DFI board with a Samsung 940MW monitor. I have not had a problem with my card on several Linux distros, including Feisty Fawn. )I have had more problems with the monitor than the card with Fiesty Fawn and had to settle for 1280 X 768 until I can get Fawn to think it is a SyncMaster.) Anyhow, Since you may be using a board with an onboard video, it is possible the problem is the inability for Feisty Fawn to to ignore the onboard video, perhaps disabling  the onboard video in BIOS and forcing Feisty Fawn to recognize the 9200 as the only video?
Maybe this will help.
 
**Well. I still have WinXP on another drive. I don't know if it would like this suggestion.**

[B]I am trying to get a burn of the ISO right now. Having problem with burning. Ruined four CDs so far. aarg.
Edit: I was able to get my four CDs restored after considerable fiddling around.

I reinstalled Feisty twice since my first post in this thread. I'm sure it won't be the last. Somehow I messed up my CD Rom player. I have had to use the CD-R/RW Player. It is much slower in "speed" than the other. Takes about four times longer to install.
kh[/B]

---

### Post by kittyhawk63 on 2007-04-27
> **Ferri said:**
> I've been able to get this card working.
You should take into account that your card is not supported in the latest versions from ati, and these affects also "fglrx" versions you can find in multiverse/restricted repositories. If you want your ATI 9200 SE work in Feisty, you have to use the open source driver, which has no 3D acceleration and, at least in my machine, slower general performance.

What is the name of the open source driver in Feisty? Is it Radeon, Vesa, ATI, or something else? How can you find out if you have the open source driver installed?
kh

---

### Post by gitti on 2007-05-01
I have an Ati Radeon 9200 SE agp with 128MB RAM.
At first installation of feisty from cd, my graphic card works greatly, except of the tv-out.
So I tried to enable that following a lot of guides all around internet and after that my drivers are become corrupted.
I have replaced the xorg.conf with the one that is included in live cd, I have reinstalled the packages that are marked as installed on live cd ad removed the others. So, finally, my system says "Direct rendering: YES".

But if I activate compiz the screen become white and I must wait 30 seconds to return on a working system.

Can you help me? O:)

Thanks ](*,)

---


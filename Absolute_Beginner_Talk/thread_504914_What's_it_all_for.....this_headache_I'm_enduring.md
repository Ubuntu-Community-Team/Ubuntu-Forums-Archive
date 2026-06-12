---
title: "What's it all for.....this headache I'm enduring?"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by SPQQKY on 2007-07-19
Noob to Linux, but I'm no dumby, however, it's vague instructions and complicated procedures that have kept me from Linux OS' in the past. I decided to give Ubuntu a try, but simple things like just installing my gfx card drivers with instructions like this....

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

* development tools like make and gcc are installed
* the linux-headers package matching the installed Linux kernel is installed
* the pkg-config and xserver-xorg-dev packages are installed
* the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist
If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

DISABLED_MODULES="nv nvidia_new"
Additionally, delete the following file if it exists:
rm -f /lib/linux-restricted-modules/.nvidia_new_installed

....that have kept me from using Linux. All I want to do is view the desktop in my monitors native resolution of 1680x1050 and that seems impossible at this point. 
What is the point of Linux? What does it offer that Windows can't? At this point the only thing I can see it offering is added trips to the pharmacy for headache medicine. 
Why can't I get the drivers to install. I have followed several guides and gotten tips from users from other forums only to come up empty handed.

---

### Post by diatribe on 2007-07-19
I'm fairly sure there is a box that you select that says 'use restricted drivers'.  If you can not click inside a box perhaps ubuntu isnt for you?

---

### Post by toutatis on 2007-07-19
I think most problems on this forum are related to video cards or it's drivers. I agree that's the weakest point of the Linux world. You still need to solve some technical problems before you've got it all up and running. I'm think that's the main reason for scaring people off.

Before I started with Ubuntu a couple of days ago, I tried Fedora. Well Ubuntu with Wubi-installer made live a lot easier for dummies like me.:(

Roel

---

### Post by aysiu on 2007-07-19
How about using different instructions, then?
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by rickycodie on 2007-07-19
use aysiu's instructions very easy to follow and very reliable.

---

### Post by SPQQKY on 2007-07-19
> **diatribe said:**
> I'm fairly sure there is a box that you select that says 'use restricted drivers'.  If you can not click inside a box perhaps ubuntu isnt for you?
Well, it's answers like that which do not help a person at all. Thanks for nothing, bud.:confused:

[QUOTE=aysiu]How about using different instructions, then?
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)[/QUOTE]
I tried that and it says my hardware does not need any restricted drivers. That is the only thing I get.

---

### Post by BlahMan_of.Doom on 2007-07-19
The easiest way to install nVidia drivers is to use Envy.

Go to your terminal, and type
```
sudo apt-get install envy
```

Now, after it's done installing, type sudo envy -t for the textual interface, or envy -g for the GTK frontend (graphical). Now, hit uninstall the nVidia drivers. This will uninstall the already existing nVidia drivers, and put the default drivers back in. Then, hit Install the nVidia drivers. And when it asks you, let it configure your xorg.conf.
That should do it..

---

### Post by aysiu on 2007-07-19
And you definitely have an Nvidia graphics card?

---

### Post by aysiu on 2007-07-19
> **BlahMan_of.Doom said:**
> The easiest way to install nVidia drivers is to use Envy.

Go to your terminal, and type
```
sudo apt-get install envy
```

Now, after it's done installing, type sudo envy -t for the textual interface, or envy -g for the GTK frontend (graphical). Now, hit uninstall the nVidia drivers. This will uninstall the already existing nVidia drivers, and put the default drivers back in. Then, hit Install the nVidia drivers. And when it asks you, let it configure your xorg.conf.
That should do it.. Envy'snot in the standard repositories.

---

### Post by SPQQKY on 2007-07-19
when i type the command sudo envy -t or -g it says command not found

---

### Post by Hobo Joe on 2007-07-19
> **BlahMan_of.Doom said:**
> The easiest way to install nVidia drivers is to use Envy.

Go to your terminal, and type
```
sudo apt-get install envy
```

Now, after it's done installing, type sudo envy -t for the textual interface, or envy -g for the GTK frontend (graphical). Now, hit uninstall the nVidia drivers. This will uninstall the already existing nVidia drivers, and put the default drivers back in. Then, hit Install the nVidia drivers. And when it asks you, let it configure your xorg.conf.
That should do it..

This is by far the best way to do it, I felt the need to emphasize it considering the doubt of the OP.

---

### Post by SPQQKY on 2007-07-19
> **aysiu said:**
> And you definitely have an Nvidia graphics card?
MSI NX8600GTS. Yes, like I said, I'm not a dumby. I have been building computers for 8 years and I tried Edgy Eft a year or so ago and gave up due to this very same headache.

---

### Post by Vague on 2007-07-19
> **SPQQKY said:**
> I tried that and it says my hardware does not need any restricted drivers. That is the only thing I get.

Just out of curiosity, what card is this, specifically?  Is it on [this list?](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)

Edit: I hate to be the bearer of bad news, but I don't believe the 8600 cards are supported by the restricted driver.

---

### Post by SPQQKY on 2007-07-19
My card is not on that list. This is one of the latest releases from nVidia.

---

### Post by aysiu on 2007-07-19
Paste (do not retype--save yourself a little sanity) into the terminal: ```
wget -c http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu2_all.deb
sudo dpkg -i envy_0.9.6-0ubuntu2_all.deb
``` This will get Envy installed. I think Envy will appear in your applications menu, but, if not, the command is probably something like ```
gksudo envy
``` The Envy homepage is here, too:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Tomosaur on 2007-07-19
> **SPQQKY said:**
> MSI NX8600GTS. Yes, like I said, I'm not a dumby. I have been building computers for 8 years and I tried Edgy Eft a year or so ago and gave up due to this very same headache.

You may not be a dumby, but you are new to Linux, and you will need time to adjust. You have no idea the amount of people who come here saying stuff like 'I've used Windows all my life, and I can't even install software on Linux?!'. The problem is that Linux and Windows are two very different beasts. You had to learn Windows from scratch, and you will have to learn Linux from scratch aswell.

Envy is the easiest solution, but perhaps not the best, and considering you've tried it and it doesn't work, I can't really suggest anything new for you to try, except to manually add the resolutions you want to your /etc/X11/xorg.conf file. This is not an ideal solution, and it may not always work, but it does sometimes, and is worth a shot of there's nothing else you can do.

Good luck anyway!

---

### Post by xpod on 2007-07-19
> I tried that and it says my hardware does not need any restricted drivers. That is the only thing I get.

Go to Applications>accessories>terminal and type in
```
lspci
```

This will hopefully show you which card/chip you have?
Some older thing that dont need the accelerated drivers by the sounds of it possibly??

Once you establish what it is with the above command you should be able to get something working with this one for now, it`s mabey not a decent enough card you have though?
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Daveth on 2007-07-19
look here

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

for Envy. Works well and is well explained.

---

### Post by bodhi.zazen on 2007-07-19
> **SPQQKY said:**
> Noob to Linux, but I'm no dumby, however, it's vague instructions and complicated procedures that have kept me from Linux OS' in the past. I decided to give Ubuntu a try, but simple things like just installing my gfx card drivers with instructions like this....

<clip>

....that have kept me from using Linux. All I want to do is view the desktop in my monitors native resolution of 1680x1050 and that seems impossible at this point. 
What is the point of Linux? What does it offer that Windows can't? At this point the only thing I can see it offering is added trips to the pharmacy for headache medicine. 
Why can't I get the drivers to install. I have followed several guides and gotten tips from users from other forums only to come up empty handed.

I understand what you are saying here. My advice is that you need to answer this question for yourself, why are you running Linux ?

If, depending on how you answer that, you stay with Ubuntu you need to give yourself time to learn a new OS. Give yourself say 3-6 months, then it will not seem so foreign ;) Keep in mind you did not learn your current OS overnight either.

And as you are learning, I can think of no better community then Ubuntu.

---

### Post by aysiu on 2007-07-19
I agree with bodhi.zazen. If Linux is giving **you** headaches and Windows isn't, use Windows.

**I** don't get headaches from using Linux. Installing Nvidia drivers was as easy for me as clicking a few buttons (that tutorial I linked to--the one with the screenshots--was done on my eMachines computer, which uses an Nvidia graphics card). If it's difficult for you, you may decide it's not worth it *for you* to go through so much trouble.

---

### Post by SPQQKY on 2007-07-19
Okay, none of this works.......none of it.

---

### Post by aysiu on 2007-07-19
> **SPQQKY said:**
> Okay, none of this works.......none of it.
Okay. So ask yourself (not us) if you think it's worth it. Do you want to solve this problem, in which case there are plenty of people who would help you, or do you want to give up? If you want to give up, that's cool.

---

### Post by SPQQKY on 2007-07-19
> **xpod said:**
> Go to Applications>accessories>terminal and type in
```
lspci
```

This will hopefully show you which card/chip you have?
Some older thing that dont need the accelerated drivers by the sounds of it possibly??

Once you establish what it is with the above command you should be able to get something working with this one for now, it`s mabey not a decent enough card you have though?
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This is the latest release from nvidia. None of these work. Envy is nowhere to be found after following aysiu's advice.  Typing lspci in terminal shows unknown device for vga.

All I need is my native resolution of 1680x1050. I do not care if I can play games with Linux, I have Windows for that. I hate to give up, but I have gone through so many different options and none seem to work, advice from here and other forums. 
The whole reason for this is to learn Linux and I really have no problems anywhere else with the OS except I cannot stand the terrible resolution. My eyes are getting old.

---

### Post by aysiu on 2007-07-19
Sorry, [the Envy installation is a bit more complicated, apparently](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu) than I thought.

Here are the exact steps:

**Step 1**: [Make sure you have extra repositories enabled](http://www.psychocats.net/ubuntu/sources)

**Step 2**: Paste these commands into the terminal: ```
wget -c http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu2_all.deb
sudo dpkg -i envy_0.9.6-0ubuntu2_all.deb
``` This last command should give you a dependencies error message. Ignore it and proceed with the next command: ```
sudo apt-get -f install
sudo envy -g
``` **Step 3**: Follow the GUI wizard's prompts.

---

### Post by SPQQKY on 2007-07-19
Okay, I got envy to install. I used it to uninstall the nvidia drivers, then ran it again to install the new drivers. I now have the ability to access the driver settings, however, and this is the biggest issue of them all, I still cannot set my resolution to above 1024x768 and it further reduced my refresh rate.

---

### Post by Wiebelhaus on 2007-07-19
> **aysiu said:**
> How about using different instructions, then?
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

too shay

---

### Post by Wiebelhaus on 2007-07-19
> **SPQQKY said:**
> Okay, I got envy to install. I used it to uninstall the nvidia drivers, then ran it again to install the new drivers. I now have the ability to access the driver settings, however, and this is the biggest issue of them all, I still cannot set my resolution to above 1024x768 and it further reduced my refresh rate.




Run this in the terminal


> sudo dpkg-reconfigure xserver-xorg -p high

Select the resolutions you want with the task bar , hit tab to select ok hit enter then restart.

---

### Post by SPQQKY on 2007-07-19
:(

---

### Post by aysiu on 2007-07-19
What model is your monitor?

---

### Post by SPQQKY on 2007-07-19
> **aysiu said:**
> What model is your monitor?
Princeton 2008sw 20.1" LCD

The above command suggested by sx66gns did not work.

---

### Post by aysiu on 2007-07-19
> **SPQQKY said:**
> Princeton 2008sw 20.1" LCD

The above command suggested by sx66gns did not work.
That's weird. When I do [a Google search for that monitor](http://www.google.com/search?hl=en&q=princeton+2008sw&btnG=Google+Search), nothing comes up.

---

### Post by Frak on 2007-07-19
Try this
[http://www.psychocats.net/ubuntu/xorg](http://www.psychocats.net/ubuntu/xorg)

---

### Post by SPQQKY on 2007-07-19
Sorry, Princeton LCD2008W - it shows 2008SW in device manager under Windows.

---

### Post by pistcivet on 2007-07-19
> **SPQQKY said:**
> Princeton 2008sw 20.1" LCD

The above command suggested by sx66gns did not work.

Mistyped the command. should be:
sudo dpkg-reconfigure -phigh xserver-xorg

That will reset xorg.conf to the same values it would have after a fresh install.
But I don't know if that will help in your situation.  :(

---

### Post by SPQQKY on 2007-07-19
I get a warning about overwriting a possibly customized configuration

---

### Post by Wiebelhaus on 2007-07-19
> **pistcivet said:**
> Mistyped the command. should be:
sudo dpkg-reconfigure -phigh xserver-xorg

That will reset xorg.conf to the same values it would have after a fresh install.
But I don't know if that will help in your situation.  :(


aye , Lol - my bad.

---

### Post by BlahMan_of.Doom on 2007-07-19
Lol it's  a 30 second fix. Copy paste your /etc/X11/xorg.conf here.

---

### Post by Azoix on 2007-07-19
[IMG]http://i58.photobucket.com/albums/g261/PostHost/Screenshots/nvidia.png[/IMG]

**[FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]I don't actually have an nVidia card, but for curiosity sake, i opened synaptic, and tried nvidia as a search, it came up with 31 directly related packages, have a look through theses first, before you give up on Ubuntu totally, see if something here can fix your vid probs.[/COLOR][/SIZE][/FONT]**

---

### Post by SPQQKY on 2007-07-19
> **BlahMan_of.Doom said:**
> Lol it's  a 30 second fix. Copy paste your /etc/X11/xorg.conf here.

?????

what does that mean? Copy where?

This is so annoying, it's a very common resolution for a couple of years now for wide screen lcd's.

---

### Post by Skidpad on 2007-07-19
Paste this into a terminal: gedit /etc/X11/xorg.conf 

When the x11 file opens up, copy & paste it here.

---

### Post by SPQQKY on 2007-07-19
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
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:7:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
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
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by TheMono on 2007-07-19
Just so you understand what is going on here, because Ubuntu uses a release model where everything is updated every six months, your graphics cards, which would normally be enabled with the check of a box, is not easily enabled because it is so recent. The next version of Ubuntu, releasing October, will have the driver supporting your card built in, making all these extra processes redundant.

However, Envy forcibly installs the most recent package from Nvidia, which will work.

The xorg.conf file, found in /etc/X11/xorg.conf, is just a list of everything needed to make your graphical environment work. If you open it, with the command

gksudo gedit /etc/X11/xorg.conf

you will find that it is fairly readable. Find the bit that specifies the 'driver', which sould currently specify 'nv' as a driver, and change the 'nv' to 'nvidia'.

EDIT: looking at what you put above, you seem to already be using the nvidia driver...?

---

### Post by SPQQKY on 2007-07-19
w00t. I got it. Monitor is at native res of 1680x1050. Thank you all for your patience with me. I thought I was going to go bonkers.
This is most excellent. Thanks again. 

I'm sure I will be back with some further questions about this OS, but like I said, this was the part that drove me nuts the most. 

Cheers!\\:D/

---

### Post by Wiebelhaus on 2007-07-19
> **SPQQKY said:**
> w00t. I got it. Monitor is at native res of 1680x1050. Thank you all for your patience with me. I thought I was going to go bonkers.
This is most excellent. Thanks again. 

I'm sure I will be back with some further questions about this OS, but like I said, this was the part that drove me nuts the most. 

Cheers!\\:D/

No worries mate , this is Ubuntu.

---

### Post by Frak on 2007-07-19
> **SPQQKY said:**
> w00t. I got it. Monitor is at native res of 1680x1050. Thank you all for your patience with me. I thought I was going to go bonkers.
This is most excellent. Thanks again. 

I'm sure I will be back with some further questions about this OS, but like I said, this was the part that drove me nuts the most. 

Cheers!\\:D/
If only more users that came to the forums were as patient as you.
We usually get griped out for making a bad OS.
Good work.
Cheers.

---

### Post by Skidpad on 2007-07-19
^^^ Been a lot of that lately...

So what finally did it?   Let us know!

To help other users with the same problem, it would be a nice gesture to go back and edit your thread title to reflect your true problem (screen resolution or something like that) and then mark it resolved.  That way, other folks doing a search will know there's both a problem, and a solution for it.  You know, help out the Brotherhood...!

:)

---

### Post by Wiebelhaus on 2007-07-19
> **Skidpad said:**
> ^^^ Been a lot of that lately...

So what finally did it?   Let us know!

To help other users with the same problem, it would be a nice gesture to go back and edit your thread title to reflect your true problem (screen resolution or something like that) and then mark it resolved.  That way, other folks doing a search will know there's both a problem, and a solution for it.  You know, help out the Brotherhood...!

:)



> **pistcivet said:**
> Mistyped the command. should be:
sudo dpkg-reconfigure -phigh xserver-xorg

That will reset xorg.conf to the same values it would have after a fresh install.
But I don't know if that will help in your situation.  :(

Prolly pistcivet's eye on details , sorry I'll pay closer attention next time.

---

### Post by Skidpad on 2007-07-19
^^^^ Ahhh, gotcha.

---

### Post by aysiu on 2007-07-19
Change this section of the /etc/X11/xorg.conf file from ```
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection
``` to ```
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 31-83
VertRefresh 56-75
EndSection
``` and then save and Control-Alt-Backspace to have the changes take effect.

I'm basing that off the vertical and horizontal ranges on [the spec sheet from the Princeton Digital website](http://www.princetongraphics.com/site/download/datasheet/specsheetLCD2008W.pdf).

---

### Post by aysiu on 2007-07-19
Wow! I missed a lot.

Never mind what I said. Looks as if you got it licked. How did you do it?

---

### Post by kittyhawk63 on 2007-07-19
Edit: Same here Aysiu.

Rome wasn't built in a day. Neither was Linux. Rome is decaying while Linux is still in its building days.

As the milk cow who was stepping on her own teats said, "You think you've got problems."

I've been working at fixing my ATI video card to stop crashing since February. Patience my friend, Patience. Don't give up. The battle has merely begun. 

As the inventor once said, "You learn more by mistakes than by successes."

Albert Edison was once asked, or something to this effect, why didn't he give up on inventing the light bulb when a thousand things he had tried did not work. He replied that he now knew those things would not work and would try something else. His list of things to try which would ultimately lead to success was now shorter.

One day I hope to resolve this ATI problem. That is my goal. I am looking for an "element" that will work. My list is getting shorter.

Hang in there. Linux is worth all the little problems we encounter. It keeps improving because we won't let it get the best of us. 
kh

---

### Post by aysiu on 2007-07-19
Well, I'll be perfectly honest here--I have very little patience for things not working. If I had hardware compatibility issues (some of the things I've seen here where people have taken days to get something working) with Ubuntu, I would have given up and gone straight back to Windows.

As things turned out, I was lucky (since I didn't research on any hardware compatibility lists or buy hardware with Linux in mind).

---

### Post by SPQQKY on 2007-07-19
LOL, update manager popped up and said there were updates, so I installed them and Ubuntu will no longer boot. I get garbled text I cannot read. 
](*,)

---

### Post by Frak on 2007-07-19
Like garbled, messed up text. Or garbled, cryptic commands?

---

### Post by SPQQKY on 2007-07-19
Like stuff that doesn't look like English with red and blue and black blocks, etc.. Back on Vista for now.

---

### Post by Frak on 2007-07-19
There's absolutely no readable text? Because it sounds like your X-Server corrupted.

---

### Post by kittyhawk63 on 2007-07-19
> **SPQQKY said:**
> Like stuff that doesn't look like English with red and blue and black blocks, etc.. Back on Vista for now.

Correct this suggestion if I am off base.
Not sure this will work. Try downloading "Super Grub" iso and burn the image to CD. Boot to it and follow instructions and see if you can get back to Linux.
kh

---

### Post by bodhi.zazen on 2007-07-19
LOL

You likely downloaded a new kernel with your update and now X will not start.

One of the "joys" of the nVidia driver is you get to re-install it with each and every kernel update ;)

It is not as bad the second time around, and by the third or fourth time you can do it in your sleep.

One other "tip"

To set your resolution, once you restore X, open a terminal

Enter : ```
gksu nvidia-settings
```

You can now change your resolution and other cool stuff with a gui. When you are done, if you like your settings, click on the "Save to X Configuration File"

---

### Post by SPQQKY on 2007-07-19
I completely reinstalled Ubuntu, then I did all the updates (I remember reading that you had to reinstall the nvidia drivers last time I tried edgy eft), then I installed Envy and reinstalled the nvidia drivers. It happened again, only this time I could read the text and it said X would not start. I do not know what to do from here. I do I restore X and get the drivers functioning again with reinstalling.

I am taking a deep breath and remembering what my father used to tell me....'If it's easy to do, it's not worth doing."

---

### Post by SPQQKY on 2007-07-19
bump

---

### Post by BlahMan_of.Doom on 2007-07-19
Wait I'm not understanding. You did or did not restore X?

If X is restored, then copy paste this into your xorg.conf. If you want to add a custom resolution, replace the BLAHxBLAH with a resolution, for example, 1600x1200 or 1280x1024.

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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
BusID "PCI:7:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "BLAHxBLAH" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "BLAHxBLAH" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "BLAHxBLAH" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "BLAHxBLAH" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "BLAHxBLAH" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "BLAHxBLAH" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection
```

---

### Post by SPQQKY on 2007-07-19
I don't know how to restore X.

---

### Post by BlahMan_of.Doom on 2007-07-20
Okay. Boot into Ubuntu as you normally would, and it should say that X couldn't be started. Hit ok, and hit Yes when it asks you to give a description. If it says something about the nVidia drivers not existing, then I can definitely help. 

I hope that was clear..

---

### Post by bodhi.zazen on 2007-07-20
yes, can you give us a better error message ?

At that screen, hit the tab key, "OK" will highlight, hit enter ...

---

### Post by SPQQKY on 2007-07-20
Yeah, it says failed to load nvidia, no drivers found

---

### Post by dorath on 2007-07-20
When X dies on me I and all I have is a text-based console to play with, I have found that doing the following usually gets me my GUI back:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo pico /etc/X11/xorg.conf
```The first line makes a backup copy of your xorg.conf file.  The second line opens xorg.conf in a basic text editor.  You can use the PageUp & PageDown keys, and common commands are listed at the bottom of the screen.  Some people like nano, others will get into a flame war about VI vs emacs, just use whatever you find easy.

In your xorg.conf file, find the bit that looks like this:```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
```

Change ```
Driver          "nvidia"
```to ```
Driver          "vesa"
```
Press ctrl+x to exit, when it asks if you want to save tell it yes.

Most times this will get my back my GUI.  However, it is *really really really slow*.  Despite the slowness it will let me do useful things like surf the internets for real solutions.

That little gem right there was one of the first things I had to learn, because I've never, *ever*, had a video card / monitor combination that has 'just worked' on a fresh install.  On the plus side, it's all been downhill from there. :)

---

### Post by BlahMan_of.Doom on 2007-07-20
OK. Now that you're in recovery, there's no chance of any files in the GUI being used right? This will sound redundant, but it worked for me. When you get the error message, press CTRL+SHIFT+F1 or, just boot into recoverymode instead.

Then, login as you normally would. Afterwards, type "envy -t." Uninstall, then install. It should work fine, as Envy does not install in su mode (sometimes referred to as sudo).

su is super user, which is basically your root. sudo, means "Super User Do." Basically, it's telling the command in front of it to override everything. You don't need to override anything in this case, since nothing is being used.

So, if you didn't want to read that then:

```
$ envy -t
```
Then uninstall, then install. Reboot and it should work.

EDIT: Just Give Me The Beans! :)

---

### Post by spur on 2007-07-20
Just for fyi. I had similar probs using kubuntu 32 bit on a 64bit system. When I installed 64bit ubuntu my nvidia card no longer gave me problems. Could your problems be similar?
I think if you are forced to use 'nv' or 'vesa' you may not be able to get the resolution you want.
One thing I have found with updates is to do any linux kernal update on itd own and before a nvidia update. This seems to avoid some common problems.
Also another source for solutions is the nvidia forum. I don't have the address but it should be easy to find with google.

---

### Post by SPQQKY on 2007-07-20
> **dorath said:**
> When X dies on me I and all I have is a text-based console to play with, I have found that doing the following usually gets me my GUI back:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo pico /etc/X11/xorg.conf
```The first line makes a backup copy of your xorg.conf file.  The second line opens xorg.conf in a basic text editor.  You can use the PageUp & PageDown keys, and common commands are listed at the bottom of the screen.  Some people like nano, others will get into a flame war about VI vs emacs, just use whatever you find easy.

In your xorg.conf file, find the bit that looks like this:```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
```

Change ```
Driver          "nvidia"
```to ```
Driver          "vesa"
```
Press ctrl+x to exit, when it asks if you want to save tell it yes.

Most times this will get my back my GUI.  However, it is *really really really slow*.  Despite the slowness it will let me do useful things like surf the internets for real solutions.

That little gem right there was one of the first things I had to learn, because I've never, *ever*, had a video card / monitor combination that has 'just worked' on a fresh install.  On the plus side, it's all been downhill from there. :)

This does nothing...........

> **BlahMan_of.Doom said:**
> OK. Now that you're in recovery, there's no chance of any files in the GUI being used right? This will sound redundant, but it worked for me. When you get the error message, press CTRL+SHIFT+F1 or, just boot into recoverymode instead.

Then, login as you normally would. Afterwards, type "envy -t." Uninstall, then install. It should work fine, as Envy does not install in su mode (sometimes referred to as sudo).

su is super user, which is basically your root. sudo, means "Super User Do." Basically, it's telling the command in front of it to override everything. You don't need to override anything in this case, since nothing is being used.

So, if you didn't want to read that then:

```
$ envy -t
```
Then uninstall, then install. Reboot and it should work.

EDIT: Just Give Me The Beans! :)

............This I don't understand..............(looks for emoticon with gun in mouth).

---

### Post by SPQQKY on 2007-07-20
Okay, sorry, BlahMan_of.Doom, this was actually quite simple, I am just quite tired. Other than a dinner break and a trip to the store to buy my sons birthday gift, I have literally been at this about 12 hours just getting Ubuntu and the drivers installed. 
So this did the trick and I am back with all updates installed, drivers are installed and resolution is where it should be. Thanks for all your help. :)

Spur, I am running an AMD AM2 Opteron 1212 HE on an Asus M2N-SLI, but I could not install 7.04 for 64 bit, I don't know if my download was corrupt or what because I burned it twice on good media (Ridata and Fuji) at slow burn, but it wouldn't go. I ended up installed the 32-bit version, but all is well for now......well, except I have no sound. :(

---

### Post by spur on 2007-07-20
Try this
> sudo dpkg-reconfigure xserver-xorgif I've remembered it right it will give you a gui and ask questions one the first screen choose 'vesa' or 'nv' and click through the screens reading them and seeing if they are relevant to you. At or near the end it will give you some options for resolution and you can choose one you know is safe with your system.
Wish I could remember more but I can't and I tried to find the reference as it is somewhere in these forums but I couldn't.
Maybe someone else will be able to enlighten you further.
I'm presuming you have boot into the recovery mode.

---

### Post by SPQQKY on 2007-07-20
Well, I'm happy with 32 bit for now. I just wanted to get it up and running and I have the drivers working and I am at my monitors native resolution.

I will have to make a new post about how to get the sound to work now......but I am getting pretty tired and may wait until tomorrow. It does show my sound card (SB Audigy) but I don't have any sound play back.

---

### Post by Frak on 2007-07-20
Wait, is your card brand new?

---

### Post by SPQQKY on 2007-07-20
No, it's the original SB Audigy.

---

### Post by Frak on 2007-07-20
OK, because, a couple of months ago, Creative announced that they are stopping development of Linux drivers for new sound cards.

---

### Post by SPQQKY on 2007-07-20
Any ideas before I hit the hay? I'm really beat, but would love to have all my video and audio problems resolved. Thanks again to everyone for their help.

---

### Post by Frak on 2007-07-20
Try installing the JACK sound server instead of the default, ALSA.

---

### Post by SPQQKY on 2007-07-20
I don't see that option. I see ALSA, ADC, OSS, ESD but no Jack. Oh well, tomorrow is another day and I'll start another thread, this is getting OT from the OP.......lol. Sounds like a rap song (and I hate rap). Nighty nights.

---

### Post by BlahMan_of.Doom on 2007-07-20
Okay. I have the same exact card as you. On headphones, the sound is EXTREMELY quiet, so, you might want to try it on your speakers. In a terminal, type:

```
sudo apt-get install alsa-oss
```

Then, type alsa-mixer in the terminal, and give us a screenshot (using the Print Screen button).

---

### Post by SPQQKY on 2007-07-20
I just had to bring up alsamixer and go to analog/digital output and turn it off. Got it going now. Thanks.

---

### Post by BlahMan_of.Doom on 2007-07-20
So Ubuntu is pretty much all good to go?

---

### Post by SPQQKY on 2007-07-20
I'm happy at this point. I basically wanted to give Ubuntu another shot simply out of bordome. I like to learn new things and Windows, even Vista (which, despite a few added features) is old hat. Plus I wanted a clean OS for mostly audio and video enjoyment. I just need an app similar to Irfanview to do quick simple photo editing and I'll feel all creamy inside.

---

### Post by Frak on 2007-07-20
I fogot about the sound card problem, just found out I have the exact same card. And yes I had to plug in seperate speakers to amplify the sound more. As I usually go through the monitor. Uneeded info.
But try Picasa from Google, you can install it via [Automatix2]("http://www.getautomatix.com/")

---


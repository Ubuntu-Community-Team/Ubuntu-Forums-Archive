---
title: "New to Linux -- Major xserver problem?"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by syn` on 2007-08-12
I decided to give Linux a go and downloaded Fiesty. Never using Linux before I figured I'd try to figure it out. Upon installation I decided I was going to try to get my drivers to work. I updated as soon as the installation was done with the Ubuntu updates and then followed the guide at:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I have a Radeon 9200, by the way. Anyways, I was trying to install from the respositories. The first one didn't work for Fawn, so I followed the next. After adding the part to xorg.conf it took me to a black sceen. I then realized it was a full-screen terminal. But the resolution is so high I can't see where I'm typing, the text is massive and I don't know how to scroll down. So after finally guessing how to log in I tried the:

sudo dpkg-reconfigure -phigh xserver-xorg

command to try and just get my desktop back since I can't read anything with the resolution so big. I heard the Vesa was typically the default to pick, so I picked it off of the list and picked 1024x760 or whatever resolution. I ended up back at the terminal still logged in so I typed **startx** and it took me to a black screen so I thought. It ended up being my resolution, so I spammed enter to get down to the text and it told me:

[b](WW) VESA: No matching Device section for instance (BusID PCI:1:5:0) found
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no sceens found

XIO: fatal IO error 104 (Connection reset by peer) on X sever ":0.0" after 0 requests (0 known processed) with 0 events remaining.[/b]


I'd like to be able to get back to my desktop. I'm guessing that's what xserver is. I'd really like to get my card working, but I have to fix whatever is wrong first. Any advice would be appreciated.






By the way, my computer is a Dell Dimension 2350. It has an onboard graphics card that has always been a pain when I've installed my ATI drives on windows. Anything in DOS would show on the onboard, so basically, that was everything -before- Windows started. Once it got to the Windows loading screen the screen went black until I plugged it into my ATI card. It worked fine, no problems with performance, but that it always did. If it matters.

---

### Post by syn` on 2007-08-12
I've also tried starting in recovery mode. That fixed my resolution but I had the same problem. Once I restarted the compute and tried booting without recovery mode, the resolution was back to being huge. When I try to goto the reconfigue fo xserver-xorg, the font is so big I can't even see all my options for the drivers or resolution.

As soon as I boot my computer it also says:

**Failed to start the xsever (your graphical interface). It is likely that it is not set up correctly**

And that's about all I can see of it.

---

### Post by jeremy1138 on 2007-08-12
ATI cards are a pain!  It took a lot of fiddling to get mine to work at all and it still doesnt work right.  I can't get anything that requires 3d acceleration to work at all.  Anyway...  I had the same problem you're having not long ago.  In order to get my computer to start the gui I had to use envy to get my video card installed.  I think that if you type
```

sudo apt-get install envy

```
in a terminal you can get envy installed.  After that all you have to do is type
```

sudo envy -t

```
into the terminal and it should lead you through the process of installing your card.  I hope this helps.

---

### Post by syn` on 2007-08-12
> **jeremy1138 said:**
> ATI cards are a pain!  It took a lot of fiddling to get mine to work at all and it still doesnt work right.  I can't get anything that requires 3d acceleration to work at all.  Anyway...  I had the same problem you're having not long ago.  In order to get my computer to start the gui I had to use envy to get my video card installed.  I think that if you type
```

sudo apt-get install envy

```
in a terminal you can get envy installed.  After that all you have to do is type
```

sudo envy -t

```
into the terminal and it should lead you through the process of installing your card.  I hope this helps.

I appreciate the reply. But would it wok if I booted it in recovery mode that way I can actually read the text?

---

### Post by jeremy1138 on 2007-08-12
yes you'll need to be able to read what's going on.  I believe it will work the same in recovery mode for you.  This can all be done from a command line.

---

### Post by syn` on 2007-08-12
When I tried to get envy I got an error saying "Couldn't find package envy"

hmm.

---

### Post by jeremy1138 on 2007-08-12
hmm you may not have the correct repositories.  I'm not really sure what to do about this...  You can read about envy and download the .deb package here ( [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) ) but I'm not sure how you're going to get this into the machine that has linux running with just a command line...  I wonder if anyone else knows?  You could also try the howto located here [http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)  This is where I got envy from and where I got the howto that got my card installed properly.  I wish I could be of more help but I'm kinda new with Linux too.

---

### Post by syn` on 2007-08-12
> **jeremy1138 said:**
> hmm you may not have the correct repositories.  I'm not really sure what to do about this...  You can read about envy and download the .deb package here ( [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) ) but I'm not sure how you're going to get this into the machine that has linux running with just a command line...  I wonder if anyone else knows?  You could also try the howto located here [http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)  This is where I got envy from and where I got the howto that got my card installed properly.  I wish I could be of more help but I'm kinda new with Linux too.

I appreciate the help. 

I have just one more question, then. If I formatt the computer again (nothing on it at the moment) would I be able to get the correct repositories? Or I could probably just download it from that link, huh?

---

### Post by jeremy1138 on 2007-08-12
reformatting would fix the problem and you could, with a properly functioning gui, download envy from the address that I gave you and you should be able to get things working.  You may want to follow the instructions at that howto that I gave you first before trying envy...  Envy supposedly doesnt work all the time and it may land you in the same boat that youre in now.  Good luck!  I hope that all works out for you.

---

### Post by syn` on 2007-08-12
> **jeremy1138 said:**
> reformatting would fix the problem and you could, with a properly functioning gui, download envy from the address that I gave you and you should be able to get things working.

You've been a life saver. :P 

I appreciate the help and fast responses. Gonna fomat it real quick and see if I can get it up and running.

---

### Post by jeremy1138 on 2007-08-12
alrighty

---

### Post by syn` on 2007-08-12
I formatted and downloaded Envy. Installed it, booted it up, had it install the ATI driver only to get:

[b][color=red]Your graphic card has been detected as a ATI Radeon 9250
Your graphic card is supported by the legacy driver
ENVY ERROR: ATI's legacy driver does not support your operative system[/b][/color]

Wonderful, eh? I ended up trying the manual install and selected what I'm assuming was the newest driver out of the two. The install worked, but when I opened the terminal and tied *fglrxinfo* I got:

[b][color=red]display: :0.0 screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel (R) 845G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2[/b][/color]

So I'm guessing it didn't work, or it isn't set to use my ATI card, which I figured it should be. Now I probably have a useless ATI driver installed. Meh. When I plug the monitor into the ATI card, my monitor stays black. Boo!

---

### Post by jeremy1138 on 2007-08-12
thats super....  did you go here and try this guy's instructions to install your card? [http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)
Is Linux still booting to the graphical user interface or are you stuck with a command line again?

---

### Post by undertakingyou on 2007-08-12
I hate ATI cards,  they are such a pain.

That said, what about doing ```
 sudo apt-get install xorg-driver-fglrx
``` and when that is done ```
 sudo aticonfig --initial
```  and then you can do a ```
sudo aticonfig --overlay-type=Xv
```

After all that you do a restart.

---

### Post by jeremy1138 on 2007-08-12
did you go to system>administration>restricted drivers manager and enable your video card driver?

---

### Post by undertakingyou on 2007-08-12
jeremy1138 has a good idea too.  I would still run ```
sudo aticonfig --overlay-type=Xv
``` after it though.

Of course if you can't get a GUI that would be hard to do  . . .

---

### Post by syn` on 2007-08-12
> **jeremy1138 said:**
> did you go to system>administration>restricted drivers manager and enable your video card driver?

I just tried that and I got:

**[color=red]Your hardware does not need any restricted drivers.**[/color]

I just tried what the reply above yours said with the terminal commands. Going to try the restart now and see if that worked. But yes, I do have a GUI now after formatting.

---

### Post by syn` on 2007-08-12
After doing:

> **undertakingyou said:**
> ```
 sudo apt-get install xorg-driver-fglrx
``` and when that is done ```
 sudo aticonfig --initial
```  and then you can do a ```
sudo aticonfig --overlay-type=Xv
```

After all that you do a restart.

I'm right back where I started with the command line at a crazy resolution after I restarted.

---

### Post by jeremy1138 on 2007-08-12
ok I assume that you're using another computer to get to this forum and that you're trying to get linux working on a different machine.  go to [http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573) and follow that guys instructions to get your wireless card working.  I think you can do it all from a command line.

---

### Post by bearyblue on 2007-08-12
sadly, Radeon 9200 is not supported by the proprietary fglrx. you should install the open-source driver. i think it's xserver-xorg-video-ati. then edit your xorg.conf accordingly.

relevant part of my xorg.conf:

Section "Device"
	Identifier  "Radeon9250"
	**Driver      "ati"**
	VendorName  "ATI Technologies Inc"
	BoardName   "RV280 [Radeon 9200 PRO]"
	BusID       "PCI:1:0:0"
EndSection

---

### Post by undertakingyou on 2007-08-12
That raises two interesting questions.  Are you sure that you have an ATI card?  If the restricted driver thing didn't see it maybe you don't.  Not to fret though, when you ran those commands that I said it *should* have made some backups of your old one.  ```
 cd /etc/X11
dir
```  at this point it should show you a list of the names in that directory.  The backups should be named something like xorg.conf.backup080920070106  or something along that line.  Find the one that is before you ran "sudo aticonfig --initial" and after you have located that do ```
sudo mv xorg.conf.backup* xorg.conf
sudo gdm restart
```  of course you will need to replace the * in the above line with the date stamp so you restore the right one.
Post back questions or your results.

---

### Post by syn` on 2007-08-12
OK, the backup worked, I'm now back @ my GUI. 

Since the Radeon 9200 isn't supported by the proprietary fglrx like beary said I'm going to give the open-source a try real quick.

Thanks so much for the help so far everyone.

---

### Post by syn` on 2007-08-12
This is what I got after installing:

sudo apt-get install xserver-xorg-video-ati
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-ati is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgr

---

### Post by bearyblue on 2007-08-12
ok. then edit your xorg.conf. change driver in Section "Device" to "radeon" or "ati". then reboot.

---

### Post by undertakingyou on 2007-08-12
> **bearyblue said:**
> sadly, Radeon 9200 is not supported by the proprietary fglrx. you should install the open-source driver. i think it's xserver-xorg-video-ati. then edit your xorg.conf accordingly.

relevant part of my xorg.conf:

Section "Device"
	Identifier  "Radeon9250"
	**Driver      "ati"**
	VendorName  "ATI Technologies Inc"
	BoardName   "RV280 [Radeon 9200 PRO]"
	BusID       "PCI:1:0:0"
EndSection

I have never used this driver before so BearyBlue may be the best authority.  But you may want to edit xorg.conf the way that he has it here.  Make a backup of your current xorg.conf first.

---

### Post by bearyblue on 2007-08-12
we were just both unfortunate to have older ATI radeon cards. and ATI's fglrx doesn't support them. it was frustrating back then to follow the wiki and having a blank screen on reboot.

syn, i assume you want to get 3D working so you want to install drivers, right? to test if 3D is working, do glxgears. the gears should rotate smoothly if you have 3D working.

---

### Post by syn` on 2007-08-12
> **bearyblue said:**
> ok. then edit your xorg.conf. change driver in Section "Device" to "radeon" or "ati". then reboot.

Alright, I did that. On reboot I got stuck back @ my original problem. Command prompt with crazy resolution. I ended up having to use a backup to get back to the GUI. But here I am. Hmm. All I replaced was the ATI part, the identifier and everything I left as was. Should I of changed that? Or maybe Radeon would work?

---

### Post by syn` on 2007-08-12
> **bearyblue said:**
> we were just both unfortunate to have older ATI radeon cards. and ATI's fglrx doesn't support them. it was frustrating back then to follow the wiki and having a blank screen on reboot.

syn, i assume you want to get 3D working so you want to install drivers, right? to test if 3D is working, do glxgears. the gears should rotate smoothly if you have 3D working.

Yea. Well, I play World of Warcraft. I'm just wanting to be able to install the drivers for that sole purpose. If it wasn't for that I'd just use the default drivers I have now.

Just did the gears. To me it -looked- choppy. But it reported around 1872fps.



fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2


By the way.

---

### Post by undertakingyou on 2007-08-12
I hate to sound dumb but . . . . with the restricted drivers thing not showing the ATI card, and any edit of the xorg.conf crashing X, are we sure that we need ATI stuff?

---

### Post by undertakingyou on 2007-08-12
> **syn` said:**
> Yea. Well, I play World of Warcraft. I'm just wanting to be able to install the drivers for that sole purpose. If it wasn't for that I'd just use the default drivers I have now.

Just did the gears. To me it -looked- choppy. But it reported around 1872fps.

That should be plenty.  Mine only gets 550 - 650 fps and it works well.

---

### Post by syn` on 2007-08-12
> **undertakingyou said:**
> I hate to sound dumb but . . . . with the restricted drivers thing not showing the ATI card, and any edit of the xorg.conf crashing X, are we sure that we need ATI stuff?

The only reason I can see me needing the ATI card is for gaming purposes. I don't know if the card is somehow working and not telling me or not, tho. I've never used Linux before, so I've never had this kind of problem before. But then again if it was, it'd have to be plugged into the actual card, and it's not. It's still on my onboard.

---

### Post by bearyblue on 2007-08-12
it didn't work? sorry for the trouble. right now, you're using the default xorg.conf given to you by the Ubuntu installer? does glxgears work?

---

### Post by syn` on 2007-08-12
> **bearyblue said:**
> it didn't work? sorry for the trouble. right now, you're using the default xorg.conf given to you by the Ubuntu installer? does glxgears work?

Right now, yea, I'm using the default xorg.conf -- fresh install of Ubuntu, maybe two hours old now after the format. Glxgears worked, said it was getting 1872fps. Well, it was. Now it's around 700-800. And then it'll shoot back up. But what I'm thinking is to just format the computer again, install a fresh copy of Windows, get my driver on there and just install World of Warcraft (the only reason I **need** the driver so-to-speak). 

I'll just dual boot Ubuntu until I can figure it out in the long run or more support is offered. OR I get lucky and upgrade my stupid card to maybe nVidia or just a newer ATI :D Good idea?

---

### Post by bearyblue on 2007-08-12
Ok. Do you have your monitor connected to the Radeon card? And post your xorg.conf. If you're going to buy a new card, they say Nvidia is better supported in Linux. But of course, it's more fun trying to get an old device to work. hehe

---

### Post by undertakingyou on 2007-08-12
I'd go for nvidia,  MUCH easier than ATI 
IMHO of course.  :)

---

### Post by syn` on 2007-08-12
> **bearyblue said:**
> Ok. Do you have your monitor connected to the Radeon card? And post your xorg.conf.

No, when I plug my monitor into my Radeon card it's just a black screen. I only get a picture out of my onboard at the moment. 





```
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
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"E151FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"E151FP"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
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
```

---

### Post by bearyblue on 2007-08-12
First, do a backup. Then, replace 

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

with

Section "Device"
	Identifier	"Radeon9200"
	Driver		"radeon"
	BusID		"" wherever your Radeon is located. 
EndSection

and replace

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
...

with

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon9200"
...

Plug your monitor into the Radeon card and reboot. If this doesn't work, then I don't know what else to do.

---

### Post by plucky on 2007-08-12
Is it possible to disable the on board video on the motherboard using the BIOS?
Could be the driver update is finding the on board video and then fails as there is no monitor attached.

Hope this helps

---

### Post by syn` on 2007-08-12
First off, I'd like to thank everyone for their help. I know it took some time and I appreciate it.

After it was all said and done, anytime I went to change anything in the *xorg.conf* I ended back up at square one with the command prompt on boot with the crazy resolution. Restarting and booting up in recovery mode I was able to go back to my backup and get to my desktop.

Being as I want to use Ubuntu, but I do play games on a regular basis I reformatted yet again, this time leading with Windows. I'm going to partition it up and install Ubuntu again and just dual boot it. Windows for games as my ATI drivers work, Ubuntu for everything else as I'm completely satisfied with Ubuntu.

Hopefully I'll be able to upgrade to nVidia or at least a new ATI card that's supported by the repositories. So as for now, my problem is fixed.

Again, thanks everyone. A great way to dive into the Ubuntu community. Also learned my way around a bit this way. Problem solved.

---


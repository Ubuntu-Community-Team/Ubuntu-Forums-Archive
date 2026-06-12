---
title: "Simple duel screening help (again!)"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by cyclingman on 2008-01-03
After looking around for many days I would like to know the easiest way to connect my TV to my laptop via S-video lead. I am a begginger and have had many failed attempts using; "screens and graphics", "xrandr", and just looking at the "xorg.conf" file.

I just want the easiest method for any beginner, I don't mind whether its a copy of my primary monitor, or an extended desktop. 

the more details the better, I need is SPELT out for me (had ubuntu for about 3 weeks...only) 

Details (I am using);Latitude Dell laptop, ATI Radeon Mobility M6 LY graphics card, Gusty Gibbons. a small amount of Ubuntu knowledge. 

I apologise that this is a commons thread, but i am in desperate need of understanding and help.

---

### Post by Nano Geek on 2008-01-03
Does your TV have a S-Video in?

---

### Post by cyclingman on 2008-01-03
yes, but im using an s-video to scart cable at the moment.

---

### Post by Nano Geek on 2008-01-03
Have you looked at the graphics config. program under **System=>Administration=>Screens and Graphics** yet?
It should be fairly easy to use.
But if that doesn't work, then please write back and I'll see if I can't find something else.

---

### Post by cyclingman on 2008-01-03
Yes, thanks> I've already tried that, but the tick box to enable a "secondary screen" on screen 2 is un-tickable (grey) even when I have everything plugged in. I've heard a lot about this program not working with some graphic cards, and am sure my connection between the two is fine. Another alternative would be most great full. =)

---

### Post by Nano Geek on 2008-01-04
I'm really at a loss at this point as to what to tell you. 
The only computers that I've done something like that one were Nvidia computers and Nvidia has a nice program that will let you do stuff like that easily. 

I will keep looking and tell you if I find anything.

---

### Post by cyclingman on 2008-01-04
thanks for the effort. I know that it's something to do with the xorg.conf and that something has to be changed, i don't what im doing and thats why a nice GUI program would suit. However, if it is something simple, i could copy and paste, or attach my xorg.conf file, and some kind person would tell me what needs to be done :) 

Any infomation is welcome and (I will be) thankfull.

---

### Post by Nano Geek on 2008-01-04
Hey again,

I just found this GUI app that lets you configure an ATI card.
Just run this command and it will start up.```
sudo apt-get install fglrx-control && fireglcontrol
```

---

### Post by cyclingman on 2008-01-04
Thanks for that, but when once i downloaded it, I got the message:

"Driver does not provide the fireGL X11 extensions!
Panel components will operate only partially."

I click OK and then the "ATI Control Panel" program opens. (the message appears every time I open the program). In the program I can only see 1 tab which is "information" with no settings to change.

Do you know what the error message means, and how I can fix it?

---

### Post by Nano Geek on 2008-01-04
I think I know what the problem is there. 

First, run this:```
cat /etc/X11/xorg.conf | grep -i "fglrx"
```If it doesn't return anything, then you need to install the ATI provided graphics driver. ```
sudo apt-get install xorg-driver-fglrx
```Once that's done, just change the place in your x.org file where it says  **Driver         "ati"** to  **Driver         "fglrx"**
Reboot after that, and you should be set to use that program.

---

### Post by cyclingman on 2008-01-05
I followed your instructions but found it difficult to rename the xorg.conf file (permission was denied so i saved it to my desktop then sudo mv it back to the folder). Once I rebooted I got the message that my computer couldn't recognise the graphics card or somthing, and that it is running in low graphics mode (small screen :( )

I made a backup of the previous xorg.conf file, so I should be okay.

The first command gave me no reply, and the second one the reinstall found;

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Have I done somthing wrong? Or did it just not work?

I will try the whole process again to see if there was a mistake. Hoping for a reply!

---

### Post by cyclingman on 2008-01-05
I done it again and got the same result. Every time i change the xorg.conf file my system cannot configure the screen setting properly and starts in low graphics mode.

I've replaced the file with my backup and am using my old xorg.conf file (not low graphics mode)

Any ideas? thanks in advanced

---

### Post by cyclingman on 2008-01-06
not there? :(

---

### Post by Nano Geek on 2008-01-06
Sorry I'm here. Sorry about that.
The internet connection went out here yesterday and I've been busy today and I'm still working.
I'll try to get back in not to long.

---

### Post by cyclingman on 2008-01-07
Although i don't know much about what im doing, I'm gonna give this a try,

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

 and then try the glfire program thingy. Im gonna make a backup of my xorg.conf file just incase. Ill give you the feedback, I might be going in the complete wrong direction, (a learning curve)

---

### Post by cyclingman on 2008-01-07
didn't work

---

### Post by Nano Geek on 2008-01-07
I am again very sorry that it has taken me so long to respond here. School has started again and I haven't had much time. 

Have you tried reconfiguring your xorg yet?```
sudo dpkg-reconfigure xserver-xorg
```There's always a chance that it might work.

---

### Post by cyclingman on 2008-01-08
Yes, I've done it before after I messed up my xorg.conf file. I've just followed the instructions and have always chosen the easy option. I don't understand what this is achieving? Is this to get the fireglcontrol program working? Or is there something in the steps?

Just some explanation on the current situation (and what i have to do) 

thanks.

---

### Post by Jense on 2008-01-08
Hi,
I am not sure about the Radeon M6, but I think it is older than the Mobility 7500, which I am using. Things is, the Chipset on grafic boards older than some model with 8000 in it is not supported by the binary driver provided by ati and never will be since they suck. I have however succesfully configured mine for dual screen using the radeon driver provided by the ubuntu repositories (I think). I don't know the xrandr commands to use the s-video output, but I am attaching my xorg.conf so you can see how I configured it. ahh, not attaching because it doesn't work for some reason. So here are the relevant parts:

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"radeon"
	BusID		"PCI:01:00:0"
	Option 		"RenderAccel" "true"
	Option		"AGPMode" "4"
	Option 		"AGPFastWrite" "true"
	Option 		"EnablePageFlip" "true"
	Option		"AGPSize"	"32" #fixes white title bars
	Option		"DRI" "true"
#	Option		"AccelMethod" "EXA"
#	Option		"XAANoOffscreenPixmaps"
# use bios hot keys on thinkpad (aka fn+f7)
        Option          "BIOSHotkeys" "on"
# enable radeon specific xinerama
        Option          "MergedFB" "true"
        Option          "CRT2Position" "RightOf"
#        Option          "CRT2Hsync" "50-75"
#        Option          "CRT2VRefresh" "30-82"
        Option          "MetaModes" "1024x768-1280x1024"
        Option          "MergedNonRectangular" "true"
       

EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes		"1024x768"
		Virtual 	2304 1024
	EndSubSection

EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	Option		"AIGLX"	"true"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

# Section "Extensions"
# 	Option  "Composite" "Enable"
# EndSection


Don't just cp it into your file, because there are some parts you will have to change depending on your computer specs. For example does it support 4x AGP? Make a backup of the original in case it doesn't work
Here are some further links I used to configure this:

[http://ubuntuforums.org/archive/index.php/t-581947.html](http://ubuntuforums.org/archive/index.php/t-581947.html)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

[http://www.thinkwiki.org/wiki/Additional_options_for_the_radeon_driver](http://www.thinkwiki.org/wiki/Additional_options_for_the_radeon_driver)

hope this helps

---

### Post by cyclingman on 2008-01-08
Thanks for that. Im having many issues, my file is obviously quite different, ut obviously with some similarities, and since i have very little knowledge about what I'm doing, I have and endless amount of this to guess and change. These are my equivalent parts of the file, to see the different. If you, or anyone else might be able to suggest what i should change :(:

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
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
	InputDevice	"Synaptics Touchpad"
EndSection



P.S I am currently using: sudo nano /etc/X11/xorg.conf  to edit the file, is this the best way (it's the only way I know that works)

Any help is welcome!

---

### Post by Jense on 2008-01-08
Nano is good, though it is up to you really, depends on what you like. I use gedit, which is more like a texteditor and a bit more comfortable if you are used to work with textprogramms. (sudo apt-get gedit).
So I am rather new to linux myself, so no idea if this will work, but you can try cp this into your xorg.conf. I commented and inserted some things. Then find out the commands to use with xrandr to enable svideo output. Make sure that the ## are allways in front of a comment, otherwise X11 will execute it as command and give out an error

Section "Device"
Identifier "ATI Technologies Inc Radeon Mobility M6 LY"
## change to use radeon driver
Driver "radeon"
BusID "PCI:1:0:0"
Option "UseFBDev" "true"
## some options to allow for non rectangular desktops and other stuff, I don't understand all of it but it works for me
# enable radeon specific xinerama
        Option          "MergedFB" "true"
        Option          "CRT2Position" "RightOf"
#        Option          "CRT2Hsync" "50-75"
#        Option          "CRT2VRefresh" "30-82"
        Option          "MetaModes" "1024x768-1280x1024"
        Option          "MergedNonRectangular" "true"

## For these find out if your grafics do support them:

#	Option 		"RenderAccel" "true"
#	Option		"AGPMode" "4"
#	Option 		"AGPFastWrite" "true"
#	Option 		"EnablePageFlip" "true"
#	Option		"AGPSize"	"32" #fixes white title bars
#	Option		"DRI" "true"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon Mobility M6 LY"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Modes "1024x768"
## include virtual screen to enable large desktop with xrandr i.e 2304x1024 means    ## 1024+1280 x 1024 so one desktop with the given number of pixels
Virtual 	2304 1024
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

---

### Post by cyclingman on 2008-01-08
I done all the changes that you instructed (including the ## ones) without checking weather they work on my graphics card (I don't know how to check) and then i restarted X and all was well.

However, I didn't know what to do from that point, it's all becoming a bit complicated and overwhelming - i loaded up fireglcontrol with the same error. I then ask xandr and tried the commands to enabled, and it said that they were disconnected (as before) and then I went into screens and graphics and unlike before, the "secondary screen" and "Extend default screen" were checked. 

HOWEVER, I still couldn't see an image, so i unticked it. Rebooted, ticked it, restarted X, then it all went into low-graphics mode again >_<

I'm getting really annoyed with what happening, and my lack of understanding. I've had to go back to my old xorg file (back were i started) again. Has ANYONE got any ideas?

---

### Post by Nano Geek on 2008-01-08
I'm afraid that I don't have any more suggestions for you. 
I was able to do something similar to that with my laptop and a LCD monitor, but that was with a Nvidia graphics-card and Nvidia's config tool worked great. I'm sorry that I put you through all of that and didn't find the solution, but I just don't know anything else to try.

---

### Post by cyclingman on 2008-01-08
Don't worry. Thanks alot for you help, and the time put in. It wasn't a total loss, I learnt a bit. I'll live without it for awhile and come back with a fresh mind some other time, mabey with new programs/better knowledge/upgrades. :guitar:

I'll occasionally check back, any suggestion by anyone, and I'll be great full.

---

### Post by Nano Geek on 2008-01-08
Sure, I'll keep looking for a solution.
Thanks for understanding.

---

### Post by Nano Geek on 2008-01-08
Actually, I'm not sure if this will help, but this looks like it might be what you're looking for. 
I hope it works.

[http://hobbylobby.wordpress.com/2007/09/08/dual-monitors-in-ubuntu-xorgconf-driver-ati-card/#comment-1265](http://hobbylobby.wordpress.com/2007/09/08/dual-monitors-in-ubuntu-xorgconf-driver-ati-card/#comment-1265)

---

### Post by Jense on 2008-01-08
I haven't made good experiences with tweaking the xorg.conf manually and also using the grafical configuration interface. It screwed up my grafics every time. The xorg.conf I gave you should do give you the prequisites for using two different screens. But I use a LCD as well for the second screen. So if xrandr doesn't give you anything when you connect the svideo i am not sure your grafics are supported by the driver. Sorry, no further idea. It took me quite a while to get it working the way I have it now, also letting it rest for a couple of weaks an then searching again. So take it slowly if thats better for you.
Sorry I couldn't help

---

### Post by Jense on 2008-01-08
post what it says if you just type in 

xrandr

---

### Post by Nano Geek on 2008-01-08
And just for the record, X.org 7.3, which will be in Hardy this April, is said to have much better support of plug-and-play monitors.

---

### Post by cyclingman on 2008-01-09
Here is the reply (i havn't plugged the cable in, do i need to? :S)

_______________________________________________________________________

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2304 x 1024
VGA-0 disconnected (normal left inverted right)
DVI-0 disconnected (normal left inverted right)
LVDS connected 1024x768+0+0 (normal left inverted right) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right)
________________________________________________________________________

Sounds good, I don't mind waiting till april ,-)

Haven't tried that link, but I will do soon, and tell you what came out. Sorry for the late reply :(

---

### Post by Nano Geek on 2008-01-09
No problem.
I hope everything works out for you.

And if you don't want to wait until April and you feel adventures, you could try downloading and installing the X.org 7.3 packages manually from [here.]("http://packages.ubuntu.com/hardy/x11/xorg") 
But I haven't heard if that works and for all I know it could trash your system and force you to reinstall. So be warned. :)

---

### Post by cyclingman on 2008-01-12
Thanks, but I'll give it a miss. I had a look %:

---

### Post by cyclingman on 2008-03-20
just came for a checkup ... 3 months later, I have at least one expectation for the hardy release (it's not far away)

---

### Post by Nano Geek on 2008-03-22
> **cyclingman said:**
> just came for a checkup ... 3 months later, I have at least one expectation for the hardy release (it's not far away)If I were you, I'd try Hardy now. I've been running it for quite a while, and I haven't had a problem. It has been very stable for me. 

Anyway, good luck!

---

### Post by cyclingman on 2008-05-29
Returning to this post ...

Hardy is here, and i was eager to try out its "good" duel screening compatibilities. So first of all, I looked for "screens and graphics", and couldn't find it. But then saw that it had to be enabled using edit menus.

So I tried it, and got more or less the same response as before (screen settings where all messed up :( ) But this time it fixed it without me having to back it up.

That didn't work, so I tried installing the "ATI catalyst control center" software, and got the same response as before (error message when trying to start the program), except this time, it doesn't even start at all :(

Has ANYONE got ANY clue on how to solve my problem???


Thanks in advanced!!!

---


---
title: "nvidia RIVA TNT2 driver"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by GrantShoe on 2007-03-04
I have kubuntu installed and my next step here is upgrading the display driver.  I did this in the past with OpenSUSE and it took me 3 days to fix x.org (i'm new...)

So here i am in kubuntu, i searched adept and found nvidia legacy drivers (nvidia-glx-legacy) and i installed that.  it was amazingly easy! i just installed it and Poof! no errors! but i don't see any difference.  at all.  i can't get above 800x600 and when i had windows xp on this computer i had 1200x900 or something like that.

are there any other places that i could get drivers for this or maybe is there something that i'm not doing right?

---

### Post by Patrick K on 2007-03-04
Did you try the nvidia applet? Not sure where it is in KDE but in Gnome it is in Applications>System Tools.

---

### Post by GrantShoe on 2007-03-05
i see that i can go from the nv standard to the nvidia proprietary driver... should i do that?


also, i can't find the nvidia applet

---

### Post by chuckyp on 2007-03-05
For the tnt2 cards if you are looking for the binary driver you need to isntall nvidia-glx-legacy from either synaptic or aptitude.

---

### Post by GrantShoe on 2007-03-05
i got the legacy drivers installed using adept... i'm not really sure what aptitude is

---

### Post by tubasoldier on 2007-03-05
yes, you should use nvidia instead of the nv driver. and you may need to edit the xorg file to allow the resolution that you are looking for. Look at the bottom of the file at the list of resolutions.

---

### Post by GrantShoe on 2007-03-05
you're gonna have to talk me through that somewhat.  i set the proprietary driver and restarted and it brought me down to 640x480...

i'm not sure how to edit the xorg file or where to find it or what list you're talking about.  i'm trying to search for help that's already been typed up but i don't even know what i'm searching for

---

### Post by HasratUSA on 2007-03-05
> **GrantShoe said:**
> I have kubuntu installed and my next step here is upgrading the display driver.  I did this in the past with OpenSUSE and it took me 3 days to fix x.org (i'm new...)

So here i am in kubuntu, i searched adept and found nvidia legacy drivers (nvidia-glx-legacy) and i installed that.  it was amazingly easy! i just installed it and Poof! no errors! but i don't see any difference.  at all.  i can't get above 800x600 and when i had windows xp on this computer i had 1200x900 or something like that.

are there any other places that i could get drivers for this or maybe is there something that i'm not doing right?

If you want to download, install the drivers and configure your Xserver manually,  which may or may not take you 4-5 days depending on your experience and common sense, you're welcome to do so. Go ahead, visit Nvidia's official site and download their closed-source driver for your Riva TNT2. Make sure you do get the correct driver file for the appropriate card.

Another very safe, fast, reliable but unmanly way of doing the same thing is to download and run Envy, a command-line based application written in Python by Alberto Milone to make it easy for newbies and the impatience to install the most appropriate/exact driver files (closed-source, of course) from the vendors' site. Remember that currently Envy supports only two vendors: 1. nVIDIA and 2. ATI.

Download the latest stable version of Envy: [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb)

Log out and press CTRL+ALT+F1

Log in again

Type envy and hit enter

Simply follow the onscreen instructions.

(Resolved)

---

### Post by tubasoldier on 2007-03-05
It would only take 4-5 days if your a complete retard - noob or not.

Back up your xorg file before you start anything!
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
```

Where it says:
Section "Device"
      Driver      "nvidia"

At the bottom of that file you will see 
Section "Screen"
      Modes "1200x900"

add "1200x900" to each of the modes and SAVE the file.

Press "ctl + alt + backspace" to restart your xserver. 

If you get no gui then login and do the following:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
This will replace the file you saved with the backup!

---

### Post by GrantShoe on 2007-03-05
> **HasratUSA said:**
> If you want to download, install the drivers and configure your Xserver manually,  which may or may not take you 4-5 days depending on your experience and common sense, you're welcome to do so. Go ahead, visit Nvidia's official site and download their closed-source driver for your Riva TNT2. Make sure you do get the correct driver file for the appropriate card.

Another very safe, fast, reliable but unmanly way of doing the same thing is to download and run Envy, a command-line based application written in Python by Alberto Milone to make it easy for newbies and the impatience to install the most appropriate/exact driver files (closed-source, of course) from the vendors' site. Remember that currently Envy supports only two vendors: 1. nVIDIA and 2. ATI.

Download the latest stable version of Envy: [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb)

Log out and press CTRL+ALT+F1

Log in again

Type envy and hit enter

Simply follow the onscreen instructions.

(Resolved)

did it.  and i'm still at the 640x480 resolution.  its pretty bad now because sometimes i can't get to an "APPLY" thing.  i one time read something about hitting shift and then moving the application that's open so that you can get to the bottom of the box but it's not shift... i'm not sure what it is.

i like how you say that it's not manly... at this point, i don't want to touch xorg after the crap that i've been through it so i'll take the most womanly way possible!


> **tubasoldier said:**
> It would only take 4-5 days if your a complete retard - noob or not.

Back up your xorg file before you start anything!
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
```

Where it says:
Section "Device"
      Driver      "nvidia"

At the bottom of that file you will see 
Section "Screen"
      Modes "1200x900"

add "1200x900" to each of the modes and SAVE the file.

Press "ctl + alt + backspace" to restart your xserver. 

If you get no gui then login and do the following:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
This will replace the file you saved with the backup!

it took that long because of frustration + school work + job work so i only was able to play around with it for an hour or two every night... if that.
I promise i'm not a retard.  just a really busy new linux user who is trying to take advantage of spring break to get through some of the major hurdles that i've had in the past.

when i did this, it's not letting me gedit it... isn't there something called vm or vim that i can edit with in terminal?

---

### Post by GrantShoe on 2007-03-05
so how about this... i went to the directory... /etc/X11 and by now there is xorg.conf, xorg.conf.1, xorg.conf.2, xorg.conf3, xorg.conf.backup, xorg.conf_backup_200703050105 and some other random files...

so i opened them and looked at the screen part that tubasoldier talked about and xorg.conf.1 has a nice listing of about 4 different resolutions that i remember from back in the xp days of this desktop.

how do i replace xorg.conf with this xorg.conf.1?  i think this SHOULD be the correct file... heh... hopefully.  if not, that's what backups are for, right?

---

### Post by tubasoldier on 2007-03-05
Sounds good to me.

It sounds like you have been working on it a while. and sorry that i inferred you were of a lower intelligence. I just dont think the automatic scripts always work well.

I would replace that xorg.conf file with the xorg.conf1 file. 
```
sudo cp /etc/X11/xorg.conf1 /etc/X11/xorg.conf
```
Also, since you are not very familiar with linux, vim would confuse you more. I'm still confused with vim and I work in the terminal a lot.  nano would be a better choice for a new user. It has all the commands you need to know at the bottom of the screen while you are using it.

Once you have that file replaced then make sure you have the "nvidia" driver in that file instead of the "nv" driver.

---

### Post by GrantShoe on 2007-03-05
> **tubasoldier said:**
> Sounds good to me.

It sounds like you have been working on it a while. and sorry that i inferred you were of a lower intelligence. I just dont think the automatic scripts always work well.

I would replace that xorg.conf file with the xorg.conf1 file. 
```
sudo cp /etc/X11/xorg.conf1 /etc/X11/xorg.conf
```
Also, since you are not very familiar with linux, vim would confuse you more. I'm still confused with vim and I work in the terminal a lot.  nano would be a better choice for a new user. It has all the commands you need to know at the bottom of the screen while you are using it.

Once you have that file replaced then make sure you have the "nvidia" driver in that file instead of the "nv" driver.

no need to apologize lets just see if we can tackle this thing.  I did just that, i copied the xorg.conf.1 file over and restarted xserver or whatever its called.  i'm back to 800x600 and no higher.  i went to the monitor and display settings and now it's not letting me change the Driver between Standard and Proprietary so now its stuck on nv.  BUT i can change the Graphics card so instead of THAT saying nv, it'll say 'RIVA TNT2'

so now when i'm in the hardware tab of the Monitor & Display - System Settings, it says
RIVA TNT2
Graphics card: RIVA TNT2
Driver: nv

Monitor: Plug 'n' Play


is this correct?

---

### Post by GrantShoe on 2007-03-05
> **GrantShoe said:**
> no need to apologize lets just see if we can tackle this thing.  I did just that, i copied the xorg.conf.1 file over and restarted xserver or whatever its called.  i'm back to 800x600 and no higher.  i went to the monitor and display settings and now it's not letting me change the Driver between Standard and Proprietary so now its stuck on nv.  BUT i can change the Graphics card so instead of THAT saying nv, it'll say 'RIVA TNT2'

so now when i'm in the hardware tab of the Monitor & Display - System Settings, it says
RIVA TNT2
Graphics card: RIVA TNT2
Driver: nv

Monitor: Plug 'n' Play


is this correct?

haha sorry for double posting so much... i'm not being patient with this tonight... i answered my own question.  it isn't correct.  i hit "TEST" and now i'm face with a screen of... it looks like chain mail and my cursor is a big black X

anyway of fixing this?

---

### Post by tubasoldier on 2007-03-05
sounds right. I'm not actually using gnome so I'm not in the same gui config tools you are. 

I would go back to my post about editing the xorg.conf file. replace the "nv" with "nvidia" and then make sure your resoluiton that you know you can get is in the file at the bottom.  

you can use gedit or nano. if you use nano then replace all the gedit commands with nano.

good luck

---

### Post by GrantShoe on 2007-03-05
i'm still kinda lost here.  does anyone with a fresh pair of eyes have any ideas?  right now my situation is:
[[IMG]http://img182.imageshack.us/img182/5343/snapshot1ou5.png[/IMG]](http://imageshack.us)
[[IMG]http://img241.imageshack.us/img241/6641/snapshot2kx1.png[/IMG]](http://imageshack.us)
[[IMG]http://img510.imageshack.us/img510/5111/snapshot3ii1.png[/IMG]](http://imageshack.us)

and my current xorg.conf file:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Radius"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"Radius"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```


so as you can see, i'm only getting 640x480 or 800x600 as my options to change the resolution but the configuration file has 4 different resolutions listed.  i'm not really sure what tuba soldier meant by nv/nvidia.

**edit:** sorry for the huge files, i meant to only copy the thumbnails...

---

### Post by jvc26 on 2007-03-05
> **tubasoldier said:**
> It would only take 4-5 days if your a complete retard - noob or not.

This guy is new to Ubuntu - give him a break that comment wasnt really necessary was it, its not exactly intuitive if you're really new and have other things to do other than to try and sort out a new OS.
Il

---

### Post by maniacmusician on 2007-03-05
hey GrantShoe,

editing xorg.conf is not that hard once you understand the basic concept of it; I'll try to explain that here. 

In the xorg.conf, there are two sections that are critical to your video experience; the Device section and the Screen section. The Device section specifies your card and what driver to use for it. So, right now, your Device section says:

> Section "Device"
	Identifier	"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
EndSection

nv is the open-source driver that apparently doesn't support your card well. You want the **proprietary driver** that you installed from the repositories. In that case, this is what we want it to say:
> Section "Device"
	Identifier	"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"**nvidia**"
	BusID		"PCI:2:0:0"
EndSection


So, open that file with root permissions (kdesu kate /etc/X11/xorg.conf) and change the nv to nvidia.

The Screen section controls what resolutions you can use. Here's a typical "Mode" line:
> Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
That specifies resolutions that you can use. It will try them in the order that you list them, and it will use the highest that it can support. So right now, it's set to try 1024x768, then the next one, etc. To add higher resolutions, simply add them in front of the 1024x768. For instance, if you want 1280x1024, and your card supports that, you add this:
> Modes		**"1280x1024"** "1024x768" "832x624" "800x600" "720x400" "640x480"

and that's it. After you do that, press Ctrl + Alt + Backspace to restart your X server, and if the drivers are installed right, you should get a good resolution

edit: I'll add a little more info about permissions. In Linux, certain files that affect your entire system have high-level permissions that only superusers can access. To get to those files, you have to give yourself "root"(admin) permissions. You typically do this by adding the command "sudo" in front of your normal command. However, when accessing **graphical applications** with superuser permissions, you have to use graphical sudo; In KDE, this is "kdesu" and in Gnome, it's "gksudo" or "gksu." This is why the command I gave you to open this file had "kdesu" in front of it.

If you have any questions, just ask.

---

### Post by GrantShoe on 2007-03-05
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


editing it with that command

kdesu... etc...

and then changing nv to nvidia worked!!

I guess that's what tubasoldier was saying but i didn't really understand what he was talking about. 

i now have 1024x768.  i think i was wrong when i said something about 1200x900 but i knew that i've viewed before was a heck of a lot bigger than 800x600

oh my, you guys are lifesavers.

wow.

ok, i need to play around some more.

next stop, getting access to my Network attached storage drive and my windows shared off of the network... here goes nothing!

thanks guys!

---

### Post by maniacmusician on 2007-03-05
It's no problem :) you can try some higher resolutions too, to see how much you can get out of it. since it's an nvidia card, it may be able to pump out more than 1024x768.

I hope you actually learned this process instead of just following instructions. It's better to actually learn what you're doing so that you get more experienced and get more skilled at doing stuff.

---

### Post by GrantShoe on 2007-03-05
> **maniacmusician said:**
> It's no problem :) you can try some higher resolutions too, to see how much you can get out of it. since it's an nvidia card, it may be able to pump out more than 1024x768.

I hope you actually learned this process instead of just following instructions. It's better to actually learn what you're doing so that you get more experienced and get more skilled at doing stuff.

I definitely have.  I think for the most part, i'm getting more accustomed to editing things that in the past i haven't tried to touch (xorg.conf).  I think that's the windows user in me where i've edited the wrong file one too many times.

In the past, linux has been a pain but now i'm having fun.  thanks for your help :)

---

### Post by maniacmusician on 2007-03-05
> **GrantShoe said:**
> I definitely have.  I think for the most part, i'm getting more accustomed to editing things that in the past i haven't tried to touch (xorg.conf).  I think that's the windows user in me where i've edited the wrong file one too many times.

In the past, linux has been a pain but now i'm having fun.  thanks for your help :)
excellent :) proves my theory that the biggest thing most new linux users lack is true education. [yawn] I'll fix that once I finish writing my book

---

### Post by HasratUSA on 2007-03-05
> **maniacmusician said:**
> excellent :) proves my theory that the biggest thing most new linux users lack is true education. [yawn] I'll fix that once I finish writing my book

Maniac Musician, you're my hero! The community should be thankful to God that teachers like you are still contributing. Your write-up about xorg.conf taught me some important lessons and is about to help me fix a little problem that I confront everytime I restart the computer.

I'm glad that I never ecountered a problem similar to that of GrantShoe. I don't have anything to complain against how GNU/Linux is treating my monitor and the nVIDIA graphics card.

The current and maximum  resolution, as I have set it in the control panel, is 1280X1024. The control panel does allow me to switch to a lower one, but never more than 1280X1024, nor do I need to select anything more than that.

So, therefore, you should ask: "What's the freaking problem?"

The problem is that if I restart the PC right now, the resolution Ubuntu will automatically switch to is 1152x864, not 1280X1024, unfortunately. But fortunately I would then launch the KDE control panel again set it back to my favourite (and desired) 1280X1024.

It's not that I restart my PC too often.

After reading your posts, I had a look at the xorg.conf file and I pray and hope you wouldn't be annoyed if I copy and paste a little bit of information from that file. Here it goes:

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 57.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1152x864" "1024x768" "800x600" "720x400" "640x480" "248x248"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1152x864" "1024x768" "800x600" "720x400" "640x480" "248x248"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1152x864" "1024x768" "800x600" "720x400" "640x480" "248x248"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1152x864" "1024x768" "800x600" "720x400" "640x480" "248x248"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1152x864" "1024x768" "800x600" "720x400" "640x480" "248x248"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1152x864" "1024x768" "800x600" "720x400" "640x480" "248x248"
    EndSubSection
EndSection

I truly believe that I would have to add "1280x1024" right before every single "1152X864"s to fix the problem in question, right? I just want to make sure that performing the change in the xorg.conf file I'm about to make after reading your posts would be safe.

P.S. Let me restate that I am able to change the resolultion from 1152X864 to 1280X1024 after restarting by going to KDE's control panel and selecting 1280X1024 from the drop-down menu, whereas GrantShoe wasn't able to choose his/her desired resolution at all. That's the difference. I hope my explanation is precise enough for you. Good luck with your book! :)

---

### Post by maniacmusician on 2007-03-05
Thanks for the luck, I shall surely need it.

Yes, you are correct, all you have to do is add "1280x1024" to the line in front of "1152x864." 

However,  you needn't do it for every line. If you have a modern graphics card, you only need to do it for the line beneath "Depth 24", as all relatively new cards can handle 24-bit graphics. If you have a very old card, you may be using 16-bit instead, but that's unlikely; that's mostly just on old laptops and stuff. So at the most, you only have to change the lines for 16-bit and 24-bit.

Good luck with your problem. I'm sure this will fix it.

PS: A cool little hint; you can also specify your desired refresh rate in this line. Suppose you want a refresh rate of 70, and the computer doesn't give this to you by default.  Assuming that your card and monitor can handle it, you can write "1280x1024_70", and the X server will try to achieve that  rate. The bad news is, that if it **doesn't** support the refresh rate that you specify, it will disregard that entry and move on to the next one. So if your computer or monitor can't handle 1280x1024 at a refresh rate of 70, it'll skip that resolution and go to "1280x1024". So you just have to make sure that you enter a supported refresh rate there.

edit: I noticed that you're using the proprietary nvidia driver.  Since you use that driver, you can check your refresh rate with this command: nvidia-settings -q all | grep RefreshRate

---

### Post by GrantShoe on 2007-03-06
maniacmusician - you said that i may be able to pump more power and resolution out of my card.  i tried changing the xorg file and i have it like this...
> Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"Radius"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

but when i look at my Monitor & Display settings, i can still only go up to 1024x768

1024x768 is a great improvement from 800x600 so i'm not really complaining but the more i deal with this, the more i see how i'd prefer a higher resolution.   Did i edit this correctly?  I added the two resolutions because i wasn't sure if either would work.

---

### Post by maniacmusician on 2007-03-06
Yes, it seems to be correct.

After editing, did you restart X? (Ctrl + Alt + Backspace) The X server (the thing that draws the windows on your screen) needs to restart to apply the changes from xorg.conf. 

If you rebooted, that should've done the trick. If you still can't go any higher after a reboot/restart of X, then your card probably can't do any better.

---

### Post by GrantShoe on 2007-03-06
yeah i've rebooted... 

ok, that's too bad

---

### Post by HasratUSA on 2007-03-06
It seems like the card Riva TNT2 is a very old one and most probably nVIDIA has stopped providing support for it. I went to nVIDIA's official site and didn't find any manual and driver. For all its worth, I believe 1028X1024 mode isn't supported and given your card's capability and age, the lower the resolution, the merrier!

However, you're always encouraged to continue experimenting with it since the information I provided above may not be accurate.

---

### Post by maniacmusician on 2007-03-06
if you can get more out of that card in Windows, you probably can in Linux as well. 

for instance, I did a bit of a search, and this thread came up ([http://www.ubuntuforums.org/showthread.php?t=365388&highlight=nvidia+RIVA+TNT2](http://www.ubuntuforums.org/showthread.php?t=365388&highlight=nvidia+RIVA+TNT2) ) That person mentions that they installed newer drivers using the Envy script ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) ) and was able to run Beryl...so I should think that  you'd be able to get a higer resolution as well.  so you can try updating the drivers that way.

I'm not really an expert on video cards, but if you do a little research on your particular model and ask around, you may be able to get  it to work better.

edit: just out of curiosity, what resolution does that card give you in Windows?

---

### Post by HasratUSA on 2007-03-06
> **maniacmusician said:**
> if you can get more out of that card in Windows, you probably can in Linux as well. 

for instance, I did a bit of a search, and this thread came up ([http://www.ubuntuforums.org/showthread.php?t=365388&highlight=nvidia+RIVA+TNT2](http://www.ubuntuforums.org/showthread.php?t=365388&highlight=nvidia+RIVA+TNT2) ) That person mentions that they installed newer drivers using the Envy script ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) ) and was able to run Beryl...so I should think that  you'd be able to get a higer resolution as well.  so you can try updating the drivers that way.

I'm not really an expert on video cards, but if you do a little research on your particular model and ask around, you may be able to get  it to work better.

edit: just out of curiosity, what resolution does that card give you in Windows?

If you go back to GrantShoe's very first post, you would notice that in windows XP he was able to set the resolution to as far as 1200X900, according to what he said previously. If it is the maximum resolution mode he was able to achieve in XP, then I don't understand why he wishes to go higher than that in GNU/Linux and also how it would be possible to go any higher . 

It may also lead us to come to the conclusion that his video card Riva TNT2 doesn't support a resolution higher than 1200X900, by analyzing some of his statements in one of his previous posts that he was able to go as far as 1200X900 in XP, Feel free to correct me if I'm wrong.

Another interesting matter to notice is that he already installed and ran the famous Envy script after I directed him to do so. Unfortunately it backfired and it's likely that a little bit of damage took place since after installing and running Envy, he was unable to click the 'apply' button in nVIDIA settings control applet to apply the changes to the configuration. The outcome of his running Envy was that the script wasn't able to solve GrantShoe's problems and he wasn't able to select a resolution higher than 600X800.

I observed that any information regarding exactly which version of Kubuntu (Whory, Breezy, Dapper or Edgy? 32 or 64 bit?) was never provided in any of his posts.

---

### Post by maniacmusician on 2007-03-06
Not to be nitpicky, but it's Hoary, not Whory :)

And [oops] I haven't read the earliest pages. If he can get 1200x900 in XP, then he should be able to get it in Linux as well. At the moment,  he can only get 1280x1024.


GrantShoe: Try putting 1200x900 as the first option in your Modes line. That may be the maximum for your card.

---

### Post by HasratUSA on 2007-03-06
Sorry I'm new and these names are confusing me :lolflag:

---

### Post by GrantShoe on 2007-03-07
> **HasratUSA said:**
> If you go back to GrantShoe's very first post, you would notice that in windows XP he was able to set the resolution to as far as 1200X900, according to what he said previously. If it is the maximum resolution mode he was able to achieve in XP, then I don't understand why he wishes to go higher than that in GNU/Linux and also how it would be possible to go any higher . 

It may also lead us to come to the conclusion that his video card Riva TNT2 doesn't support a resolution higher than 1200X900, by analyzing some of his statements in one of his previous posts that he was able to go as far as 1200X900 in XP, Feel free to correct me if I'm wrong.

Another interesting matter to notice is that he already installed and ran the famous Envy script after I directed him to do so. Unfortunately it backfired and it's likely that a little bit of damage took place since after installing and running Envy, he was unable to click the 'apply' button in nVIDIA settings control applet to apply the changes to the configuration. The outcome of his running Envy was that the script wasn't able to solve GrantShoe's problems and he wasn't able to select a resolution higher than 600X800.

I observed that any information regarding exactly which version of Kubuntu (Whory, Breezy, Dapper or Edgy? 32 or 64 bit?) was never provided in any of his posts.

1200x900 was just a random number i made up.  i knew that i was in the 1000s and i did quick math to get from 800x600 to something higher with similar dimensions.  I don't know exactly what i got in xp because it's been about a year now since this computer has had xp (and it's been about a year since it's had any use really...) 

i'm thinking of trying that envy again.  not tonight because i have to studyup some more and when i get involved with this, i don't wanna put it down.  and rightly so because i'd forget what i was doing if i dropped it in the middle.  I'll probably give this a try tomorrow some time or maybe later this week depending on when i can put a good amount of time off for this.

in the meantime, i'm trying to get an 802.1x client working on here as well as mounting a network drive with something like 200 gigs of music and video and that's all not going smoothly so now that i have a workable resolution i don't want to... mess it up(?)

i'm running kubuntu 6.10 32bit.

---

### Post by GrantShoe on 2007-03-07
> **maniacmusician said:**
> Not to be nitpicky, but it's Hoary, not Whory :)

And [oops] I haven't read the earliest pages. If he can get 1200x900 in XP, then he should be able to get it in Linux as well. At the moment,  he can only get 1280x1024.


GrantShoe: Try putting 1200x900 as the first option in your Modes line. That may be the maximum for your card.

right now i'm getting 1024x768 but i tried to force higher.  i feel like in xp, i probably got a higher resolution than this but don't quote me.

[[IMG]http://img409.imageshack.us/img409/1332/snapshot3qe9.th.png[/IMG]](http://img409.imageshack.us/my.php?image=snapshot3qe9.png)

---

### Post by maniacmusician on 2007-03-07
> **GrantShoe said:**
> right now i'm getting 1024x768 but i tried to force higher.  i feel like in xp, i probably got a higher resolution than this but don't quote me.

[[IMG]http://img409.imageshack.us/img409/1332/snapshot3qe9.th.png[/IMG]](http://img409.imageshack.us/my.php?image=snapshot3qe9.png)
I quoted you :)


Silliness aside, you sound like you've got a good plan going. Good luck with whenever you try envy.

Here's a couple of things that may help you:

- A command: sudo dpkg-reconfigure xserver-xorg    That command regenerates Xorg.conf according to your input. It lets you choose a driver (pick the "nvidia" one), it lets you pick resolutions as well. You should select 1024x768, 1280x1024, and everything in between. Go higher if you want. The computer will pick the highest that your monitor and video card can do. With this command  you can also  input certain specifics like HorizSync and VertRefresh rates. 

- Research your card a little to see what other people have gotten out of it. It'll at least be a good starting place.

PS: What's with that dark gray theme? I'm pretty sure that's not a default theme :)

---

### Post by GrantShoe on 2007-03-07
i appreciate the help and this thread has been bookmark'd so i can come back to it.

my buddy came over yesterday and he was helping me try to get that 802.1x client working so he knew my password.  i leave for 5 minutes and next thing i know, he's changed everything to the redmond themes.  i'm so happy to not have to look at xp (even though it's on my laptop directly to the right... but STILL.

so i tried to change back to something bareable.  

in appearance - colors its the color scheme "system" and i'm using the "plastik" window decoration.

he also changed the screen so that i type in my password to log on and then next screen that comes up looks like the xp loading screen but i haven't found that fix yet.

any suggestion for improvement, i'm all for it. I'm a minimalist with my computer layouts and looks so anything flashy is usually not my fancy.

is there a thread where people post their desktop layouts and preferences?

---

### Post by maniacmusician on 2007-03-07
If you go to the Cafe subforum, there is a "show off your desktop" thread each month, It's stickied at the top of the Cafe subforum.

As for customizing your themes, do this: right click on your bottom taskbar > Configure Panel > "Menus" tab > Optional Menus > Tick off the "settings" menu.  Hit apply. Now, in your KMenu, there will be a "settings" subset with all sorts of options in it. There's also a main "Control Center" (KMenu > Settings > Control Center) With all sorts of appearance customizations in it.

The screen that he changed to look like the Windows XP Loading screen is called the splash screen, you can change it at Kmenu > Settings > Appearance & Themes > Splash Screen

You can also go to [http://www.kde-look.org](http://www.kde-look.org) to get more themes, splash screens, color profiles, etc.

---

### Post by bgochnauer on 2007-03-08
I have a Riva TNT2 card as well but the resolution, stuck at 640x480 was because my monitor didn't detect correctly. Once I set my monitor to Flat Panel 1280.x1024 I could set my video to 1280x1024. This has happened on MANY distros.


I can't find the nvidia-glx-legacy driver, adept has it listed but grayed out. 
(Running Kubuntu)
Synaptic can't find it.

Downloaded from debian site and tried but said it needed xorg SDK.
I'm rather new (2 months) but couldn't decern if xorg-dev and xorg-SDK are the same thing.
Can't find Xorg SDK either.

I was hoping for a nvidia-glx-legacy 'Unbuntu' package but can't find it.?

Thanks.

---

### Post by maniacmusician on 2007-03-08
> **bgochnauer said:**
> I have a Riva TNT2 card as well but the resolution, stuck at 640x480 was because my monitor didn't detect correctly. Once I set my monitor to Flat Panel 1280.x1024 I could set my video to 1280x1024. This has happened on MANY distros.


I can't find the nvidia-glx-legacy driver, adept has it listed but grayed out. 
(Running Kubuntu)
Synaptic can't find it.

Downloaded from debian site and tried but said it needed xorg SDK.
I'm rather new (2 months) but couldn't decern if xorg-dev and xorg-SDK are the same thing.
Can't find Xorg SDK either.

I was hoping for a nvidia-glx-legacy 'Unbuntu' package but can't find it.?

Thanks.
hi,

do you have all your repositories enabled? 

To do this, open Adept. Click on View > Manage Repositories. I'd tick off all the ones on the first tab for good measure. The only repository I don't recommend using is "Backported updates" in the Updates tab. That one can sometimes cause problems.

or if you want, just enable the "multiverse" repositories, because that's where nvidia-glx-legacy is.

---

### Post by orangenick on 2007-03-12
Hi guys,

Just wanted to say I have the TNT2 64mb card you're all talking about:

(I have no idea what I'm doing.  I but I think that makes me like (almost) everyone else.)

 I'm not entirely sure what happened but sometimes I got high-res but mostly i got 800x600, so tonight I decided to try to "sort it out"

First I tried the add/remove, searched for an nvidia driver and although it suggested I should use the legacy driver it also refused to install it (go figure...) so I installed the non-legacy one.  I don't know if that had any effect or not.

I didn't get the high res screens, so I installed the envy script (retarted 'noob' and proud cos at least I know the difference between your and you're) followed the log-out advice, alt-ctrl-f1 (wtf? panic...) logged in and realised that I'd forgotten how to run 'envy'. After the usual gibberish that I have to type in commands, I didn't believe it could be as easy as writing 'envy' without at least one -i or something, so I decided to 'go back in' and try again.

Starting with Alt+ctrl+F1 and working updwards I eventually got back to the login screen, logged in, (800x600) and a window appeared saying that I had to re-start the machine to apply an update. What update? dunno, best do as it says... I restarted.

when the machine had restarted, for some reason, the login screen was 'high-res'.. wow. I checked the driver and it was 'nv'.  From this, I decided that I really don't know what I'm doing.  

Once I start a path I follow it to the end so I logged in, checked this forum (just 'envy', really? .. ok remember that!) and logged out again, crossed my fingers,  ran the envy script, noticed in all the stuff that went past that it uninstalled my nvidia driver.. did some other stuff and finished. I logged back in and now I'm offered the following screen res:

1280 x 1024   
1152 x 864 
 and various other options.

So don't loose heart because your card can do up to 1280 x 1024.  If you want me to post any of my configuration files I can, but you'll have to tell me which one and where it is cos I really don't know what I'm doing.

More power to scripts that sort stuff out for you automatically, (ok, sometimes they don't work) ... I agree with the ManicMusician about "teaching", I really wish I knew what I was doing, but Linux has got so much better since I tried to use it two years ago and got nowhere for 3 months, formatted and installed Windows..

I'd like to ask a question thats completely unrelated if no-body minds: why doesn't yum work on Ubuntu?  Five evenings of arguing with MadWifi were fixed by the yum command on my other 'project' Fedora 6 so I'm kinda missing it already..!

nick

---

### Post by maniacmusician on 2007-03-12
hey nick, 

thanks for the heads up, good sir. I think it would be great if you could post your /etc/X11/xorg.conf so that GrantShoe and future users can make good use of it.

As for your other comments about teaching; yes, I agree that automated stuff has it's place. It's good when:
> -  you don't have a lot of time to work on stuff yourself (but you need to understand, and you do, that there's more of a chance of screwing up when it's automated)
- when you already know what you're doing, but automating it will make it happen faster
- when the automation process is so perfect that nothing will ever go wrong (this will never happen)

So while I totally agree that automated things can be great and useful (hey, I use them myself), I think it's also important to learn and understand how stuff works. You don't have to be a geek to understand it; just gotta take your time and be willing to learn. 

Anyways, thanks for posting, nick.

---

### Post by HasratUSA on 2007-03-13
I'm Just conferming that:

1. Beryl is working, never crashing but crashes when I run Pengune Planet Racer. I have to stop Beryl and then run it to avoid a crash. Apart from that, I'm enjoying every single feature of Beryl thanks to ManiacMusician,

2. After carefully reading and following his guidelines, I added "1280X1240" before appropriate places and now after every restart, the computer is picking up the correct and my desired resolution,

3. I'm using Gyachi Improved to use Yahoo Messenger's voice and webcam features. Download and run it at your own risk from [http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/) if you have been looking for a true alternative to Yahoo Messenger for Linux but to no avail.

3. I'm not having any kinds of problems with the OS I'm running, Thanks to anyone and everyone who ever cared to stretch their arms in times of my need.

---

### Post by Slim Odds on 2007-03-13
> **maniacmusician said:**
> Not to be nitpicky, but it's Hoary, not Whory :)

Depends on how you installed it. :lolflag:

---

### Post by punong_bisyonaryo on 2007-03-28
Good day!

Sorry about this, I posted a question in this link:

[http://www.ubuntuforums.org/showthread.php?t=365388&highlight=GLX_EXT_texture_from+pixmap](http://www.ubuntuforums.org/showthread.php?t=365388&highlight=GLX_EXT_texture_from+pixmap)

I had a question regarding using Beryl with a RIVA TNT2, and seeing how such a wonderful support this thread is having, maybe you could help me out too.

I get an GLX_EXT_texture_from pixmap fail when starting beryl.

---

### Post by maniacmusician on 2007-03-28
> **punong_bisyonaryo said:**
> Good day!

Sorry about this, I posted a question in this link:

[http://www.ubuntuforums.org/showthread.php?t=365388&highlight=GLX_EXT_texture_from+pixmap](http://www.ubuntuforums.org/showthread.php?t=365388&highlight=GLX_EXT_texture_from+pixmap)

I had a question regarding using Beryl with a RIVA TNT2, and seeing how such a wonderful support this thread is having, maybe you could help me out too.

I get an GLX_EXT_texture_from pixmap fail when starting beryl.
I'm not sure, but I think that means that your card doesn't support pixmap textures...in other words, it's too old. Just a guess though. You should  probably check with the folks on IRC (#beryl on  freenode) or at the Beryl forums.

---

### Post by punong_bisyonaryo on 2007-03-30
Darn! And all of the computers here in the office are on TNT2s. I wonder if there's a way to get through this. I just got a Geforce fx 5200. I think I'll have better luck with that at home.

PS. Even if glxinfo says DirectRendering is yes, how do you know your video card is actually being used? 3D applications seem really slow, even the screensavers, even for a TNT2. I tried bringing down to the lowest setting Nexuiz, but still awfully slow. Screensavers like the GLBlur rn slow even in the screensaver preview window.

---

### Post by Aliarse on 2007-03-30
> **punong_bisyonaryo said:**
> Good day!
I get an GLX_EXT_texture_from pixmap fail when starting beryl.

I got the same error when i tried beryl, running a TNT2M64. Im wondering how [HasratUSA]("http://ubuntuforums.org/member.php?u=246512") got it working if he's running a TNT2..:confused:

---

### Post by punong_bisyonaryo on 2007-03-31
> **orangenick said:**
> I'd like to ask a question thats completely unrelated if no-body minds: why doesn't yum work on Ubuntu?  Five evenings of arguing with MadWifi were fixed by the yum command on my other 'project' Fedora 6 so I'm kinda missing it already..!

nick

Isn't Yum like Ubuntu's apt-get? Fedora and Ubuntu have different package managers, and also have roots in different Distros. Ubuntu is Debian-based, Fedora is Redhat-based(??? or is it the other way around?). Haven't tried using Yum much though.:confused:

---

### Post by HasratUSA on 2007-03-31
> **Aliarse said:**
> I got the same error when i tried beryl, running a TNT2M64. Im wondering how [HasratUSA]("http://ubuntuforums.org/member.php?u=246512") got it working if he's running a TNT2..:confused:

Hi,
    I'm running Edgy Eft with Beryl up and running on not Riva TNT2, but nVIDIA GeForce 7300 LE UltraBuffer 256 MB Video RAM and it's not really as expensive as the name might sound. It's a great card that Dell offered me when I bought an AMD Athlon Dual Core 64 bit 3800+ from them 3 months ago.

---

### Post by jack24 on 2008-02-17
Thank you.  I actually like messing with the computer, but I don't always have time.  Your advice is great.

Thanks

---


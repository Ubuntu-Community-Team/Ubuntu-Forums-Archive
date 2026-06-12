---
title: "[SOLVED] dual monitor setup on my video card with 2 video ports"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-08-25
Hello, 

I received a computer with a video card that looks like it can accept 2 monitors. If this is what I think it means, I can and want to have  a dual-monitor setup.  

You are probably wondering what video card is in my computer. Me, too. So, I did lspci. Here are what I think are the pertinent results from lspci:
 
> 05:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)]
05:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)] (Secondary)Please note: I am not sure if the description in brackets (i.e. "Radeon X850XT Platinum (PCIE") is what the computer found by itself, or whether that text was something I typed in manually. I do not remember now. So if the text in brackets could be user-edited, it may be inaccurate. Just a warning. I guess what I'm trying to say is that I'm not sure exactly what video card is in my box. Please explain.

I don't know why I get "duplicate" information. Is it an error, or is that what happens when you have a video card that can accept 2 monitors. Please explain.

The visible part of the video card (not hidden inside the box) looks like the attached thumbnails.

My video card has one S-Video port and 2 DVI ports.


Currently, only one (the left one) DVI port works. When I unplug the monitor from the left DVI port and plug it into the right DVI port, my monitor stays blank/black. Why is this?

Is it possible to have a dual monitor setup with my computer, so that I could have, in effect, the screen space of the sum of the 2 monitors? Does this make sense?
If so, how do i set up my ubuntu to do that?

---

### Post by Spr0k3t on 2007-08-26
There is a high chance you have the ATI Radeon X850XT.  I've seen other threads where people have set up these cards with dual monitors but they are set up without hardware accel.  I'm sure you will need to tweak your xorg.conf in order to get this working as mentioned in this thread here: [http://ubuntuforums.org/showthread.php?t=530675](http://ubuntuforums.org/showthread.php?t=530675) .  Before making any changes to your xorg.conf though, you should make a backup of your known good configuration.```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
```

As a side note, editing the xorg.conf may become a thing of the past with Gutsy.  I've been  testing the multiple screen support with nvidia and intel chipsets and the devs have done really good.  Please keep in mind that Gutsy is still alpha software though.

---

### Post by hanzj on 2007-08-26
Hi,
That link you gave doesn't have a happy ending. The OP over there is still unable to have a dual-monitor setup.

---

### Post by hanzj on 2007-08-31
I have hardware acceleration on. What should I do next? Thank you.

---

### Post by hanzj on 2007-09-02
So far no answer.

Will the release of Ubuntu 7.10 Gutsy Gibbon solve my problem?

---

### Post by hanzj on 2007-09-22
I have 2 moniters plugged into my video card, and they both show the same thing. How can I have a dual-monitor setup that essentially gives me an expansion of my desktop, if you know what I mean (rather than just 2 duplicates)?

---

### Post by Pumalite on 2007-09-22
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by CaptainInsaneO on 2007-09-22
Here's how to do it (if anyone finds any errors in this, let me know):

You will want to use Xinerama to do this, Twinview is for nVidia cards only.

Open terminal, and type this:

```
lspci -x | grep -i -e VGA -e DISPLAY
```

to find information about your video card.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
and then type
```
sudo gedit /etc/X11/xorg.conf
```

You need to tell X about your second monitor. Find the "Monitor" section in your xorg file. Right underneath it, add a second Monitor section to identify the new monitor. For an example:

```
Section "Monitor"
       # Second Monitor
       Identifier       "CRT"                # Or LCD
       Option           "DPMS"
       HorizSync        31.5 - 57.0       # Will depend on your monitor
       VertRefresh      50-100             # Will depend on your monitor
EndSection

```

You also need to create a second "Screen" section. It should look something like the example below, so that X knows about the second screen.

```
Section "Screen"
       #Defines 2nd Screen
       Identifier       "Second Screen"
       Device           "ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)] "
       Monitor          "CRT"       # Or whatever you put for the monitor Identifier
       DefaultDepth      24
               SubSection "Display"
                      Depth       24
                      Modes      "1280x1024"       # Your max res
               EndSubSection
EndSection
```

Make sure the "Monitor" lines in your "Screen" section match the identifiers from the Monitor sections. The device name should match the results from lspci (what you did earlier)

Now you need to edit your ServerLayout. It should look something like this, I've bolded the parts you need to pay special attention to:

```
Section "ServerLayout"
       Identifier           "Default Layout"
       [B]Screen 0             "Default Screen"
       Screen 1             "Second Screen" RightOf "Default Screen"[/B]
       InputDevice        "Generic Keyboard"           #Etc,etc.
```

You should really only need to add the bolded lines, so DON'T copy and paste this example right into your xorg.conf. Just the bolded parts.

Now, to have your displays linked (one desktop instead of two seperate ones), you need to add this section to your xorg file:

```
Section "ServerFlags"
       Option       "Xinerama" "true"
EndSection
```

And restart X (Ctrl+Alt+Backspace). If something gets messed up (a.k.a. X stops working for any reason) you can always just go to a tty and do this:

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

to restore your working xorg.conf. Good luck, and if you have any questions just check back here.

---

### Post by hanzj on 2007-09-22
What about BigDesktop? If I have the choice between xinerama and BigDesktop, which should I choose? [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174) inspired me to ask this question.

---

### Post by CaptainInsaneO on 2007-09-22
With that question, you really get into the beauty of Linux: you can use pretty much whatever you want as long as it fits your needs and it works.

So you have to ask yourself, will BigDesktop work for what you want? Will it be easier for you to set up? The decision is really yours and I can't make it for you, you should search around for more info on it.

Here's another thread for your reference: [http://ubuntuforums.org/showthread.php?p=1773544](http://ubuntuforums.org/showthread.php?p=1773544)

---

### Post by moon2js on 2007-10-29
> **CaptainInsaneO said:**
> Here's how to do it (if anyone finds any errors in this, let me know):

You will want to use Xinerama to do this, Twinview is for nVidia cards only.

Open terminal, and type this:

```
lspci -X | grep -i -e VGA -e DISPLAY
```

This is important because it will tell you if you can even do a dual-head setup. It's fairly simple: if there are two devices listed, it's possible. If there's one, it's not. If there are two, back up your xorg.conf...

```
$ lspci -X | grep -i -e VGA -e DISPLAY
lspci: invalid option -- X
Usage: lspci [<switches>]
```

Maybe you meant a lowercase X? In which case I get:

```
$ lspci -x | grep -i -e VGA -e DISPLAY
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
```

I only have one entry, so I can't do a dual-head setup?

As it is now, I have two monitors plugged into the one graphics card (both using VGA cables, but on the card, there's one DVI and one VGA connector -- I use a changer to change a VGA cable to DVI for one of the monitors to the card). In Gutsy (and Feisty before), this results in the monitors mirroring each other.

Can I not make the desktop span across monitors? Is that what you mean by a "dual-head setup"?

In XP, the monitor spanning (with the exact same hardware config) works perfectly without any tweaking (i.e. my desktop is extended on to the second monitor and I can drag windows from one to the other). So I know in theory the card can handle monitor spanning. But can I do this in Ubuntu with this somewhat old graphics card?

---

### Post by CaptainInsaneO on 2007-10-31
Thanks for pointing that out... I actually don't know what i was thinking when I wrote that. Must have been late at night. :lolflag:

I've edited the post to fix the errors, hopefully it doesn't make me look as dumb now.

"Dual-head" simply means having two monitors for one computer. You can absolutely do it, as is obvious by the fact that you're getting an image on both of them right now.

Please post your xorg.conf and I can help you fix your problem.

---

### Post by moon2js on 2007-10-31
I briefly tried to get a dual-head config in Feisty but gave up. Now in Gutsy, there's an option "Screens and Graphics" but there's only one "Screen 1" listed (even though the second monitor is mirroring the first) and the "Secondary Screen" options are greyed out.

If it's possible to change the mirroring to spanning by editing xorg.conf, please do point me in the right direction:

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
	Load	"dbe"
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
	Identifier	"ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"AddARGBVisuals" "True"
	Option		"AddARGBGLXVisuals" "True"
EndSection

Section "Monitor"
	Identifier	"EN7220"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
	Monitor		"EN7220"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	Option "AddARGBGLXVisuals" "True"
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

### Post by CaptainInsaneO on 2007-11-01
Ok, I've rewritten your xorg.conf.

This is a mere suggestion, look over it and edit it to your needs, but I've added all the necessary fields for you. Remember to put modelines for the second monitor! I've left those blank for you because I don't know your hardware.

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
	Load	"dbe"
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
	Identifier	"ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"AddARGBVisuals" "True"
	Option		"AddARGBGLXVisuals" "True"
EndSection

Section "Monitor"
	Identifier	"EN7220"
	Option		"DPMS"
EndSection

Section "Monitor2"
	Identifier	"MONITOR2"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
	Monitor		"EN7220"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	Option "AddARGBGLXVisuals" "True"
EndSection

Section "Screen2"
	Identifier	"Secondary Screen"
	Device		"ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
	Monitor		"MONITOR2"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		
	EndSubSection
	Option "AddARGBGLXVisuals" "True"
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Default Screen"
	Screen 1	"Secondary Screen" RightOf "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "ServerFlags"
	Option		"Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

P.S. Don't forget to back up your xorg before editing!

---

### Post by moon2js on 2007-11-01
Thanks for doing that! I'll give it a go when I get home to that computer.

It looks like all you did was add Monitor2 and Screen2 sections and edited the ServerLayout section. Is there some reason why these sections weren't added during installation?

I remember messing with X11 config years ago and there was some utility that you could evoke manually to grab the monitor specs and automatically add them to the conf. Does that exist on Ubuntu and would that work on the second monitor?

Also, I just noticed all those "wacom" (tablet input?) entries on my xorg.conf. Is that normal? I certainly don't have any input devices besides a mouse and a keyboard (connected via a hardware KVM switch).

---

### Post by CaptainInsaneO on 2007-11-01
Personally, I have no clue why they're weren't added when you first configured X. Did you happen to run the ati-config tool when you first set things up? My experience with ATI is very very limited so I don't know. I know that if you use nVidia, the nvidia-settings will configure both screens for you.

I also added the Server Flags section.

I don't know of any tool that does for you, and a quick Google search didn't come up with anything for me either (I'm trying to hurry because I'm making dinner while I type this :lolflag:) but I bet if you looked up your monitor, you could find the specs that way.

The wacom entries are normal, I've actually never seen a xorg.conf without them. You can ignore them, they're useful if you have a Tablet PC.

Edit: If you'd like, you can try using the following command instead, but remember (as always) to back up your xorg.conf beforehand.

```
aticonfig --initial=dual-head --dtop=horizontal --screen-layout=right -v
```

and then Ctrl+Alt+Backspace

---

### Post by moon2js on 2007-11-01
[Edit: I was going about something completely wrong, and I don't want anyone to waste time/be confused by this post, so I deleted it. Sorry, folks.]

---

### Post by hanzj on 2007-11-03
I'm now using Gutsy Gibbon 7.10. According to [http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710) 

> [LIST]
[*]The ati driver has dropped MergedFB / Xinerama support in favour of xrandr 1.2 support, and old multi-head xorg.conf setups will break. To set up dual-head see the guides at  [COLOR=RoyalBlue][http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html) [/COLOR]or [COLOR=RoyalBlue][http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)[/COLOR][/LIST][LIST]
[*]As xrandr and xinerama are incompatible, you cannot mix some graphics cards using xrandr-enabled drivers with others that are still limited to using xinerama. In this case, you will need to revert to pre-xrandr versions of the respective drivers: for Intel cards, use the old "i810" driver instead of "intel", for ATI cards, use the old [COLOR=RoyalBlue][6.6 version]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/1:6.6.3-2ubuntu6")[/COLOR].[/LIST]  
So my question is: How can we configure without messing around with xorg.conf?
How can we configure using xrandr? I tried setting up xrandr, but I get this error message:
> 
                             $ xrandr --output DVI-0 --left-of DVI-1
xrandr: screen cannot be larger than 1600x1200 (desired size 2880x1200)


---

### Post by moon2js on 2007-11-03
Thanks for posting that. I googled a few mention that Xinerama was dropped in Gutsy, which explains my problem, and the [Debian howto link]("http://wiki.debian.org/XStrikeForce/HowToRandR12") you provided was really helpful.

I'm having a similar problem (screen size not large enough error message). Did you try specifying the virtual screen size in xorg.conf? 

> **II.5. Placing outputs in a virtual screen**

Randr 1.2 provides the ability to create a large virtual screen and place multiple output in it, either with or without overlapping zones. To reduce memory consumption, drivers will often create a default virtual screen with small dimensions, for instance 1600x1200. Look at the output of xrandr to know your virtual screen dimensions. It would be 2048x1152 if xrandr reports:

```
  $ xrandr
  Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 2048 x 1152
```

If you plan to use multiple outputs displaying different zones, you should configure your xorg.conf by adding a Virtual line to subsection Display in the Screen section.

```
  Section "Screen"
    ...
    SubSection "Display"
      Depth 24
      Virtual 3000x2000
    EndSubSection
  EndSection
```


My current setup shows:

```
$ xrandr 
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1200
VGA-0 connected 1280x1024+0+0 (normal left inverted right) 376mm x 301mm
   1280x1024      60.0*+   75.0     59.9  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
DVI-0 connected 1280x1024+0+0 (normal left inverted right) 300mm x 225mm
   1024x768       75.0 +   84.9     75.1  
   1280x1024      59.9* 
   800x600        84.9     75.0  
   640x480        84.6     75.0     60.0  
   720x400        70.1  
S-video disconnected (normal left inverted right)
```

So I added to my xorg.conf:

```
    SubSection "Display"
      Depth 24
      **Virtual 2560x1024**
    EndSubSection
```

But that causes Ubuntu to start up in low-graphics mode. I'm not sure if I made some mistake or my older hardware (Radeon 7500) isn't up to the task, as the howto warns is possible. I tried changing DefaultDepth to 16, but that didn't change anything. I tried removing xorg.conf entirely and letting autoconfiguration work, but it does what it normally does and gives me mirroring at 1280x1024.

Extended desktop (screen spanning) works perfectly in XP, and I saw someone on [a bug report]("https://bugs.launchpad.net/xorg-server/+bug/132716") (unrelated, but same hardware) mention they got dual-head working. Does anyone know anything I can try or see any mistakes I made?

---

### Post by CaptainInsaneO on 2007-11-04
I'm sorry, I had not realized xinerama was outdated in Gutsy.

I also wrote that howto before Gutsy launched. At this point I'm out of ideas to help you...

I'll keep looking around though, if I find something out that I think will help your problem, I'll definitely let you know! :)

---

### Post by hanzj on 2007-11-04
Dear Moon2JS and CaptainInsaneO,
[http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/](http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/) has helped. Moon2JS, you may be right. One probably has no way to avoid manually editing the xorg.conf file. That's what I did and now enjoy 2 displays.


My problem now is that I can't seem to get the ATI restricted driver working with the xrandr/xorg setup.

---

### Post by moon2js on 2007-11-06
OK, I found one mistake I made. Some of the howtos describe adding the Virtual line to xorg.conf with syntax like "3000x2000" (or whatever resolution), but apparently that's incorrect because Gutsy starts up in ugly-mode when I do that. There should not be an "x" between the numbers, i.e. "Virtual 3000 2000". After doing that, Gutsy works fine, and xrandr reports that I have enough screen real estate to extend the desktop.

But when I try something like:

```
xrandr --output DVI-0 --left-of VGA-0
```

...my VGA-0 (LCD flat panel, 19in) just shows gibberish and the right third (or half?) of the DVI-0 (CRT 17in) shows all broken window parts that don't respond to clicks (and appear to be what should be on the primary monitor). I have to drag the terminal to the working/viewable left two thirds on the secondary monitor to turn off this craziness. This happened when both monitors were set to the same resolution (1280x1024) and the Virtual (screen) was 2560x1024.

Anyone have any idea of what I'm doing wrong or what I might try?

---


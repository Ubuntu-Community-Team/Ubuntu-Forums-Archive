---
title: "Comp is slow. Probably graphics?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-09-21
There's a bit of drag on my comp; it hesitates quite a bit, or the pointer moves in jumps rather than smoothly across the screen. The standard test I have is to load a simple game, like Freecell Solitaire, and see how easiy and quickly I can manipulate the cards. It&#347; very slow.

So I go to the SiS site, and they claim to have an online chipset identifier. I've left it running for as long as ½ an hour, and nothing has happened. So I went to their Linux faq page, and they claim that the current Linux kernel has all of the default and up-to-date drivers.

By the way, I also ran every option available through Automatix, and nothing seemed to help there.

$ lspci gives me this:
> 0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter

Any suggestions? TIA

---

### Post by Qrk on 2006-09-22
Are you sure you are using the SiS drivers? You can check xorg.conf (etc/X11/xorg.conf) to see if the driver under your graphics device is listed as SiS, or as a slightly easier method, try

```
sudo dpkg-reconfigure xserver-xorg
```

and verify that sis is slected in the second dialog.

---

### Post by ricardisimo on 2006-09-22
> **Qrk said:**
> Are you sure you are using the SiS drivers? You can check xorg.conf (etc/X11/xorg.conf) to see if the driver under your graphics device is listed as SiS, or as a slightly easier method, try

```
sudo dpkg-reconfigure xserver-xorg
```

and verify that sis is slected in the second dialog.

I not really sure what this means:

 > No X server known for your video hardware.                                &#9474;
 &#9474;                                                                           &#9474;
 &#9474; Either you have no video hardware installed on this machine (serial       &#9474;
 &#9474; console only?), or the "discover" program was unable to determine which   &#9474;
 &#9474; X server is appropriate for your video hardware.  This could be due to    &#9474;
 &#9474; incomplete information in discover's hardware database, or it could be    &#9474;
 &#9474; that your video hardware is simply not supported by any available X       &#9474;
 &#9474; servers.   

I followed along for a few steps after, but thought the better of it after I imagined not having any graphics at all and being unable to undo it. Where to go from here?

---

### Post by ricardisimo on 2006-09-22
Hmmmm... I just spotted another problem: my CPU usage is through the roof pretty much at all times, and almost all of it is by "checkgmail", which was one of the *Automatix* installs. A few odd things... Add/Remove doesn't even know it's there, so I can't uninstall, only install again. Also, even after I quit Gmail checker, it's still using CPU - lots of it. How do I uninstall this awful program? Side note: what is Xorg?
One more thing... Immediately after using Frostwire, my connection(s) started acting up (and along with it my CPU usage went up dramatically as well. It is sending data NONSTOP now, even after I quit and kill all of the pertinent programs, and even after I disable all connections. What the hell is that? Mind you, I have a dismal view of **all **post-Napster file sharing programs. Not one has treated me well. Zero. Oh, well... TIA.

---

### Post by jcrnan on 2006-09-22
xorg is the what is keeping all graphics on the pc working.

To remove a program completely you can do "sudo apt-get purge <programname>" or replace purge with remove if you want to keep your settings for the program.

As for why its going slow Im not sure, only thing I could reccomend would be trying to install new gfx drivers.

---

### Post by Tomosaur on 2006-09-22
Alright, I take it you're pretty new to linux? The commands people keep telling you to do should be input into what is known as the terminal. This is a command-line interface, and you would do well to learn it. Most people can get by in Ubuntu without it, but when things are going wrong, the terminal can usually get you out of your fix.

Anyway:
1) Click Applications, then Accessories, then Terminal.

2) In the terminal, type this:
```

sudo dpkg-reconfigure -phigh xserver-xorg-core

```

3) When it asks for your password, type the same password you use to log in to your machine. You will not see your password being typed, so be sure to spell it right.

Reboot your machine (or do an X-Reboot, which can be done using ctrl+shift+backspace). If that doesn't improve things, please open up a text editor, open the file /etc/X11/xorg.conf, and paste the contents here.

---

### Post by ricardisimo on 2006-09-22
I followed both of your recommendations, and one or the other did the trick as far aseasing up on the CPU. Thanks to you both. Unfortunately, speed is still somewhat of an issue, at least based on the hesitation in simple solitaire games and the *really* slow movement of all of the varieties of screensaver. I going to assume that determining my graphics card chipset is vital for any progress here, just as with the modem or any of the other cards. Or, is there further refining that can be done without this info? By the way, what exactly did that last bit of code that Tomasaur gave me reconfigure? TIA.

---

### Post by ricardisimo on 2006-09-29
I'm still wondering what Tomosaur's code did, exactly... just curious and still learning.

Comp's still dragging more than a little bit, and I looking for options; where to look, what to alter, if anything. I still suspect my graphics card/driver.

Are any other noobs experiencing this drag? Don't get me wrong, by the way... I loving Ubuntu more and more every day, for reasons both philosophical and practical. But I definitely was of the impression that, if anything, Ubuntu and the other Linux OSs were faster, not slower than Windows. Looking forward to correcting the issue. TIA.

---

### Post by ricardisimo on 2006-09-30
I'm still far from optimal, I'm still wondering if anyone else is having problems with the computer dragging more than they would have expected before installing Ubuntu, and I'm beginning to wonder if perhaps there isn't another culprit: my RAM. What made me think it might be this is watching Pan struggle mightily with the header list of a large binaries group and then simply shut down (several times). Also, multitasking (browser, card game, terminal) shouldn't be as rough as it currently is. How do I go about getting specs on my memory and/or tinker with it?
Before I stray too far from the graphics issue...
When I try configuring xserver-xorg, this is the first curious thing I see:

```
No X server known for your video hardware.                                &#9474;
 &#9474;                                                                           &#9474;
 &#9474; Either you have no video hardware installed on this machine (serial       &#9474;
 &#9474; console only?), or the "discover" program was unable to determine which   &#9474;
 &#9474; X server is appropriate for your video hardware.  This could be due to    &#9474;
 &#9474; incomplete information in discover's hardware database, or it could be    &#9474;
 &#9474; that your video hardware is simply not supported by any available X       &#9474;
 &#9474; servers.        
```

Furthermore, I guess I'm not using an SiS driver after all, but rather ***vesa*** on a Generic Video Card. Below is the xorg.conf file that someone above asked to see:


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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
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



Thanks once again for everyone's help. It is greatly appreciated.

---

### Post by ricardisimo on 2006-10-04
There's been a bit of jumping back-and-forth between threads, since I thought I might have a memory issue, but here's the update for this topic: I switched drivers from *vesa* to *sis*, and my FPS dropped by two-thirds (which is bad) from an already pathetic 120 to about 40, but my comp's performance suddenly became much smoother, with less seizing up, and no crashes yet (which is good). I have no explanation for this, and I'm not complaining, but obviously I'd like to get everything working a bit faster.

Along with all of the info in the previous post, I got this from ***sudo lshw***:

```
 *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: 661/741/760/761 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga cap_list
                resources: iomemory:d0000000-d7ffffff iomemory:dfee0000-dfefffff 
```

I'd greatly appreciate any help identifying my graphics card chipset so as to make sure that I'm choosing the best possible driver. Thanks again for everything.

---

### Post by DarkN00b on 2006-10-04
You need the correct drivers for your SIS video system.  I don't see the drivers in the repositories, so I'll do a little Googling to see what I can find.

---

### Post by ricardisimo on 2006-10-04
You rock my friend! Going back to my original post: does anyone think that my firewall settings are the reason the SiS site's chipset detector isn't doing what it's supposed to do? Seems like they would have factored that in, or no?

---

### Post by srt4play on 2006-10-04
Backup you xorg.conf:

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Open the file for editing:

sudo nano /etc/X11/xorg.conf

Change the word "vesa" in the file to "sis".

Save the file with ctrl-o then enter.  Exit the editor with crtl-x then enter.  

Press ctrl-alt-backspace to restart the X server with the new configuration.

These steps solved slowness on one of my SiS graphics equipped computers.

---

### Post by DarkN00b on 2006-10-04
Here's the best I could do for you, as SIS only has 2 year old Linux drivers for this chipset and those are for Red Hat.

Read these pages carefully:

[http://xorg.freedesktop.org/archive/X11R6.8.0/doc/xorg.conf.5.html]("http://xorg.freedesktop.org/archive/X11R6.8.0/doc/xorg.conf.5.html")
[http://xorg.freedesktop.org/archive/X11R6.8.0/doc/SiS2.html]("http://xorg.freedesktop.org/archive/X11R6.8.0/doc/SiS2.html")
[http://xorg.freedesktop.org/archive/X11R6.8.0/doc/sis.4.html]("http://xorg.freedesktop.org/archive/X11R6.8.0/doc/sis.4.html")

Read them in that order to build up an understanding of what is going on, and that may help you fix your problem.

Before you change anything though, type "glxinfo" into a terminal window and post the first 5 lines of the output. I'd like to see what that says.

Thanks to SD-Plissken for the links he provided in [this]("http://www.ubuntuforums.org/showthread.php?t=124967") post  (which might interest you as well).

What srt4play said will probably work. You might still want to read the first two links I posted because they supply basic knowledge that you need if you are going to modify your xorg.conf file manually.

Also, as a new user you might be more comfortable using gedit instead of nano.  To use it just type sudo gedit /etc/X11/xorg.conf in the terminal.

---

### Post by djsroknrol on 2006-10-04
> **ricardisimo said:**
> There's a bit of drag on my comp; it hesitates quite a bit, or the pointer moves in jumps rather than smoothly across the screen. 

Are you still having issues with the mouse?....I don't think that Xorg.conf has anything to do with it and your entries look good for your mouse....just wondering...

---

### Post by srt4play on 2006-10-04
Actually, what I said will probably most definitely work. 

If you're already in the terminal, why open up gedit?  If I were going to sudo-edit a file with gedit , I would hit alt-F2 and put "gksudo gedit /path/to/file".  It's much faster to use nano if already in the terminal, and it's a good tool to know how to use anyway.

---

### Post by DarkN00b on 2006-10-04
That's true, I just thought he'd be more comfy with a gui based editor as a new user.

---

### Post by ricardisimo on 2006-10-05
> **srt4play said:**
> Backup you xorg.conf:

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Open the file for editing:

sudo nano /etc/X11/xorg.conf

Change the word "vesa" in the file to "sis".

Save the file with ctrl-o then enter.  Exit the editor with crtl-x then enter.  

Press ctrl-alt-backspace to restart the X server with the new configuration.

These steps solved slowness on one of my SiS graphics equipped computers.

I already did this, and like I said, it's much, much better in terms of performance; pages scroll smoothly, my display doesn't seem to be playing catch-up with itself, the mouse pointer doesn't jump around the page... all very good. The problem (if it is one) is that I strongly suspect that my comp should be operating much faster than it is. This suspicion is corroborated by the frames-per-second readings I'm getting, which are in the 40s rather than in the high-hundreds or even 1000s. Something's up, I know it is... I just don't know what. Any other guesses? Thanks again for your time, everyone.

---

### Post by ricardisimo on 2006-10-05
> **DarkN00b said:**
> Before you change anything though, type "glxinfo" into a terminal window and post the first 5 lines of the output. I'd like to see what that says.

```
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2

```

Here's hoping this is useful. I'm still reading the links you sent. Thanks.

---

### Post by DarkN00b on 2006-10-06
Ah, so direct rendering is not working.

The only thing I know to try is to add the following line to Section "Device" in Xorg.conf.

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"SiS"
	BusID		"PCI:1:0:0"
        VideoRam        32768          #Add this line to assigm 32 MB mem to chipset.
EndSection
```

Only do this if you have 32 megs of ram to spare.  For some reason some on-board chipsets do not report required menory, and some will not enable direct rendering without manually allocating that memory.  Such is the case with my Intel i855 chipset.

Restart Gnome and run glxinfo again.  If the third line says:

"direct rendering: yes"

then you have fixed your problem.  This is a simple and relatively harmless thing to try and it may fix your problems.

---

### Post by ricardisimo on 2006-10-06
> **DarkN00b said:**
> Ah, so direct rendering is not working.

The only thing I know to try is to add the following line to Section "Device" in Xorg.conf.

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"SiS"
	BusID		"PCI:1:0:0"
        VideoRam        32768          #Add this line to assigm 32 MB mem to chipset.
EndSection
```

Only do this if you have 32 megs of ram to spare.  For some reason some on-board chipsets do not report required menory, and some will not enable direct rendering without manually allocating that memory.  Such is the case with my Intel i855 chipset.

Restart Gnome and run glxinfo again.  If the third line says:

"direct rendering: yes"

then you have fixed your problem.  This is a simple and relatively harmless thing to try and it may fix your problems.

I'm assuming I can open xorg.conf with gedit and put "32768" in there. Why that number, if I may ask?

---

### Post by ricardisimo on 2006-10-06
More specifically, can I just add a new line "VideoRam..." with gedit, or should I be opening xorg.conf in a terminal and trying something else?

---

### Post by ricardisimo on 2006-10-06
Never mind... gedit won't let me anyhow.

---

### Post by ithaka on 2006-10-06
Hi,


I just finished installing Ubuntu 6.06LTS. When starting the first time I had a very low resolution at 60Hz. So I ran a dpkg-reconfigure xserver-xorg again, successfully.

But I have the feeling that my system is quite sluggish. Perhaps this is normal, it is just my (subjective) experience.

It is mostly the way the GUI (gnome) reacts. Also when surfing, I get often hickups in flash animations, window contents that build up rather slow (e.g. file browsing), none of the shipped screen saver that run smooth (ok detail). Small things like that.

I still use the default theme at 1152*864 24bit 75Hz.
Hardware is not state of the art anymore, but not that bad either:
- Intel P4 2.3GHz 512MB
- 80GB IDE Western Digital Caviar HD of which 20GB assigned tot Ubuntu, the other 60GB are split up in 20GB partitions with NTFS.
- Asus nvidia Geforce 4 AGPx4(or 2, not sure) 128MB, but recognized correctly by the xserver configurator.
- Soundblaster PCI sound card

Any ideas?

Olivier

---

### Post by ricardisimo on 2006-10-06
Please do me a favor and run "glxgears -printfps" in terminal. Let it run for a minute or so (with the gears in the foreground, by the way) and tell me what numbers you get. Thanks.

---

### Post by DarkN00b on 2006-10-06
Refer to the first post by srt4play above for how to edit xorg.gconf. Also try what he said. He has more experience with Linux than me.

[quote="ricardisimo"]Please do me a favor and run "glxgears -printfps" in terminal. Let it run for a minute or so (with the gears in the foreground, by the way) and tell me what numbers you get. Thanks.[/quote]

I don't know if this was aimed at me or not, but I get 470-480 fps.

---

### Post by ricardisimo on 2006-10-06
> **DarkN00b said:**
> I don't know if this was aimed at me or not, but I get 470-480 fps.

It was aimed at anyone and everyone, although probably more this last guy who's also having issues. I just need a point of reference, and now you've given me one. My fps is slower than 1/10th yours, and your numbers look modest compared to the 1000-1200s that I saw in another post. I definitely have to work on this.

There are other problems. My Pan newsreader is freezing up my comp whenever it works with groups that have more than, say, 100,000-150,000 articles. That's not even all that many headers... I can't even glance at the big binary groups. Fageddahboutit. It feels like a memory issue, rather than an app issue, just based on how well Pan works with the smaller groups.

Trudging forward.

---

### Post by ricardisimo on 2006-10-06
> **DarkN00b said:**
> Refer to the first post by srt4play above for how to edit xorg.gconf.

Whoops! I'm hoping this isn't a big problem... I don't appear to have a xorg.conf file any longer. Or rather, I have several of them: xorg.conf.20061003155956, xorg.conf.backup, and xorg.conf_backup, and perhaps a few others, but I think this is it. Which file is my comp using? Can I get the basic conf file back? How? Thanks for everyone's patience with me here. I'm clearly in way over my head for the time being, but I'll get better, I promise.

---

### Post by DarkN00b on 2006-10-06
> **ricardisimo said:**
> Whoops! I'm hoping this isn't a big problem... I don't appear to have a xorg.conf file any longer. Or rather, I have several of them: xorg.conf.20061003155956, xorg.conf.backup, and xorg.conf_backup, and perhaps a few others, but I think this is it. Which file is my comp using? Can I get the basic conf file back? How? Thanks for everyone's patience with me here. I'm clearly in way over my head for the time being, but I'll get better, I promise.

Unless you deleted it, there should be one file in there called xorg.conf.  This is the one your comp is using.  To get back to your original config, just view the directory as a list and find the oldest xorg.* and copy it to your home folder. Change the name to xorg.conf and always keep a copy somewhere. That way if you need to you can just copy that file to /etc/x11 whenever something goes wrong.

Heh, if I tank my system too badly, I usually end up booting into recovery mode and fixing things that way. This is technically frowned upon because you basically log on as root, but it makes things easier for me.

---

### Post by ricardisimo on 2006-10-06
> **DarkN00b said:**
> Unless you deleted it, there should be one file in there called xorg.conf.  This is the one your comp is using.  To get back to your original config, just view the directory as a list and find the oldest xorg.* and copy it to your home folder. Change the name to xorg.conf and always keep a copy somewhere. That way if you need to you can just copy that file to /etc/x11 whenever something goes wrong.

Heh, if I tank my system too badly, I usually end up booting into recovery mode and fixing things that way. This is technically frowned upon because you basically log on as root, but it makes things easier for me.

No... it's not there, but I think I know which one is being used, since only one of them has "sis" listed as the driver. It's bizarre. i know for a fact I never manually deleted anything. Is it possible that one of the command lines renamed it for some reason? If so, how the hell does bootup know which file to read?

As far as you know, can I rename the file just via nautilus? Thanks.

---

### Post by DarkN00b on 2006-10-06
> **ricardisimo said:**
> As far as you know, can I rename the file just via nautilus? Thanks.

Not that I know of.  You need root privs for that.

---

### Post by ricardisimo on 2006-10-06
> **DarkN00b said:**
> Not that I know of.  You need root privs for that.

OK. Done via sudo gedit... Now my fps is WAAAAAYY up in the high 40s instead of the low 40s. Either it made no difference (perhaps it's ignoring the xorg.conf and using one of the backups instead) or I need to enter a larger number (from the part-time handyman scholl: if a small hammer won't work, use a bigger hammer) or I'm tinkering in completely the wrong place. It could be something else entirely. Any thoughts? Thanks again.

---

### Post by DarkN00b on 2006-10-06
If it ain't working at 32768 it ain't gonna work. I wish I could help more, but I'm not much more than a noob myself. Sorry dude.

---

### Post by ricardisimo on 2006-10-06
> **DarkN00b said:**
> If it ain't working at 32768 it ain't gonna work. I wish I could help more, but I'm not much more than a noob myself. Sorry dude.

Don't "sorry" anything, guy. You've been a saint to put up with this as far as you have. If you're a nüb, I shudder to think how low I am on this particular totem. Thanks again.

Anyone else have any suggestions? I'm thinking I might do well to start a new thread, refined a bit by what's already been tried... I'll definitely do it if no one can take this thread any further.

---

### Post by max.diems on 2006-10-06
You may want to try XFCE. It's the [FONT=Courier New]xubuntu-desktop[/FONT] package.

---

### Post by max.diems on 2006-10-06
Heh. My 35th post is the 35th post in this thread.

---

### Post by ricardisimo on 2006-10-06
> **max.diems said:**
> You may want to try XFCE. It's the [FONT=Courier New]xubuntu-desktop[/FONT] package.

You mean start over? Get rid of Ubuntu and load Xubuntu? I'm hoping it won't come to this.

---

### Post by gn2 on 2006-10-06
> **ricardisimo said:**
>  if a small hammer won't work, use a bigger hammer

Is that what we domestic precision engineers call a reciprocating tolerance adjuster?

Also if it's really big can be used as a universal key...

---

### Post by max.diems on 2006-10-06
But I am just puhing my favorite WM here.

---

### Post by podunk on 2006-10-06
Have you ever considered buying a new video card? 

I've been following your epic for quite some time now, and sadly I don't know enough to help.

I have an old Nvidia card with 64 megs of ram and it returns a gklxgears of upper 800.

Taking a quick look at Tiger Direct I see 64 meg Nvidia AGP cards starting at 25 bucks.

Don't buy ATI - they don't support us much better than SiS does.

---

### Post by ricardisimo on 2006-10-06
> **podunk said:**
> Have you ever considered buying a new video card? 

I've been following your epic for quite some time now, and sadly I don't know enough to help.

I have an old Nvidia card with 64 megs of ram and it returns a gklxgears of upper 800.

Taking a quick look at Tiger Direct I see 64 meg Nvidia AGP cards starting at 25 bucks.

Don't buy ATI - they don't support us much better than SiS does.

Sadly, I suspect that you're absolutely right. It's just that, I don't know about you, but when I first heard about Gnu-Linux, there was this aura about it, that somehow it could salvage even your old TI-99s and Colecos from the 80's. OK, maybe not that much, but the key was not having to buy a new comp or new equipment every year. I was hoping to avoid this, but you're absolutely right... it's all of $20-$30. Thanks.

---

### Post by podunk on 2006-10-07
I understand – I felt the same way about my ATI card. I bought the card to go in a Win 98 machine (up until July this was my preferred OS, but MS dropped support) and it was buggy as heck. It was hard to set up, several of my favorite games would corrupt the screen when I exited them and the only way to get it back was reboot.

Worked perfectly in XP. My XP went much faster with that card. Which of course did me no good – I hate XP – it's so slow as to be painful. So I stuck it back in the box and put my old card back in.

I installed the card back before I set up Ubuntu – and turned into a pain in the burro here to.

It's a good card – the company that makes it is however focused on a very narrow (but large, very very large) market. If you're not in that market you can just eat some grits or something.

You can have a great piece of hardware – but if the company that makes it refuses to support your platform you're out of luck. On the other hand a mediocre piece of equipment from a company willing to optimize it for a platform can work very well.

I'll bet you a cup of mocha java Ubuntu that if you stick a Nvidia card in your machine you'll be amazed at how much better it runs – in both Windows and Linux. Plus if you don't think Linux is faster than XP then I'll spring for whipped cream too. :-)

---

### Post by ricardisimo on 2006-10-07
> **podunk said:**
> I understand – I felt the same way about my ATI card. I bought the card to go in a Win 98 machine (up until July this was my preferred OS, but MS dropped support) and it was buggy as heck. It was hard to set up, several of my favorite games would corrupt the screen when I exited them and the only way to get it back was reboot.

Worked perfectly in XP. My XP went much faster with that card. Which of course did me no good – I hate XP – it's so slow as to be painful. So I stuck it back in the box and put my old card back in.

I installed the card back before I set up Ubuntu – and turned into a pain in the burro here to.

It's a good card – the company that makes it is however focused on a very narrow (but large, very very large) market. If you're not in that market you can just eat some grits or something.

You can have a great piece of hardware – but if the company that makes it refuses to support your platform you're out of luck. On the other hand a mediocre piece of equipment from a company willing to optimize it for a platform can work very well.

I'll bet you a cup of mocha java Ubuntu that if you stick a Nvidia card in your machine you'll be amazed at how much better it runs – in both Windows and Linux. Plus if you don't think Linux is faster than XP then I'll spring for whipped cream too. :-)

Mmmm... Frapubuntuccino!... with whipped cream, no less! Sweet elixir of life... I'll let everyone know how the new card works once it's in. Thanks for trying, everybody.

---

### Post by ithaka on 2006-10-08
Hi,


As requested it ran the glxgears with the following results

829 frames in 5.8 seconds = 143.950 FPS
791 frames in 5.4 seconds = 146.132 FPS
798 frames in 5.4 seconds = 147.060 FPS
798 frames in 5.4 seconds = 146.903 FPS
798 frames in 5.4 seconds = 146.751 FPS
798 frames in 5.4 seconds = 147.088 FPS
798 frames in 5.4 seconds = 146.921 FPS
798 frames in 5.4 seconds = 146.947 FPS
798 frames in 5.3 seconds = 150.856 FPS
798 frames in 5.4 seconds = 146.871 FPS
798 frames in 5.4 seconds = 146.930 FPS

One remark though, the gears were displayed very bad, like 0.5-1 frames per second, is this normal? I would think with 143fps they would move normally.


Olivier

---

### Post by podunk on 2006-10-09
That's *very* slow. I see from a previous post you have an AGP Nvidia, it should run faster than that. Have you installed the Nvidia drivers?

I followed the guide on this page for mine:
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

The command
```
glxinfo
```

should have this close to the top of the gobblygook:
direct rendering: Yes

when your card is set up right.

Welcome to Ubuntu. :-)

---

### Post by ithaka on 2006-10-09
After install I ran a dpkg-reconfigure xserver-xorg to get better resolution.
The wizard recognized my chipset so I reckon it installs the correct drivers.
Perhaps I get something wrong over there, but when not sure I leave the default value. 

However, thanks for the link. I will try some of the stuff I find on the page this evening.

Will post my findings...

---

### Post by gn2 on 2006-10-09
Always been curious about Frames Per Second...

Surely the limiting factor is the screen refresh rate, if the screen only updates at 60hz-85hz (in most cases) what is the relevance of a FPS above that?

Maybe I'm missing something......

---

### Post by ithaka on 2006-10-09
Apparently the correct drivers were indeed not installed yet. Everything looks better and is waaaay faster. Thanks for the excellent help!

---

### Post by shivam on 2006-10-09
well i think that the DMA can also cause this kind of problem.
check your DMA status with

$ sudo hdparm /dev/hda

if you get a line with "using_dma    =  1 (on)"
then your DMA is on else you might get a 0 (off)

the mouse must be giving very pathetic performance when you must be copying big files if DMA is the problem

also you can try

$ sudo hdparm -tT /dev/hda

this will give u the data transfer rates
for the hdd it must be around 50 MB/s

---

### Post by srt4play on 2006-10-10
> **shivam said:**
> 
also you can try

$ sudo hdparm -tT /dev/hda

this will give u the data transfer rates
for the hdd it must be around 50 MB/s

You make it sound like if you don't get 50MB/s hard disk transfer rate then everything will be slow, which is obviously untrue.  I had a crappy hard drive once that transferred only 10MB/s but the machine was still very usable.

---

### Post by shivam on 2006-10-10
well if the DMA is off then the hdd will give performance of the order of 2.5 to 3 MB/s and that will sure affect the usability of the system i guess. 
try to turn off the dma of ur system and see the changes.

---

### Post by ricardisimo on 2006-10-10
> **podunk said:**
> I'll bet you a cup of mocha java Ubuntu that if you stick a Nvidia card in your machine you'll be amazed at how much better it runs – in both Windows and Linux. Plus if you don't think Linux is faster than XP then I'll spring for whipped cream too. :-)

Well, I broke down and bought the new card. Unfortunately, here I was expecting to just pop it in and be done with it... but like so much of my Ubuntu experience, it's just not meant to be that easy. So here I am asking for pity and help again...

I've got an nVIDIA 64M GeForce MX4000 T64/T32 AGP VGA card. When it's plugged in on startup, I get a failure to start the X Server, with overlapping prompts: a blue screen asking if I want X Server to diagnose the problem, as well as an ID and password prompt. What should I be seeing, and how should I proceed? Thanks.

---

### Post by RanDinCarolina on 2006-10-10
I think all that is saying is that the correct drivers aren't loaded. You probably don't have the "nv" driver loaded so log in and do 

```
dpkg-reconfigure xserver-xorg
```

When asked for the driver scroll up or down until you see the "nv". That's the basic nVidia driver. Select it, then finish the rest of the configuration. 

Once you finish either reboot or CTL+ALT+BKSP.

If you get graphics, then use synaptic and get the "good stuff". You'll need either nvidia-glx-legacy or nvidia-glx and the restricted modules. 
I think that will set you up....if not check the nvidia threads, they have all the info you will need.

---


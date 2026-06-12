---
title: "X Server problem"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by snellbag on 2006-08-12
My Ubuntu has suddenly decided on startup to show this error:

"[COLOR="Red"]Could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected[/COLOR]"

Can someone please help me?

---

### Post by MikeMLP on 2006-08-12
post a copy of your /etc/X11/xorg.conf file (you can edit it by entering the following once you have logged in with a Ubuntu live CD:
```
sudo gedit /etc/X11/xorg.conf
```

I have also edited my xorg.conf file from my windows XP partition using this to access my linux partition from within windows:[http://www.fs-driver.org/]("http://www.fs-driver.org/")
Which is useful if you dual boot and can't stand the speed of the liveCD

Alternatively, you can troubleshoot yourself:
If I recall correctly, the error that pops up gives you the option of looking at a log file.  Take a look at that and see where it tells you it is having a problem (most likely somewhere within the xorg.conf file.  Posting the gist of what it says here will also help us find out where in the xorg.conf file your machine is getting messed up.  After the error, you should be dumped to a text login where, after logging in, you can use the command:

```
sudo vi /etc/X11/xorg.conf
```
This edits your xorg.conf file using the vi text editor (a basic text editor that can be run within the terminal).  It uses hotkeys, so it is best to read some documentation if you've never used it before: [http://www.comptechdoc.org/os/linux/usersguide/linux_ugvi.html]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugvi.html")
The two commands you'll need are the "i" key to enter text input mode (allows you to type text) and the :wq command which saves, and then quits. (first hit escape to get out of text input mode)

HOWEVER:  if you are completely new to this, you'd probably apreciate someone to walk you through the process first, so, unless you feel absolutely comfortable troubleshooting yourself, start by posting a copy of the xorg.conf file here, so we can take a look at it.

Edit:  There also may be older (working) versions of the xorg.conf file in your /etc/X11 folder, probably named xorg.conf."something" (where "something" can be any combination of letters and numbers) that can be used to replace your non-working copy of xorg.conf.

The bad news: it is a little tiny bit complicated to troubleshoot this problem
The good news: it happens every once in a while, and is usually pretty easy to get GDM back.

---

### Post by snellbag on 2006-08-12
this is the dump of /etc/X11/xorg.conf:
"Files"
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
	Identifier	"Trident Microsystems CyberBlade/i7"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems CyberBlade/i7"
	Monitor		"Generic Monitor"
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

---

### Post by PriceChild on 2006-08-12
> **MikeMLP said:**
> ```
sudo gedit /etc/X11/xorg.conf
```

You really should use gksudo there.

---

### Post by MikeMLP on 2006-08-12
Just a shot in the dark:  Were you using ATI or Nvidia drivers prior to this happening?  The reason I ask is because it looks like  you have DRI enabled, but no proprietary driver specified.  
Perhaps you were using opensource drivers?  

Was there anything that you were doing prior to this, like upgrading the kernel, or switching window managers, trying to get graphics drivers running, or configuring input devices?  In other words, can you think of anything that may have caused this?

Also, when you start up, on the screen when it says that it can't start X, there should be a way to view a log file, which will tell you exactly what lines of the xorg.conf file X is getting messed up at.  You may be able to find out what section is giving you your problem by looking at that.  Perhaps some other users may be able to see something just by looking at the xorg.conf text you've entered here as well.

Out of curiousity, what is Trident Microsystems Cyberblade?  is that some sort of network card or vid card?  I've never heard of that brand/make before.  Thanks

---

### Post by MikeMLP on 2006-08-12
oh and one more thing:  are you sure this is the entire dump?  it looks like there are some things missing at the beginning.  At the very least, there should be the word Section before "Files" at the beginning, just like there is the word Section before the word "Module" in the next section.  Depending upon your video setup, there may need to be a "Server Layout" section before the "Files" section as well.  I'm sure more experienced users will be able to jump in here as well.

Edit: nevermind, I see the "Server Layout" section now, it is near the end of the file.  The question about having the word Section before "Files" at the beginning still stands though.

---

### Post by snellbag on 2006-08-12
I was originally trying to get my hard drives mounted. I think Trident Microsystems was a crappy vid card supplied by the pc company (TIME, lol). It told me to view the syslog, but I don't know how to...

---

### Post by snellbag on 2006-08-12
sorry, yeah i missed out the beginning of the file

---

### Post by MikeMLP on 2006-08-12
@ PriceChild
Thank you for the tip, I wasn't aware of that.  For a discussion on gksudo versus sudo, check here: [http://psychocats.net/ubuntu/graphicalsudo.php]("http://psychocats.net/ubuntu/graphicalsudo.php")
PriceChild, if you have any other links that talk about the proper usage of gksudo and the dangers of sudo, please post them.  I realize that this is OT, however for people searching the posts (especially newbies) this is an excellent point to be made, and since it was brought up here, there ought to be enough information here for users to understand why they should use gksudo... now back to the situation at hand...

---

### Post by MikeMLP on 2006-08-12
you can view the syslog from the terminal using:

```
 more /var/log/messages 
```

This may also show why the X-server couldn't start (I'm not sure, I've always viewed the log directly from the message that pops up when my X-server won't start, so I'm not entirely sure if you'd be looking at the same log file, again, I'm sure a more experienced user will pop in here soon to confirm or refute this).  You may find some pertinent information here though.  It will be chronologically ordered so you can see what was going on within the system at the time of the bootup.

---


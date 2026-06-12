---
title: "screen resolution"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by camdy on 2007-02-24
hi how do i change the resolution in Ubuntu 6.10 64AMD desktop i only have 800 x 600 & 640 x 480 i need it to be 1280 x 1024

---

### Post by Jussi01 on 2007-02-24
Go to terminal (Applications - Accessories - terminal) and type:
```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by louis_nichols on 2007-02-24
You need to edit the file /etc/X11/xorg.conf.

Make sure you back it up first: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then open it for editing: ```
gksudo gedit /etc/X11/xorg.conf
```
Towards the end of the file you will find several blocks that look like this: ```
Subsection "Display"
        Depth       16
        Modes       "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
```
Those 800x600 things are the available resolutions. You need to add to those lines your desired resolution. Something like this: ```
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        
```
Then you logout and press CTRL+ALT+Backspace to restart the X server and, when logging in again, you should be able to select the other resolutions too.

---

### Post by lodravah on 2007-02-24
I'm gonna try this too, but just a quick question. If I should mess up X, how do I reconfigure it if it won't start afterwards?

---

### Post by louis_nichols on 2007-02-24
If you only edit the xorg.conf file, then you just restore it afterwads. So if you restart and all you get is a black screen with a login prompt, you login there and type:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
The dpkg-reconfigure solution presents no risks and is actually worth trying first. But is is possible that it will just make the same configuration it made the first time.

---

### Post by FyreBrand on 2007-02-24
> **lodravah said:**
> I'm gonna try this too, but just a quick question. If I should mess up X, how do I reconfigure it if it won't start afterwards?

First make a backup copy of your current xorg.conf file.  From the terminal:
```
cd ~
cp /etc/X11/xorg.conf xorg.conf.orginal
```
That will move you to your home directory and make a backup copy of your xorg.conf file.  That way if you hose it up you can restore it by:
```
cd ~
sudo cp xorg.conf.original /etc/X11/xorg.conf
```

If you really hose it up and didn't make a backup of the file then you can reconfigure it with this command (again from the terminal):
```
dpkg-reconfigure -phigh xserver-xorg
```

A good idea might be to do a forum search on the type of video card you have and see how other people have installed and configured drivers for your card.  The kind of problem you're having sometimes can be solved by installing (or reinstalling) and configuring the proper video drivers.

---

### Post by Meson on 2007-02-24
I'm trying to add "1680x1050" to xorg.conf  There are a number of different levels between 0 and 24... do I add it to each one?

---

### Post by Quillz on 2007-02-24
You'll need a video driver. If you have ATI, go for fglrx.

---

### Post by camdy on 2007-02-24
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Package `xserver.xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver.xorg is not installed


hi i tried & this is what has come up if i understand it right i don't have xserver.xorg intsalled

---

### Post by igknighted on 2007-02-24
its xserver-xorg, not xserver.xorg

---

### Post by igknighted on 2007-02-24
> **Meson said:**
> I'm trying to add "1680x1050" to xorg.conf  There are a number of different levels between 0 and 24... do I add it to each one?

No, there should be a line that says "defaut 24" or something like that, whatever the number after default is, just add it to that level.

---

### Post by camdy on 2007-02-24
thanks :lolflag:  ok now it use kernel framebuffer device interface? what do i type in here?

---

### Post by lodravah on 2007-02-24
This is what  my xorg.conf looks like in Edgy. I tried adding "1280x1024" behind "1024x768" in all rows, but nothing happened. Any ideas?

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

---

### Post by igknighted on 2007-02-24
> **lodravah said:**
> This is what  my xorg.conf looks like in Edgy. I tried adding "1280x1024" behind "1024x768" in all rows, but nothing happened. Any ideas?

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

What driver are you using?  Did you install the drivers for your ATI card, or are you using the stock drivers?  If you haven't installed the drivers, install the package "xorg-driver-fglrx" from synaptic and then run the command "aticonfig --initial" in the terminal.

EDIT: For future reference, when putting a file like that up use code tags so it doesn't take up so much space

---

### Post by igknighted on 2007-02-24
> **camdy said:**
> thanks :lolflag:  ok now it use kernel framebuffer device interface? what do i type in here?

You could enable it, shouldn't hurt.  I usually don't.  I haven't had an issue either way yet.

---


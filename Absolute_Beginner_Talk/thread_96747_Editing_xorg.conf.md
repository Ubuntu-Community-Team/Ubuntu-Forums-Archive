---
title: "Editing xorg.conf"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by niallabrown on 2005-11-29
Hi,

Real nubie here.  I have a Acer AL2032W A with a native rez of 1680X1050

I did mangage to pull up the X11 menu by entering: sudo gedit /etc/xorg.conf (suppried I got this far)

These are the tech specs for the monitor:
[http://www.acerpanam.com/synapse/forms/portal.cfm?recordid=258&formid=3404&website=AcerPanAm.com/canada&originwebsite=AcerPanAm.com&central=1&words=all&keywords=&pupv=pu]("http://www.acerpanam.com/synapse/forms/portal.cfm?recordid=258&formid=3404&website=AcerPanAm.com/canada&originwebsite=AcerPanAm.com&central=1&words=all&keywords=&pupv=pu")****

What do I need to do to this file?

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"Acer MFM DVI"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


```

(there is more to this file if you need it)

Thanks for your time!

Niall

---

### Post by zaphod_es on 2005-11-29
You might do better reposting your message with the correct subject xorg.conf.  I skipped your message thinking that it was some strange app I had never heard of.

Sorry, I cannot answer your question; it is a pig to sort out xorg.conf

ZB

---

### Post by aysiu on 2005-11-29
[QUOTE=niallabrown]
What do I need to do to this file?[/QUOTE] You will find the answer [here](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by mo_x on 2005-11-29
You could try the following:
In the Monitor section of your xorg.conf put the line:
```
VertRefresh	75
```
and replace the Modes lines with
```
Modes "1680x1050"
```
Make a backup of your xorg.conf first in case it doesn't work.
If it doesn't work you may need to create a modeline for this resolution, you should then post the file /var/log/Xorg.0.log and your complete xorg.conf.

---

### Post by niallabrown on 2005-11-29
Thanks for trying, but I think this is over my head. :confused:

---

### Post by mo_x on 2005-11-30
Do you want to give up already ](*,) 
If you post your /var/log/Xorg.0.log and /etc/X11/xorg.conf (as attachments, make a copy and change file extensions to txt) I can help you with the changes.

---

### Post by KermitJr on 2005-12-01
I was having trouble with several older video cards and a particular monitor and kept getting 640x480 no matter what I did for modes, etc.  

HOWEVER, when I went back one time and ran
```
sudo dpkg-reconfigure xserver-xorg
```
This is the easy way to edit xorg.

I entered the actually amount of RAM on the video card (one was 4096 and another 2048) and PRESTO! My Modes line worked as normal with or without monitor on boot.  (Number of MB * 1024)

Log out and ctrl-alt-backspace to restart xserver.

So try entering in the actual video RAM you have and that should hopefully fix your error.

If not, troubleshoot by looking for the actual error messages in the /var/log/X11/xorg[tab].log file.

Hope this helps!
KermitJr

---

### Post by pointzero on 2007-10-31
This was the best fix.  Now much is automatically detected.

[http://forum.insanelymac.com/index.php?showtopic=45092&hl=al2032](http://forum.insanelymac.com/index.php?showtopic=45092&hl=al2032)

---


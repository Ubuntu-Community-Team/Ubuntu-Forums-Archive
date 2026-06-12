---
title: "I can't see!!!"
date: 2005-09-19
forum: Absolute Beginner Talk
---

### Post by bezzer on 2005-09-19
I have just installed hoary on my pc.  The installation seems to have gone ok (plenty of incomprehensible type moving up the screen).  At the end I assume it went into the window manager thing but my screen just went black and gave me the helpful message "no support".  When I hit the off button a command line login prompt appeared but not for long enough to log in before the computer powered down.

Any helpful ideas???

Thanks
D

---

### Post by SilentCacophony on 2005-09-19
You might need to be more specific in order to get any help. Sounds like it may be a hardware problem to me. Listing your hardware (including graphics card) might let someone who's had a similar problem recognise it better.

---

### Post by bezzer on 2005-09-19
Fair point!

OK, so I loaded winxp and found out that my graphics card is a RAGE 128 Pro Ultra GL AGP.

Searched the forums for help, but to be honest as a newbie went right over my head.

can go Ctrl+Alt+F1 and get a terminal, even tried running sudo dpkg-reconfigure xserver-xconf and I think I answered the questions right, but still don't work.

I can't paste any logs because I don't know how and i'm having to log into windows to get net and ask questions anyway.

Anybody able to help?

Thanks
D

---

### Post by matthew on 2005-09-19
A couple of followup questions/ideas:

1) it sounds like everything is working perfectly in Windows, is that correct? If so, then we can eliminate hardware failure.

2&3) Are you sure you have the right version of Ubuntu? What is your computer's processor type? i.e. Pentium 4, AMD 64, etc. It is possible that you have accidentally tried to install a version of Ubuntu intended for a different processor, like maybe the mac PowerPC version on your Intel box, etc.

It may be something other than this, but I like to try to eliminate the more obvious/silly problems first since I tend to make them often and then try to come up with some elegant and complicated, but unnecessary solution.

---

### Post by xmastree on 2005-09-19
[QUOTE=bezzer] At the end I assume it went into the window manager thing but my screen just went black and gave me the helpful message "no support".[/QUOTE]Try it again, and this time, once it's stopped, press Ctrl-Alt F1, log in and do: ```
sudo killall gdm
```That should stop the desktop manager. Then type ```
startx
``` and see what happens. You might be able to see some errors listed.

Or...
It could be simply that it's trying to run your screen at too high a resolution. press Ctr-Alt-minus (on the numerical keypad, right edge) to switch to a different resolution. If that works, you will need to dig around in your xorg.conf file to lower the default setting a little.

> I can't paste any logs because I don't know how and i'm having to log into windows to get net and ask questions anyway.Is your windows disk FAT32? You could mount it from a terminal, and copy files to it from there if you need to.
```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000
cp /etc/X11/xorg.conf /media/windows/
```And xorg.cong will then appear in c:\

---

### Post by bezzer on 2005-09-20
@ matthew
Yep, everything works great in windows and I'm pretty certain I've got the right Ubuntu (the x86 version and my pc has an AMD Duron processor).  I can get a working terminal, just not any kind of graphics stuff. 

@xmastree
At work now, but will try when I get home tonight and post any results here.

Thanks for the help so far guys.

D

---

### Post by bezzer on 2005-09-20
Hooray!

Ctrl-Alt - worked and I think it;s ok now.

Thanks for the advice!

D

---

### Post by xmastree on 2005-09-20
Ctrl-Alt - or + will cycle through the available modes. If one of those appears blank then your monitor can't support it and you need to remove that one from your xorg.conf

---

### Post by bezzer on 2005-09-21
How do I do that?  Now I have to push Ctrl-Alt - four times at start up to get the login screes (else I just get a blank screen).  Then when it does work, the desktop is too big for the screen and I have to scroll up to get the menus etc.  If I go to the Screen Resolution option and change it to 1024*768 at a refresh rate of 70Hz it's fine.  But even though I've ticked the "make default" box it still resets everytime I turn my pc on.

If I need to change my xorg.conf, I need some step by step instructions 'cos I would find that quite scary!

Thanks
D

---

### Post by xmastree on 2005-09-21
[QUOTE=bezzer]If I need to change my xorg.conf, I need some step by step instructions 'cos I would find that quite scary![/QUOTE]
First back up the existing one.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```Then edit the active one```
sudo gedit /etc/X11/xorg.conf
```Look for this bit:
```
SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
``` and remove any reference to any modes you don't want to use so that each subsection looks like this:
```
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
EndSubSection
```Then log out, and restart x by pressing Ctrl-Alt-Backspace.

If you got it right, you should be up and running. Worst case, x won't start in which case you login from a different terminal, and restore your backup file.
```
sudo cp /etc/X11/xorg.conf.back /etc/X11/xorg.conf
```

Good luck!

---


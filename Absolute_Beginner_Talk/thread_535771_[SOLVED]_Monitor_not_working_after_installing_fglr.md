---
title: "[SOLVED] Monitor not working after installing fglrx"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by NovaAesa on 2007-08-26
After installing fglrx (following this [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)), my monitor doesn't work. When I boot up the monitor displays "Out of Range 75.0KHz / 60Hz."

Thank you to anyone who can help.

EDIT: I'm using a 17' LCD monitor with a native resolution of 1280x1024 and a Radeon X800XL

---

### Post by bdoe on 2007-08-26
Could you boot into safe mode and post your /etc/X11/xorg.conf file?

---

### Post by NovaAesa on 2007-08-26
I've booted in recovery mode (and got the console/terminal), but I'm not really sure how to use it to get the contents of the file. What should I type in there?

---

### Post by NovaAesa on 2007-08-27
Ok, I used the shell to examine the file and this is what I got:

[A whole heaps of instructions, I think they are commented out with #]
Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice " "stylus" "SendCoreEvents"
InputDevice " "cursor" "SendCoreEvents"
InputDevice " "eraser" "SendCoreEvents"

Any ideas anyone?

---

### Post by mysticmatrix on 2007-08-27
> **NovaAesa said:**
> After installing fglrx (following this [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)), my monitor doesn't work. When I boot up the monitor displays "Out of Range 75.0KHz / 60Hz."

Thank you to anyone who can help.

EDIT: I'm using a 17' LCD monitor with a native resolution of 1280x1024 and a Radeon X800XL

This happens if your computer hasn't recognized correct frequency of your monitor.
Try googling "<name of your monitor> specs". This will probably tell you what are Horizontal and vertical sync rates of your monitor.

Having that knowledge, boot into safe mode and type
```

sudo nano /etc/X11/xorg.conf
```

Then edit this section

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	[COLOR="Red"]28-64[/COLOR]
	VertRefresh	[COLOR="Red"]43-60[/COLOR]
EndSection

```

You should change the values marked in red by value of your monitor. If those line are not there, just type them in with correct values. BTW, 28-64 is for my monitor, and yours would be something else.

After this, save the file and exit and reboot. If you still face trouble, reply back

Cheers

---

### Post by NovaAesa on 2007-08-27
It's still not working. My monitor is a LG Flatron L1750SQ

The values I found from googling are:
Horizontal 30-83kHz
Vertical 56-75Hz

So I changed the numbers to 30.0 - 83.0 and 56.0 - 75.0

---

### Post by NovaAesa on 2007-08-27
After looking at the file again I noticed that there are two sections called "Monitor"

There is another one below the first.This second section is as follows:

Section "Monitor"
   Identifier "aticonfig-Monitor[0]"
  Option  "VendorName" "ATI Proprietary Driver"
  Option "ModelName" "Generic Autodectecting Monitor"
  Option "DPMS" "true"
EndSection

Should the two sections be merged together or something?

---

### Post by SpiritIsReality on 2007-08-27
howdy

could you try typing at the command prompt
sudo dpkg-reconfigure xserver-xorg
press enter
answer the questions best you can, the defaults are usually right,
so usually just press enter to accept default answer.
when you get to the advanced, medium, simple, for the monitor,
you could choose advanced, and type in your monitor's rates.
when done, type
sudo shutdown -r now
press enter
to restart your rig. 
should be back in the saddle.
hope all goes well.

[http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com%2Fcommunity+monitor+resolution&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com%2Fcommunity+monitor+resolution&btnG=Search&meta=)
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)
[http://ubuntuforums.org/showthread.php?t=484846&highlight=free+books](http://ubuntuforums.org/showthread.php?t=484846&highlight=free+books)

trails

---

### Post by NovaAesa on 2007-08-27
That got it working - thanks mate!

---

### Post by SpiritIsReality on 2007-08-27
OK
good news
now, what I see suggested here,
is to log in, click on thread tools,
click on 
mark this thread solved...
you're in the saddle

trails

---


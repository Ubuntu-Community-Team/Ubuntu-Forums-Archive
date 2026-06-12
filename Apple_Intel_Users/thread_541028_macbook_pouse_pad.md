---
title: "macbook pouse pad"
date: 2007-09-02
forum: Apple Intel Users
---

### Post by constantgamer247 on 2007-09-02
im extremely new to linux. I just got my 1.83 Ghz intel core duo (not core 2 duo its the old core duo) macbook to dual boot mac and linux. now i have a few questions. how can i get the mouse to work exactly like in osx. I want to be able to 2 finger scroll and click. Also when I turned up the sensitivity the mouse did not speed up.

i was told to "sudo apt-get install qsynaptics" in terminal and i did and a lot of stuff apeared.  I think it worked. When I click system and then preferences thier is a new option called touch pad.  when i click it I get 

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

please help.  This USB mouse sucks.

---

### Post by czechman86 on 2007-09-02
Hey amigo!

okay, i had the same questions as you almost. i dont remember exactly what i did, but i followed the instructions in this guide:

[http://ubuntuforums.org/showthread.php?t=493758]("http://ubuntuforums.org/showthread.php?t=493758")

i hope that this helps!

---

### Post by constantgamer247 on 2007-09-02
can u please explain because that makes no sence to me

---

### Post by czechman86 on 2007-09-03
> can u please explain because that makes no sence to me

No problem at all (although I am very new to Linux too, so I do apologize if this does not make sense). The first thing that I need you to do is open up your terminal and type the following or copy and paste the following code:

```
sudo gedit /etc/X11/xorg.conf
```

You will be prompted for your password. After that, a new window will open in a basic text editor and it will display your Xorg file. Go to the text editor window and scroll down and look for a section that looks similar to this:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"TouchpadOff"		"2"
EndSection
```

If you do see a section that looks similar to this, then please post it in your next reply. If you do not, then please inform me, and from there, we will move forward. Please do not expect yours to look exactly like mine, for I have done some tweaking.

I hope this made sense, and look forward to moving to the next step! :)

Thank you to: benanzo for his [guide]("http://ubuntuforums.org/showthread.php?t=493758") and the help it provided me in providing technical help.

---

### Post by themacmonk on 2007-09-05
I tried this and it works!  You just have to get use to using text to change some things around.  You'll get use to it.  I'm new to Ubuntu as well and that was the first thing I did. I'm using a first generation MacBook.  I haven't gotten it to behave the same as on MAC but it's pretty close.

One thing I'm wondering if anyone knows how to do is to tweak the "two finger" scroll.  For example, when trying to scroll in a window I have to put both fingers on the pad simultaneously to enable the window scroll feature, if I don't the mouse jumps to a different corner of the screen.  On OS X you can be using one finger then add the second and it will scroll and not make the mouse jump to where your second finger landed.

No big deal, but just something I noticed when first trying it out. I'm liking Ubuntu so far!

---

### Post by cyberdork33 on 2007-09-05
> **themacmonk said:**
> One thing I'm wondering if anyone knows how to do is to tweak the "two finger" scroll.  For example, when trying to scroll in a window I have to put both fingers on the pad simultaneously to enable the window scroll feature, if I don't the mouse jumps to a different corner of the screen.  On OS X you can be using one finger then add the second and it will scroll and not make the mouse jump to where your second finger landed.

I really doubt that there is a way to do that. the cursor is probably actually jumping to a point 'between' both your fingers (the calculated point if all the pressure on the pad were concentrated at one point in the middle). This is normal PC touchpad behavior, and probably what was mimicked.

---

### Post by themacmonk on 2007-09-05
Thanks for the insight!  On a related topic (maybe), I noticed that the touch pad is supersensitive to the point where if I'm in a media player such as mPlayer, that when I bump the laptop or even put a cup of coffee down next to it, the song or movie will skip forward or backwards.  I'm assuming the touchpad is picking up the vibrations?

Thanks again!

---

### Post by cyberdork33 on 2007-09-05
> **themacmonk said:**
> Thanks for the insight!  On a related topic (maybe), I noticed that the touch pad is supersensitive to the point where if I'm in a media player such as mPlayer, that when I bump the laptop or even put a cup of coffee down next to it, the song or movie will skip forward or backwards.  I'm assuming the touchpad is picking up the vibrations?

Thanks again!
That almost sounds more like the accelerometer affecting things (although I have not heard that before...). You can adjust the senitivity of the touchpad by editting the options in your xorg.conf file. You can read what all the specific options do in the man pages:```
man synaptics
``` Read specifically the Finger High / Finger Low options.

---

### Post by themacmonk on 2007-09-05
Perfect, 

Thanks!

---


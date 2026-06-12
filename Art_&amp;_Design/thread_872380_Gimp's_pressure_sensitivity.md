---
title: "Gimp's pressure sensitivity"
date: 2008-07-27
forum: Art &amp; Design
---

### Post by Stoodle on 2008-07-27
It seems that the Gimp isn't registering pressure. What should I do?

---

### Post by eilu on 2008-07-28
Don't think it's enabled by default, try checking under preferences> input devices or check the tool- there's a little dropdown for pressure sensitivity, the default in mine is pressure sensitivity = opacity for the brush. (don't have a tablet, can't test atm)

---

### Post by lyceum on 2008-07-28
> **eilu said:**
> Don't think it's enabled by default, try checking under preferences> input devices or check the tool- there's a little dropdown for pressure sensitivity, the default in mine is pressure sensitivity = opacity for the brush. (don't have a tablet, can't test atm)

Mine stay stuck on "none" it will not let me re-set. :(

---

### Post by Stoodle on 2008-07-28
I don't have anything that says input devices. Not really sure how to change it in terminal either. The "presscurve" settings don't make sense.

---

### Post by lyceum on 2008-07-28
> **Stoodle said:**
> I don't have anything that says input devices. Not really sure how to change it in terminal either. The "presscurve" settings don't make sense.

on the main GIMP panel: File/Input devises/Device then select touch pad from the drop down menu

---

### Post by Stoodle on 2008-07-28
Yeah I saw it. However, I can set pressure sensitivity and it's defaulted on 3 but I don't think that putting it one way or another on the bar changes it. Not on that computer right now though.

---

### Post by Stoodle on 2008-07-28
Oh hey, I got it to work. I had it set to disabled, and then set it to Screen. What's the difference between window and screen?

Also, I don't get much space on my tablet. It maps the whole screen to a small section starting from the top left. I have a Bamboo Fun.

Last, when I was use wacomcpl, let's say I go to tablet and choose tablet controls. What do the buttons mean such as left, right, middle, fourth, fifth, ignore, and key stroke? What do buttons 1, 2, 3, and 4 correspond to?

---

### Post by lyceum on 2008-07-28
> **Stoodle said:**
> Oh hey, I got it to work. I had it set to disabled, and then set it to Screen. What's the difference between window and screen?

Also, I don't get much space on my tablet. It maps the whole screen to a small section starting from the top left. I have a Bamboo Fun.

Last, when I was use wacomcpl, let's say I go to tablet and choose tablet controls. What do the buttons mean such as left, right, middle, fourth, fifth, ignore, and key stroke? What do buttons 1, 2, 3, and 4 correspond to?

You got further than i did. Mine keeps going back to disabled.

---

### Post by VeeDubb on 2008-07-29
The difference between "screen" and windows is that with "screen" your configured device covers the whole screen.  With "window" it ties the dimensions of your tablet to the image you're working on.

If you're using a mouse and tablet combined, "window" may work better, but it requires you to make some changes to the configuration of the devices in your xorg.conf

Unfortunately, it's been so long since I've done that on any distro, that even if I remembered how, the configuration options would have changed by now.

For the one getting stuck, be sure you're selecting the stylus in the "configure extended input devices" dialog.  If it's still looking at the mouse, pressure sensitivity will not work, and the options will probably be locked out.  Gimp is nice in the sense that it lets you configure each device separately.

---

### Post by YoungCthulhu on 2008-08-31
Hi,

I was having similar problems with my CTE-640 tablet, and looked up PressCurve mentioned by Stoodle above, as I had never seen the thing before. 

I found it mentioned by the Linux Wacom Project via Google ([http://linuxwacom.sourceforge.net/index.php/howto]("http://linuxwacom.sourceforge.net/index.php/howto") and read about a tool called xsetwacom, that seems to automate all the messing around.  I tried to download it using Synaptic and sudo apt-get install etc etc but could find no sign of it.  Perhaps I am not looking in the right repositories :confused:

Anyway, I printed out their great "HowTo" for xsetwacom and found that it seems to create an entry in /etc/X11/xorg.conf.  I tried it and it worked! Then I messed around a bit and ended up with a pressure sensitivity curve that suits me.  Here's the relevant part of my /etc/X11/xorg.conf 
> Section "InputDevice"
        Driver          "wacom"
        Identifier      "pad"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "pad"
        Option          "PressCurve"    "0,5,10,20,30,40,60,80,100"
        Option          "USB"           "on"
EndSection

I added the PressCurve line using vim editor.  If you are new to hacking, as I am, be sure to make a copy of your xorg.conf file before you do eg:
> stuart@GORT:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.omigodivstuffeditup  :lolflag:

As you can see, I like lots of control over fine shading effects, being a bit of a pencil fanatic before I discovered GIMP :)

Cheers, and good luck!!

---

### Post by Stoodle on 2008-08-31
I had it working just by having it updated. Now, my tablet isn't working again after an update. I think it was something to do with the linux header updates or something.

---

### Post by neota on 2008-08-31
> **YoungCthulhu said:**
> Hi,

I was having similar problems with my CTE-640 tablet, and looked up PressCurve mentioned by Stoodle above, as I had never seen the thing before. 

I found it mentioned by the Linux Wacom Project via Google ([http://linuxwacom.sourceforge.net/index.php/howto]("http://linuxwacom.sourceforge.net/index.php/howto") and read about a tool called xsetwacom, that seems to automate all the messing around.  I tried to download it using Synaptic and sudo apt-get install etc etc but could find no sign of it.  Perhaps I am not looking in the right repositories :confused:

Anyway, I printed out their great "HowTo" for xsetwacom and found that it seems to create an entry in /etc/X11/xorg.conf.  I tried it and it worked! Then I messed around a bit and ended up with a pressure sensitivity curve that suits me.  

"I don't think that means what you think it means."
The PressCurve setting is not arbitrary length.. It's fixed at 4 points.

for example:

75 0 100 25  is a very sensitive curve (lots of difference in response between min and max pressure -> big variation in brush size). I like to use this as the default curve for stylus point

0 25 75 100  is a quite blunt curve which I use for my stylus eraser.


I suspect the wacom driver is doing something odd to your setting there.. "0,5,10,20,30,40,60,80,100"
It may have squashed it into '0, 20, 60,100'
or it may have chopped off the end like '0,5,10,20'
Anyway, no need to change it yet -- if you want to change it later you'll need to find out the curve it's actually using.

---

### Post by lyceum on 2008-08-31
Is there anything going on in the Ubuntu world to get this fixed, or will we just have to keep trying to fix our WACOM's ourselves?

---

### Post by neota on 2008-09-01
> **lyceum said:**
> Is there anything going on in the Ubuntu world to get this fixed, or will we just have to keep trying to fix our WACOM's ourselves?
Either 
a) your GTK+ is not compiled with XInput support (unlikely)
b) You don't have the drivers set up properly in X (most likely)
(for example, you simply don't have any entries for your stylus in xorg.conf; If that is the case, it will usually show up as a mouse instead; you NEED those entries)

Here is a sample, from my xorg.conf. 
it might look odd depending on the forum's disposition, but this won't effect whether it works.
```

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

```
And later, my 'ServerLayout' looks like
```

Section "ServerLayout"
	Identifier      "Default Layout"
        screen 0 "scr1" 0 0
#	Screen "screen1"
	InputDevice	"GKb"
	InputDevice	"CMo"
	InputDevice     "stylus"	"SendCoreEvents" # important line
	InputDevice     "cursor"	"SendCoreEvents" # important line
	InputDevice     "eraser"	"SendCoreEvents" # important line
EndSection

```

c) You have a very recent tablet (like Bamboo) which is only supported with very recent versions of linuxwacom. In this case you might need to enable unstable/testing repositories to get a recent version, or even compile and install linuxwacom yourself.

---


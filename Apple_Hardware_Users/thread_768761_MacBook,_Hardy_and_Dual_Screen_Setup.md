---
title: "MacBook, Hardy and Dual Screen Setup"
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by PartisanEntity on 2008-04-26
Does anyone have any experience with setting up an external monitor on the MacBook?

Right now, both displays are cloned. The external monitor has the correct resolution while the MacBooks display does not.

I would like to have two separate x screens. Do I just add the info to xorg.conf? Or is there are easier way?

---

### Post by daengbo on 2008-04-26
If you are running Hardy, you can go to System > Preferences > Screen Resolution and uncheck "Clone."

---

### Post by PartisanEntity on 2008-04-26
Clone is unchecked, yet the screens are still being cloned

---

### Post by bluefish86 on 2008-04-26
Screen Resolution doesn't work properly on my macbook.  To get dual head working, I had to run this command:

xrandr --output VGA --auto --below LVDS

Note that if you are using compiz, the macbook video card limits you to 2048x2048 maximum combined resolution (ie the internal 1280x800 display won't work right or left of a 1280x1024 external display, only above or below it).

To disable the external monitor, run this:
xrandr --output VGA --off

---

### Post by PartisanEntity on 2008-04-28
I still cannot get this to work, anyone have any other tips ?

---

### Post by bluefish86 on 2008-04-28
Sorry, I forgot a very important step.  By default, only enough memory is allocated for the internal monitor.  You have to tell X11 to reserve more.  First, figure out the maximum total dimensions you'll be using.  I have a 1280x1024 display below my internal 1280x800, so my total is 1280x1824.  Note that if your total is more than 2048x2048, you won't be able to run compiz ("Advanced Desktop Effects") due to a limitation in the video card.

Open a terminal and run the following to edit your xorg configuration:
```
sudo gedit /etc/X11/xorg.conf
```

Find a section that looks like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Now change it to look like this (substitute your own dimensions for mine):
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	
	SubSection "Display"
		Depth	24
		Virtual	**1280	1824**
	EndSubSection
EndSection
```

Log out.  When the login screen appears, hit Ctrl-alt-backspace (backspace is labeled "delete" on the macbook keyboards).  Login and run that command I gave you yesterday again.

I'm currently working on an autodetect script that enables or disables the external monitor based on if it's connected.  I'll post it when I get it working, along with directions on how to run it automatically on login.

---

### Post by bluefish86 on 2008-04-28
Okay, here's the script:
```
#!/bin/sh

if [ $1 ]; then
	if [ $1 = "on" ]; then
		TODO="on"
	elif [ $1 = "off" ]; then
		TODO="off"
	elif [ $1 = "auto" ]; then
		TODO="auto"
	else
		TODO="error"
		echo "Unknown argument\nValid arguments: on off auto"
	fi
else
	TODO="auto"
fi

if [ $TODO = "auto" ]; then
	STATUS=`xrandr -q | sed -n 's/VGA \([a-z]*\).*/\1/p'`
	if [ $STATUS = "connected" ]; then
		TODO="on"
	elif [ $STATUS = "disconnected" ]; then
		TODO="off"
	else
		TODO="error"
		echo "Error parsing display status"
	fi
fi

if [ $TODO = "on" ]; then
	echo "Turning VGA on."
	xrandr --output VGA --auto --below LVDS
	gconftool-2 --type int --set /apps/panel/toplevels/top_panel_screen0/monitor 1
elif [ $TODO = "off" ]; then
	echo "Turning VGA off."
	gconftool-2 --type int --set /apps/panel/toplevels/top_panel_screen0/monitor 0
	xrandr --output VGA --off
fi
```

To install it, run
```
sudo gedit /usr/local/bin/vga
```

Paste the script in, save it and close gedit.  Now make the script executable
```
sudo chmod 755 /usr/local/bin/vga
```

You can run the script at any time with the command *vga*.  You can force the display on or off by running *vga on* or *vga off*.

To have it run on login, go to System->Preferences->Sessions.  Click the Add button.  Enter *vga* as the command, and whatever you want for the name and comment.  Click OK and close sessions.  Next time you log in, it should run automatically.

You can also put a button in the panel to run it.  Right click on empty space on the panel, and choose "Add to panel".  Choose "Custom Application Launcher".  Leave the type set to "Application", enter *vga* as the command, and whatever you want for the name, comment and icon.

---

### Post by Dale Cooper on 2008-08-15
Thank you very much Bluefish86, your posts have been really helpful and I got it working great.

However I got an annoying issue that I don't know how to solve. When I maximize a window on the main screen, it will hide the top gnome panel (the secondary screen is above, so the bottom panel is hidden if it is below). Also on the top panel I can see the drop shadow of the secondary screen's maximized window.

Anyone with a fix or a good idea for this please? Thanks in advance

---

### Post by fishes on 2009-02-05
Yesterday, I installed 8.10 on my MacBook 2,1. bluefish86, your explanations were very helpful and saved a lot of time.  Yesterday, after reading your post, I got everything working with the xorg.conf edit xrandr and Screen Resolution. I have not been able to get the script to work consistently, however.

But today, no such luck. I have my monitors set up one above the other, as you note is necessary for an extended set up with a 22" monitor.  I log in without the monitor connected, plug it in, go to Screen Resolution, arrange the monitors vertically, turn off mirroring, and then turn the 22 inch on to it's full resolution.  Then the problem starts.  The only desktop that shows up is in the upper right of the 22 inch monitor, the rest of both screens is blacked out. The visible desktop is the size of my MacBook screen.  Strangely, my cursor is free to move all over both the 22 inch monitor and the MacBook's screen, even in the black areas.  Windows, however, disappear as I drag them into the black.

It's almost as if the black is on a layer below the cursor but above the windows, panel, and background image. It is masking all but a part of the desktop.

I've also tried xrandr and your script, but the same problem occurs.

Have you ever experienced this, or do you have any suggestions on a fix? Thanks.

---


---
title: "Multi-Button Mouse configuration for dummies"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by John Murphy on 2006-08-29
Believe me when I say there's a Long way of doing this and a short and painless way of doing it. This routine seems to have been taailor made for Ubuntu if not other debian variants also. I spent months trying to configure a S intellimouse Optcal last year on SuSE 9.3. Never got it right and lost the kernel with a routine similar to the one [Here](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons)

- entirely up to you ifyou want to torture yourself with this routine - for me the g++ compiler didn't work half the links were dead or worse......

Trust me on this - you can configure your mouse in aout 7 inutes or less if your quick at typing.......or copying and pasting!

Heres The Complete Routine

=========================================================================
> 
I found this [Link](http://ubuntuguide.org/wiki/Dapper) and it rocks - tailored to Ubuntu and you can install lots of stuff withot weeks of stress by the looks of it!


**_[size=3]To  Configure Ubuntu for multi-button Mouse[/size]_**


**Activate side-mouse-buttons in FireFox**

Just add two lines to xorg.conf will activate side-mouse-buttons in FireFox. This should work with most 5-button mouse. Here is a list of mice that worked with this instruction.

Logitech MX510
Logitech MX518

**Backup Gnome configuration file**

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

**Modify the Gnome configuration file**

```
gksudo gedit /etc/X11/xorg.conf
```

Find the Input Device section for your mouse and add two lines as shown below. You may also increase the number of buttons if your mouse has more than 7, just fix the rest of the section based upon the number of buttons (remember back/forward, wheel click & tilt left/right all count as buttons)

Change:

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	...
	Option "Protocol" "ExplorerPS/2"
	...
	Option "Emulate3Buttons"       "true"
EndSection

to:

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	...
	Option "Protocol" "ExplorerPS/2"
	...
	Option "Emulate3Buttons"       "true"
	Option "Buttons" "7"
 	Option "ButtonMapping" "1 2 3 6 7"
EndSection


At this point you can reboot your computer or reboot Gnome (Ctrl-Alt-BackSpace) to see if your forward/back buttons work in FireFox. They still won't work in Nautilus yet until you install the imwheel dameon.


[b/_Install & Configure IMWheel_[/b]

   ** * Install IMWheel **

```
sudo apt-get install imwheel
```

   ** * Modify IMWheel configuration file **

```
gksudo gedit /etc/X11/imwheel/imwheelrc
```

    * Insert the following at the bottom of this existing file 

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right 

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right


   ** * Create IMWheel start-up script **

```

sudo mkdir /home/login
gksudo gedit /home/login/mouse
```

    *** Insert the following into this new file **

#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 6 7 4 5" &
exec imwheel -k -b "67" &
exec $REALSTARTUP

    *** Grant execution for everyone to this new script **

```
sudo chmod +x /home/login/mouse
```

    * Configure this script to be executed at start-up
         1. Select 'System' > 'Preferences' > 'Sessions'
         2. Click the StartUp tab
         3. Click Add, then input: /home/login/mouse
         4. Click OK, then Close 

    * Reboot your computer or your Gnome environment and then test your back/forward mouse buttons in Nautilus

---

### Post by flixer on 2006-08-30
I did all the stuff in this how-to. One problem with my mouse(MX510). Everything went backwards. For example, my scroll works as the previous and next buttons.

P.S This how-to is much easier than the previous ones.

Here's my xorg.conf:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option 		"Emulate3Buttons" "true"
	Option 		"Buttons" "7"
	Option 		"ButtonMapping" "1 2 3 6 7"
EndSection
```

---

### Post by JPMaximilian on 2006-11-29
I followed those directions for my mx310, it doesn't work in nautilus and now my back forward buttons scroll and my scroll goes back-forward in firefox.  But like I said, nautilus back forward doesn't work.  Kind of a step backwards I'd say.

---

### Post by BioX on 2007-03-01
I tested this settings on mice from Mx3000 Laser Desktop - mx600 laser - on this mouse you have to change part of xorg.conf to:
```
     Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"6 7"
	Option		"Emulate3Buttons"	"true"
	Option "Buttons" "7"
	Option "ButtonMapping" "1 2 3 4 5"
```

If not - your backward/forward buttons will work as scroll and vice versa.
But i still don't know how to set zoom buttons on mouse.

---

### Post by chavo on 2007-03-01
> **flixer said:**
> I did all the stuff in this how-to. One problem with my mouse(MX510). Everything went backwards. For example, my scroll works as the previous and next buttons.

P.S This how-to is much easier than the previous ones.

Here's my xorg.conf:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option 		"Emulate3Buttons" "true"
	Option 		"Buttons" "7"
	Option 		"ButtonMapping" "1 2 3 6 7"
EndSection
```

Try adding this in there 
```

        Option          "ZAxisMapping"          "4 5"

```

---

### Post by Snyper64 on 2007-03-15
Also, you have your "Emulate3Buttons" set to "true", you want to change that to "false" or just delete it completely. Hope this helps.

Snyper64

---

### Post by Wiebelhaus on 2007-04-26
I followed the directions to the T , now i need to restore my conf.bak , please explain to this noob how to do that?


thanks.

---

### Post by Snyper64 on 2007-04-26
Did you change the identifier? If you did change it back or change the identifer in the server layout to match what you changed it to.

---

### Post by SirThom on 2008-03-19
Hmmm.
I saw a few guides like this and I ran the instructions on one of them and I got some of the buttons on my Logitech VX Nano sort of working . . . well they do something, like, bring up contextual menus or something.  I haven't quite experimentally verified what they do.
Anyway, what I really want to do (I do this on my multi-button logitech on my mac and on this one when I was running xp) is customise what the buttons do.  I never used the horizontal scroll, so I set nudging the wheel to the left and right to be copy and paste,  Also I set the other buttons to do things which depend on where I am like open up a new browser tab, save a document, whatever.  Is there anyway of doing this in ubuntu?  Is perhaps something coming in Hardy Heron?

I remember something on one of the systems that I used in the past that let me configure a generic multi-button mouse through the gui.  I could press different buttons, the app would tell me their number, and I could tell the app what I wanted those buttons to do.  I can't remember if this was *nix or something else.

---

### Post by Xiong Chiamiov on 2008-03-19
> **sx66gns said:**
> I followed the directions to the T , now i need to restore my conf.bak , please explain to this noob how to do that?


thanks.

Quite a time ago, but:
```

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

```

---

### Post by Jim_1981 on 2008-03-29
> **John Murphy said:**
> ...

#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 6 7 4 5" &
exec imwheel -k -b "67" &
exec $REALSTARTUP

...

If you have the problem with the back forward buttons and the wheel getting mixed up, changing the above script to :

```
#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 4 5 6 7" &
exec imwheel -k -b "45" &
exec $REALSTARTUP
```

will fix it. I still found this didn't work in nautilus though, so I just removed imwheel and edited /etc/X11/xorg.conf instead. I find I actually don't miss the side buttons in nautilus too much and without imwheel rolling the wheel on the desktop scrolls through the different workspaces, which I rather like.

---


---
title: "mx310 how to install my mouse"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by zazeem on 2006-07-27
hi, i have an mx310 logitech optical 6 button mouse, and i have been changing the xorg config to different post i have read and faqs but none of them work, is there a nooby guide to installing an mx310 somewhere? Everytime i try somthing i restart and get a blank console screen where i go in and change it back to the old lame mouse settings, please help its driving me insane!!

---

### Post by reacocard on 2006-07-27
you're in luck. i have the exact same mouse. it's easy to get the side buttons working. here's the relevant section of my xorg.conf:

```
Section "InputDevice"
	Identifier	"Logitech USB Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
	Option          "ButtonMapping"         "1 2 3 6 7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection
```

just change your mouse's config to this. if your identifier line is different, don't change it. save, reboot, that's it.

---

### Post by zazeem on 2006-07-31
thnx <333

---

### Post by JPMaximilian on 2006-08-24
Sweet fix, It crashed my xserver at first, but after reading the part about not changing the identifier I was golden.  Is there any way to keep the back forward buttons while still using the scroll as scroll and middle click as opposed to moving the middle click to the button below it?  Thanks.

---

### Post by reacocard on 2006-08-24
>  Sweet fix, It crashed my xserver at first, but after reading the part about not changing the identifier I was golden. Is there any way to keep the back forward buttons while still using the scroll as scroll and middle click as opposed to moving the middle click to the button below it? Thanks.
What do you mean? This config works perfectly for me, the middle-click is still middle-click. the little tiny button below the scrollwheel for some reason works just like the left-click for me.:-k

---

### Post by JPMaximilian on 2006-08-24
I stand corrected, the small button below the scroll acts to open up links in a new window, and the middle click works normally.  It'd be sweet if the forward back buttons worked for nautilus as well.

---

### Post by Louie on 2006-11-19
I tried to change my mouseoptions in the xorg conf from;



Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

to;

Section "InputDevice"
    Identifier    "Logitech USB Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option          "Buttons"               "7"
    Option          "ButtonMapping"         "1 2 3 6 7"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "false"
EndSection


But it my X-server refuse to start again after that :(

---

### Post by reacocard on 2006-11-19
> **Louie said:**
> I tried to change my mouseoptions in the xorg conf from;



Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

to;

Section "InputDevice"
    Identifier    "Logitech USB Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option          "Buttons"               "7"
    Option          "ButtonMapping"         "1 2 3 6 7"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "false"
EndSection


But it my X-server refuse to start again after that :(


Don't change the Identifier line.

---

### Post by Louie on 2006-11-19
Thank you reacocard! You saved my day. It working fine now :)
Just one more question, how do I change so I get the "back" and "forward" button to switch side, Im lefthanded

---

### Post by reacocard on 2006-11-20
> **Louie said:**
> Thank you reacocard! You saved my day. It working fine now :)
Just one more question, how do I change so I get the "back" and "forward" button to switch side, Im lefthanded

try
```
Option "ButtonMapping" "1 2 3 7 6"
```

---

### Post by mirzmaster on 2007-02-20
> **reacocard said:**
> you're in luck. i have the exact same mouse. it's easy to get the side buttons working. here's the relevant section of my xorg.conf:

```
[FONT="Lucida Console"]Section "InputDevice"
	Identifier	"Logitech USB Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
	Option          "ButtonMapping"         "1 2 3 6 7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection[/FONT]
```

just change your mouse's config to this. if your identifier line is different, don't change it. save, reboot, that's it.

This worked perfectly!  By the way, I was able to change the Identifier as long as I changed the corresponding entry under the "ServerLayout" section.

So my ServerLayout now looks like the following:

```
[FONT="Lucida Console"]Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
#	InputDevice    "Configured Mouse"
	InputDevice    "Logitech MX310 Optical Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection[/FONT]
```

I now have two mice defined, but as dictated in the "ServerLayout" section, only the latter is in use:

```
[FONT="Lucida Console"]Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier	"Logitech MX310 Optical Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
	Option          "ButtonMapping"         "1 2 3 6 7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection[/FONT]
```

---

### Post by Snyper64 on 2007-03-13
Question, how do I get into my xorg.conf file? I tried typing "gedit /etc/X11/xorg.conf" into the terminal but it showed up as a read only. I know how to do basic programming(I took Visual Basic in high school and college) but I am a Linux noob!! I would also like to know how to back up the file just in case i screw up and how to restore it in the terminal as I have yet to pick up a book on Linux to learn the command language.

Thanks
Snyper64

---

### Post by reacocard on 2007-03-13
> **Snyper64 said:**
> Question, how do I get into my xorg.conf file? I tried typing "gedit /etc/X11/xorg.conf" into the terminal but it showed up as a read only. I know how to do basic programming(I took Visual Basic in high school and college) but I am a Linux noob!! I would also like to know how to back up the file just in case i screw up and how to restore it in the terminal as I have yet to pick up a book on Linux to learn the command language.

Thanks
Snyper64

backup:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

restore backup:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

edit:
```
gksudo gedit /etc/X11/xorg.conf
```

System files (like xorg.conf) can only be modified by root (like administrator and C:/Windows in windows), so prefix those command with sudo (or gksudo for GUI apps) to gain temporary root privileges.

---

### Post by Snyper64 on 2007-03-13
Thanks

---

### Post by capre91 on 2007-04-19
Hi all, I have the same mouse (mx310)...however, when I open the xorg.conf file it is blank...what am I doing wrong?

thanks
Tony

edit: I found my problem...I was typing this: x11,  the x has to be a capital X

OK

Tony

---

### Post by Snyper64 on 2007-04-19
To open your xorg.conf file open up a terminal and type in:
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by capre91 on 2007-04-19
Hi snyper64, I finally got my back and forward buttons to work...and you were right...leave the identifier alone! Thanks for your help.

Tony

---

### Post by Snyper64 on 2007-04-19
You can change the identifier but you also have to change the identifier in the server layout.

---

### Post by capre91 on 2007-04-19
Ok very good. Thanks again for the info.

---

### Post by Snyper64 on 2007-04-20
I do not know if anybody else is having problems with this mouse in Fiesty but i had trouble getting the forward and back buttons to work. After comparing my old xorg.conf file to my new one I noticed that Option "Protocol" "ExplorerPS/2" now showed up as Option "Protocol" "ImPS/2". As soon as I changed it back to Explorer it now works fine. Hope this helps anyone that is having the same problem as I did. Also heres what the file should look like for reference: ```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
	Option          "ButtonMapping"         "1 2 3 6 7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection
```

---

### Post by bubble_bobble on 2007-04-30
I commented out and modified my xorg file as follows:

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ExplorerPS/2"
#	Option		"ZAxisMapping"		"4 5"
#	Option		"Emulate3Buttons"	"true"
#EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
	Option          "ButtonMapping"         "1 2 3 6 7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection

Now the back/forward side buttons on my mx310 work, but my question is, is there now a way to reactivate the paste function that my mouse had before I made these changes?

When I clicked the right and left mouse buttons, I would paste whatever was highlighted in another window, and that was really useful.

---

### Post by reacocard on 2007-04-30
> **bubble_bobble said:**
> I commented out and modified my xorg file as follows:

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ExplorerPS/2"
#	Option		"ZAxisMapping"		"4 5"
#	Option		"Emulate3Buttons"	"true"
#EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
	Option          "ButtonMapping"         "1 2 3 6 7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection

Now the back/forward side buttons on my mx310 work, but my question is, is there now a way to reactivate the paste function that my mouse had before I made these changes?

When I clicked the right and left mouse buttons, I would paste whatever was highlighted in another window, and that was really useful.

The middle button does the same thing, or you can just change "Emulate3Buttons" back to "true".

---

### Post by bubble_bobble on 2007-04-30
> **reacocard said:**
> The middle button does the same thing, or you can just change "Emulate3Buttons" back to "true".

Thank you. My middle button is broken. Will emulate away!

---

### Post by TexSquid on 2007-07-02
I have the following problem 
after running
gksudo gedit /etc/X11/xorg.conf
I get
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
for my MX310
Everthing on the mouse works but the back /forward function
and when I go to System Settings the Mouse is listed but the dialog box states..
the mouse is detected and libusb was found but it is not possible to access this mouse..
and goes on to say it may be a permission problem.
I am running Kubuntu  7.04 if that makes a difference

---


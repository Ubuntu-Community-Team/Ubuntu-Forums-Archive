---
title: "2 Questions: Window Snap and Extra Mouse Buttons"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by kodemage on 2007-07-26
There are 2 things I'd like to be able to do which I cannot figure out. 

Window Snap:
On windows I used a program called AllSnap ([http://www.cs.toronto.edu/~iheckman/allsnap/](http://www.cs.toronto.edu/~iheckman/allsnap/)) to make all the windows snap into position, like in winamp or photoshop. I am looking for a way to duplicate this functionality. I'll bet there's a simple checkbox on a gnome option menu somewhere to do this but I can't find it.

Extra Mouse Buttons:
I have a Logitec MX 310 which has 5 buttons and a scroll wheel. I cannot find a way to make the Forward and Backward buttons work in Firefox or File Manager, nor can I use the alt-tab button. The System>Preferences>Mouse menu offers no help.

Regards,
-Benjamin

---

### Post by felicity on 2007-07-26
Your windows don't automatically snap? I used to use AllSnap on windows too, and one of the perks of using GNOME for me is the automatic snapping functionality. 

Here's what I do to get my extra mouse buttons working in firefox and nautilus:

1. Install imwheel:

```
sudo aptitude install imwheel
```

2. Edit xorg.conf:

```
 sudo gedit /etc/X11/xorg.conf
```

3. Replace the mouse section with the following:

```
 Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons" "7"
	Option		"ButtonMapping"		"1 2 3 6 7"
	Option		"Emulate3Buttons"	"false"
EndSection
```

4. Create .imwheelrc:

```
sudo gedit .imwheelrc
```

5. Paste in the following code:

```
 ".*"
      None, Up, Alt_L|Left
      None, Down, Alt_L|Right

      "(null)"
      None, Up, Alt_L|Left
      None, Down, Alt_L|Right

```
6. Edit the startup file to make imwheel start with X:

```
sudo gedit /etc/X11/imwheel/startup.conf
```

Find this line and change the 0 to a 1:

```
  IMWHEEL_START=0
```

To look like:

```
  IMWHEEL_START=1
```

7. Create one last file:

```
sudo gedit /etc/X11/Xsession.d/63xmodmap
```

Paste in the following code:

```
 killall imwheel
      xmodmap -e "pointer = 1 2 3 4 5 6 7"
      BINARY=$(which imwheel)
      $BINARY -k -p -b "6 7"
```

8. Make the file executable:

```
  sudo chmod 777 /etc/X11/Xsession.d/63xmodmap
```

9. Finally restart X:

CTRL + ALT + BACKSPACE

---

### Post by xopher_mc on 2007-07-26
Hi

I don't know of any setting to do what you wan for the windows.

To get the mouse working go to 

Applications > Accessories >Terminal

copy and past the following commands in

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bk        This makes a backup 

sudo gedit /etc/X11/xorg.conf

This should bring up the configuration file

find the bit to do with the mouse. mine looks like

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Paste this over the top of it.

Section "InputDevice"
   Identifier  "Configured Mouse"
   Driver      "evdev"
   Option      "Device"   "/dev/input/event0"
EndSection

NB make sure the identifier is the same on both

Save and close

then type 

xmodmap -e "pointer = 1 3 2 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32"

CTRL +ALT +BACKSPACE

Hopefully that should do it.

---

### Post by kodemage on 2007-07-26
xopher_mc: I get the following error when executing your instructions.

kode@Shiva:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bk
kode@Shiva:~$
kode@Shiva:~$ sudo gedit /etc/X11/xorg.conf
kode@Shiva:~$ xmodmap -e "pointer = 1 3 2 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32"
xmodmap:  commandline:1:  bad number of buttons, must have 11 instead of 32
xmodmap:  1 error encountered, aborting.
kode@Shiva:~$

felicity: I think there's a problem with your method in or around step 4. The path may be incorrect is it supposed to be in the ~ directory? Am I supposed to be creating a new file?

In any case neither of your solutions worked :(

Regards,
-Benjamin

---

### Post by felicity on 2007-07-26
Yes, you're supposed to be creating a new file in your home directory for step 4.

---


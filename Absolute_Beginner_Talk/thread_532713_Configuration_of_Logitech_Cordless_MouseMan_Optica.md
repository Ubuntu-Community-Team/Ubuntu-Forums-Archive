---
title: "Configuration of Logitech Cordless MouseMan Optical"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by stefangachter on 2007-08-23
I have a Logitech Cordless MouseMan Optical mouse and I try to make the thumb button work with firefox. Even reading through several post, I could not get the correct settings. Could somebody post the xorg.conf section of the mouse device and the xmodmap settings? Or any other hints? Thanks a lot, Stefan

---

### Post by felicity on 2007-08-23
I use this for my intellimouse, but it should also work for the MouseMan.

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

### Post by stefangachter on 2007-08-23
Thanks a lot! Now it works as expected... Finally I got the mouse running. Is there something like a database, where you can search for your hardware and then get a guidline how to install the device? This would be more efficient than searching the forums.

---

### Post by felicity on 2007-08-23
I don't know of one. :( 

I just try to bookmark the various HOWTO pages I find related to my own hardware, that way I always have them for future reference. That doesn't help finding them in the first place though..  :lol:

---

### Post by stefangachter on 2007-08-24
I found this link:Is my hardware Linux-compatible?

[http://www.linux.com/feature/118497](http://www.linux.com/feature/118497)

Lists some hardware databases and might be a starting point...

---

### Post by Herb7211 on 2008-06-05
Hello there,

I'm also trying to get my Logitech Cordless Mouseman Optical to run perfectly (it runs almost perfectly, only the back-Button doesn't work in firefox)

I'm running Ubuntu 8.04, and i essentially copy/pasted everything from the second post, except in the xorg.conf i set the Buttons to 6 (the cordless Mouseman only has a Thumb- (Back) Button, no forward button on the right side)

Srolling and everything works fine (as before) but the back-button still doesn't work. To find out the button-mapping of my mouse, i started the graphical-ui if imwheel with "imwheel -c"
Now, if I click the "Grab wheel action" to identify the buttons, the back-button and the Button for pressing down the mouse-wheel are **both!!** identified as button 6, so it looks like imwheel can't differentiate between those two.

Firefox however can. - If i click on one of the tabs with the middle (wheel) button, it closes the tab, if i click on it with the thumb-button, nothing happens.

Now what else can i try? - Does anyone have the same mouse running with all 6 buttons?

Thanx in advance, herb

---


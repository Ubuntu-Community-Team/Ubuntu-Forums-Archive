---
title: "[B]How do I configure my IntelliMouse Optical to function correctly[/B]"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by kannedheat on 2007-06-04
I am trying to configure my  IntelliMouse Optical to function correctly. I changed my the relevant portion of my xorg.conf file looks like:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons" "7"
	Option		"ButtonMapping"		"1 2 3 6 7"
	Option		"ZAxisMapping" "4 5"
	Option		"Resolution" "100"
EndSection
```

And  the relevant portion of my .imwheelrc looks like:

```
# Intellimouse or Mouseman's Back/Forward Buttons
	".*" None,Up,Alt_L|Left None,Down,Alt_L|Right

# http://ubuntuforums.org/showthread.php?t=178574#5 I added
  
 "(null)"
 None, Up, Alt_L|Left
 None, Down, Alt_L|Right

```

And the relevant portion of my imwheelrc/startup.conf looks like:

```
IMWHEEL_START=1
```

The only problem is that I cannot scroll correctly. My mouse mapping is:
[LIST=1]
[*]Left 1
[*]scroll button 2
[*]Right 3
[*]Left thumb 4
[*]Right thumb 5
[*]scroll up 6
[*]scrll down 7
[/LIST]

Thanks,
Kannedheat

---

### Post by kannedheat on 2007-06-05
I found my solution from [http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#codecs]("http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#codecs")
[B]
Enable Intellimouse Support[/B]

The following works for the Microsoft IntelliMouse Explorer 3.0A. It will enable full support for the forward and back side buttons (works in Nautilus, Epiphany, Firefox, Konqueror). As always, backup your files before mucking with them.

   1.  Install imwheel:

      ```
sudo aptitude install imwheel
```

   2.  Edit xorg.conf:

     ```
 sudo gedit /etc/X11/xorg.conf
```

   3.  Replace the mouse section with the following:

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

   4.  Create .imwheelrc:

      ```
sudo gedit .imwheelrc
```

   5.  Paste in the following code:

```
 ".*"
      None, Up, Alt_L|Left
      None, Down, Alt_L|Right

      "(null)"
      None, Up, Alt_L|Left
      None, Down, Alt_L|Right
```     

   6.   Edit the startup file to make imwheel start with X:

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

   7.   Create one last file:

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

   8.   Make the file executable:

    ```
  sudo chmod 777 /etc/X11/Xsession.d/63xmodmap
```

   9.  Finally restart X:

      CTRL + ALT + BACKSPACE

And your done.:D

---

### Post by LollYouSuckZor on 2007-06-05
And you tried to Bold the title...

---

### Post by badbob100 on 2007-06-05
lol you have to do all that just to enable mouse buttons! Bye bye linux...
I have a 5 button mouse which doesn't work fully (forward/back not working) why isn't mouse config available in mouse settings.

Given up on Ubuntu for HTPC and rig...

---

### Post by kannedheat on 2007-06-05
Grow up Nickolas

---

### Post by badbob100 on 2007-06-13
> 9. Finally restart X:

CTRL + ALT + BACKSPACE

Alright upto there, done that screen corruption, total lockup, reboot and ubuntu doesn't load up. Great.

---

### Post by Spritegeezer on 2007-06-13
A person tries to help someone and you give him grief.  BadForm BadBob.  By all means, leave Ubuntu.  I'm sure the purchase price will be cheerfully refunded.

---


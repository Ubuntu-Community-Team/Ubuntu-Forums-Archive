---
title: "IntelliMouse Optical to work for all users"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by kannedheat on 2007-06-08
I setup my mouse to work under root my problem is that it does work for all users.  How do I setup IntelliMouse Optical to work for all users?

---

### Post by viciouslime on 2007-06-08
What doesn't work exactly? Also, you really shouldn't be logging in as root, best in fact to leave root disabled, it simply isn't needed in ubuntu. :)

---

### Post by kannedheat on 2007-06-08
I  configured my IntelliMouse Optical to function correctly by Enable Intellimouse Support. I changed my the relevant portion of these files looks like: 

NOTE: The following works for the Microsoft IntelliMouse Explorer 3.0A. It will enable full support for the forward and back side buttons (works in Nautilus, Epiphany, Firefox, Konqueror). As always, backup your files before mucking with them.

1. Install imwheel:

```


sudo aptitude install imwheel

[CODE]

2. Edit xorg.conf:

[CODE]

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
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons" "7"
	Option		"ButtonMapping"		"1 2 3 6 7"
	Option		"ZAxisMapping" "4 5"
	Option		"Resolution" "100"
EndSection


```


4. Create .imwheelrc:

```


sudo gedit .imwheelrc


```

5. Paste in the following code:

```


 # Intellimouse or Mouseman's Back/Forward Buttons
 
      ".*"
      None, Up, Alt_L|Left
      None, Down, Alt_L|Right

# http://ubuntuforums.org/showthread.php?t=178574#5 I added

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


The only problem is that I cannot use this configuration for my other users on the same computer.:(

---

### Post by kannedheat on 2007-06-09
I created IMWheel start-up script:
```

sudo mkdir /home/login
gksudo gedit /home/login/mouse

```
Then I inserted the following into this new file:
```

#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 6 7 4 5" &
exec imwheel -k -b "6 7" &
exec $REALSTARTUP

```
I want to grant execution for everyone to this new script:
```

sudo chmod +x /home/login/mouse

```
My question is how do I configure this script to be executed at start-up?
I am using Kubuntu 7.04.

---

### Post by ggaaron on 2007-06-09
${HOME}/.kde/Autostart/
Every file in this folder will be executed on kde startup.

---

### Post by kannedheat on 2007-06-10
I copied the file /home/login/mouse to /<usersnamehere>/.kde/Autostart and it isn't working.:(

---


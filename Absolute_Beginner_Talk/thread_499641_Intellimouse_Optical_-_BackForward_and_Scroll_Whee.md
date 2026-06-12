---
title: "Intellimouse Optical - Back/Forward and Scroll Wheel are reversed!"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by chrisf79 on 2007-07-12
Greetings:

In an attempt to get my back/forward buttons working in Firefox on my Microsoft Intellimouse Explorer, I followed a thread on this forum and edited my xorg.conf to have the following:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"	"7"
	Option		"ButtonMapping" "1 2 3 6 7"
EndSection

```

Unfortunately, now my Back/Forward buttons on the mouse make the page scroll.  The wheel does forward/back.

I also have imwheel installed if that matters.

How do I reverse this so the buttons do what they're supposed to?  Any help would be greatly appreciated!

---

### Post by jimrz on 2007-07-12
here's my xorg.conf section that woks perfectly with the same mouse
```
Section "InputDevice"
	Identifier "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "Buttons" "7"
        Option "ButtonMapping" "1 2 3 6 7"
        Option "ZAxisMapping" "4 5"
        Option "Resolution" "100"
EndSection
```

pretty similar, think all you need do is get rid of the "emulate 3 button" thingy and you should be ok

---

### Post by RagingOcelot on 2007-10-15
I can confirm this worked for me with an Intellimouse Optical USB.  Thanks, jimrz !

---

### Post by boyturtle on 2007-11-26
Me too. Thanks a whole bunch jimrz. 

Now, for the first time in a while, I can use my mouse like its supposed to be used again :guitar:

---

### Post by RoughriderUT on 2008-01-09
Hi. This helped me out too, thanks for the info.

---

### Post by sagarhshah on 2008-01-22
Hey,

this one worked for me as well jimrz
I have a usb microsoft intellimouse although I am using it with a ps/2 adapter it still worked for me.

Thanks

Sagar

---

### Post by Macbeth417 on 2008-02-15
I followed this tutorial and made a few minor tweaks 
[http://dotnet.org.za/matt/pages/39097.aspx](http://dotnet.org.za/matt/pages/39097.aspx)

I had the same issue, wheel and back/forward buttons swapped. 
Just so happens those are button, 4 5 6 and 7. So  I  just flipedp 6 7  with 4 5 in my /etc/X11/Xsession.d/63xmodmap file.

This worked perfectly for me!

change your /etc/X11/Xsession.d/63xmodmap to have 12345 for the pointer value and change the $Binary to "4 5": 

```
killall imwheel
xmodmap -e "pointer = 1 2 3 4 5 6 7"
BINARY=$(which imwheel)
$BINARY -k -p -b "4 5"
```




my xorg.conf section in case you wanted to see

```
Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ExplorerPS/2"
    Option "Buttons" "7"
    Option "ButtonMapping" "1 2 3 6 7"
    Option "Emulate3Buttons" "false"
EndSection
```

Worked perfectly for intellimouse 4.0

---


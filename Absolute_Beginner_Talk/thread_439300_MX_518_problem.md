---
title: "MX 518 problem"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Mr.Kuchinawa on 2007-05-10
I have a mx518 mouse, and when I click on the "back" button on the side of the mouse it seems as it is configured as the middle mouse when clicked on. The "forward" button acts like it's the right mouse button.
How do I fix this?

I believe it was after upgrading to feisty what I encountered this problem.

Thanks in advance.

---

### Post by Rescue9 on 2007-05-12
Ok... here are the things that I did to get my 518 running. 

Put this in your xorg.conf:
```
Section "InputDevice"
        Identifier      "MX518"
        Driver          "evdev"
        Option          "Device"        "/dev/input/mx518"
EndSection

```
You'll notice above that I have mx518 for my device. I mapped this using udev rules by adding the following to a new file called 19-local.rules to the /etc/udev/rules.d/ folder with the following information:

```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB-PS/2 Optical Mouse", NAME="input/mx518"

```
This allows me to map the mouse to "/dev/input/mx518". This is nice for me  since I have a laptop with a touchpad, stickpointer, and the 518 that sometimes don't play nicely together. If you wish not to map it this way, thats ok too. What I suggest you do is open a terminal and and

```
cat /dev/input/mouse
```

while moving the mouse around. This will cause "junk" to scroll across the screen and you can verify that /dev/input/mouse is the correct input. If you only have one mouse input, this may not be necessary, but with me, I have 3 inputs, so I have to make sure it's the right one.

And then you'll need to modify your Xmodmap somehow. What I do is put the file .Xmodmap with the following:
```
pointer = 1 2 3 4 5 8 9 6 7

```

The above will correctly map your mouse buttons.
I believe that this is all I had to do, but I tried so many things I forget. :-P. If this doesn't fix your problem... repost and I'll get back to you.

---

### Post by Mr.Kuchinawa on 2007-05-12
how do i open my .xmodmap? When I type cat /dev/input/mouse, it's says no such directory

---

### Post by Rescue9 on 2007-05-12
to open .xmodmap open a terminal window and type ```
gedit .xmodmap
``` from your home directory.

If there isn't a /dev/input/mouse then search for /dev/input/{WhateverXorg.confHasListed] and try that.

---

### Post by Fruktkake on 2007-12-13
I added the first code through xorg.conf. Then I  There didn't seem to be a file called that because the file I edited was empty. Then I made a new file by using the command you posted, and pasted the code there then saved it. My MX518 still doesn't work. What have I done wrong?

---

### Post by hyperq on 2008-02-06
I got the side mouse buttons on my Logitech MX518 working in Firefox. I am using the "evdev" driver, not the "mouse" driver. I am using Kubuntu 7.10 Gutsy, which already has the package "xserver-xorg-input-evdev" installed by default.

Simply change the mouse section of your /etc/X11/xorg.conf to this:

[HTML]
Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "evdev"
       Option          "CorePointer"
       Option          "Buttons"       "7"
       Option          "ZAxisMapping"  "4 5"
       Option          "ButtonMapping" "1 2 3 6 7"
       Option          "Name"  "Logitech USB-PS/2 Optical Mouse"
EndSection
[/HTML]

---


---
title: "Installing (modifying) mouse drivers in 7.04"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Smittysmit on 2007-05-19
Hello all,

I have a Kensington Expert Mouse Pro but have been unable to use all of my buttons.  I understand that i might not be able to program the 6 quick launch buttons but really want to use the second set of right/left for going forward/backward in web pages.

I found this on the net but have no clue on EXACTLY what I need to do.  I have dabbled with Linux in the past but need step by step help.

This is a page to remind me about how to configure Linux and X for this input device, which despite the name is actually a trackball.

[B]Firstly, you need a version of the Linux kernel which supports the input core and which puts PS/2 mice through the input core. It also needs to be new enough to have the patch for Expert Mouse support in psmouse-base.c. That probably means later 2.4.x kernels or a 2.6.x kernel. Use cat -A /dev/input/mice to check that this is all working and that all four buttons and the scroll wheel generate different byte sequences.

A suitable XF86Config-4 rune is:

Section "InputDevice"
        Identifier      "Generic Mouse"
        Driver          "mouse"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/mice"
        # /dev/input/mice can emulate plain PS2, ImPS/2 and ExplorerPS/2;
        # only this one supports more than 3 buttons + scrollwheel:
        Option          "Protocol"              "ExplorerPS/2"
        # scroll wheel
        Option          "ZAxisMapping"          "4 5"
        # four real buttons and the scroll wheel:
        Option          "Buttons"               "6"
        # This bit's optional; it configures button 4 as a sort of 'lock'
        # button, so instead of holding down one of the other buttons you
        # first press button four then click the other button:
        Option          "DragLockButtons"       "6"
EndSection[/B]


Any help is greatly appreciated.
Smitty

---

### Post by mahy on 2007-05-19
This is fairly easy. Open the xorg.conf, like this

```
sudo gedit /etc/X11/xorg.conf
```

Find the stanza about your mouse and make it look like this:

```
Section "InputDevice"
        Identifier      "Generic Mouse"
        Driver          "mouse"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Buttons"               "6"
        Option          "DragLockButtons"       "6"
EndSection
```

---

### Post by Smittysmit on 2007-05-20
Thanks for the reply.  It will be a day or so till I get time.  I assume this is done in the terminal window?

---

### Post by sson on 2007-05-26
Using 7.04, there must be something missing, does not work on my Dell Latitude with a Logitech MX500 USB mouse... :(

---

### Post by ozmoid on 2007-09-09
Did not work with my Kensington Orbit USB in 7.04.

---

### Post by LowSky on 2007-09-09
```
sudo -i
```
then type password

```
sudo gedit /etc/X11/xorg.conf
```

then paste this over your old settings
```
 
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
EndSection


```

if that doesnt work just use the this part and paste it over the original xorg file

```

    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
EndSection

```

remember to make back ups of the xorg file

---

### Post by ozmoid on 2007-09-10
Thank you, LowSky for the additional info, but the first edit to the xorg.conf file will not let the GUI load. When I started up this morning, I got "Failed to start the X server"

The log is giving me only two lines:
(==) Log file: "var/log/Xorg.0.log"
(==) Using config file: "/etc/X11/xorg.conf"

I'm going to try to boot from the CD and restore the .conf file. If I make it that far, I'll come back and try your settings! :)

---

### Post by Rmplstlskn on 2007-09-10
I tried LowSky's mod and I now have a "BACK" button on my Expert Mouse with Scroll Ring, only problem is the BACK is the button usually used for FORWARD (top right button).

How can I map the BACK to the top LEFT button?

Also, the top left button doesn't seem to do anything...

My lower buttons and scroll ring work great in FFawn.

We're almost there... 

Rmpl

---

### Post by ozmoid on 2007-09-11
> **ozmoid said:**
> Thank you, LowSky for the additional info, but the first edit to the xorg.conf file will not let the GUI load. When I started up this morning, I got "Failed to start the X server"

The log is giving me only two lines:
(==) Log file: "var/log/Xorg.0.log"
(==) Using config file: "/etc/X11/xorg.conf"

I'm going to try to boot from the CD and restore the .conf file. If I make it that far, I'll come back and try your settings! :)

I cannot edit the xorg.conf while booted from the CD - can't get to the file in terminal, so no "sudo"! I can get the machine to boot from the drive, but I do not know how to edit the .conf file in the terminal - can't launch gedit, no GUI.

Any help appreciated!

---

### Post by LowSky on 2007-09-24
```
sudo -i
```
then type password

```
sudo gedit /etc/X11/xorg.conf
```

then paste this over your old settings
```
 
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
[COLOR="Red"]    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
EndSection[/COLOR]


```

if that doesnt work just use the red part (leave the old line above the red) and paste it over the original xorg file


remember to make back ups of the xorg file

---

### Post by woodwardt on 2007-09-25
Wonder if one of you can give advice to a total newbie with ubuntu and linux please:

I've done the live install from the alternate cd after checking it's validity using an old 400 meg celeron hp sis 620 motherboard.  But no mouse activity at all...zero! It's a Logitech marble mouse (standard ps2 type mouse)

Now I am not even familiar with the tools at hand in ubuntu much less how to use those tools / issue commands etc.  So, if you've the time I really would appreciate some advice because without being able to use the mouse I cannot use the environment. Thanks.

---

### Post by t2000kw on 2007-09-30
I just picked up a Kensigton Expert Mouse, new, in the box with the price sticker still on it, even though it's an older model.

These work fine in Windows, and work well as a 2-button "mouse" (actually it's a trackball) in Ubuntu.

One of the things not addressed in any of these posts is how to get the upper two buttons (mine has 4 buttons total, no scroll ring) to do something useful. I copied and pasted the above information into xorg.conf and I did not screw up the X-server, but it didn't do anything, either. I would at the very least like to be able to press one of the upper two buttons down and then scroll vertically within a window. 

This isn't a showstopper for Ubuntu, but it's another area where it falls short of Windows for usability. Not that I'm gong back, bu tit sure would be nice to be able to have some of the extra functionality under Linux for this thing. 

If someone has figured out a way to do more than just change the xorg.conf file and can actually make the trackball do something useful with the upper buttons, I would like to know. Getting it to work as a normal trackball or mouse is not a problem--the stock xorg.conf file already does that without any modifications needed.

---

### Post by ADH on 2007-12-09
I'd like to set my top two buttons as held down for drag and drop.

---


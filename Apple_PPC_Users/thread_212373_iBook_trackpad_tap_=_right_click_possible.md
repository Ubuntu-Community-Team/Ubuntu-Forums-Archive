---
title: "iBook trackpad tap = right click possible?"
date: 2006-07-09
forum: Apple PPC Users
---

### Post by printmkr on 2006-07-09
I see where I can activate a trackpad tap as being a mouse click but is it possible to make it a right click for those of us with laptops with only one button? I looked at mouseemu, but unless I am missing something, it does not seem to offer that functionality... thanks for any help! (Running Ubuntu on a G3 500 mhz iBook with 320 megs of RAM and it's not too shabby!)

---

### Post by rbalfour on 2006-07-09
> **printmkr said:**
> I see where I can activate a trackpad tap as being a mouse click but is it possible to make it a right click for those of us with laptops with only one button? I looked at mouseemu, but unless I am missing something, it does not seem to offer that functionality... thanks for any help! (Running Ubuntu on a G3 500 mhz iBook with 320 megs of RAM and it's not too shabby!)

it's F12 on the ibook.

---

### Post by printmkr on 2006-07-09
yep, but the f12 key (actually the f11 key now after mouseemu) is "far away" from my hand on the trackpad. I am looking to tap (or double tap) on the trackpad and get a "right click", similar to Raging Menace's "Sidetrack" (  [http://http://www.ragingmenace.com/software/sidetrack/]("http://http://www.ragingmenace.com/software/sidetrack/")  ) on OSX.

---

### Post by jah on 2006-07-14
Is is possible to remap right click away from F12, as it is really annoying having that button do it. Is there any way to get ctrl-click right click functionality in Ubuntu, like in OS X?

Cheers

Ps: i have an iBook G3. In Tiger, you hit F12 to open the CD drive (it is not slot loading). How do i open the cd drive in Ubuntu, as F12 is right click... Very frustrating not being able to use CDs!!

Thankyou :)

---

### Post by anday on 2006-07-21
[I]Is is possible to remap right click away from F12, as it is really annoying having that button do it. Is there any way to get ctrl-click right click functionality in Ubuntu, like in OS X?

Cheers

Ps: i have an iBook G3. In Tiger, you hit F12 to open the CD drive (it is not slot loading). How do i open the cd drive in Ubuntu, as F12 is right click... Very frustrating not being able to use CDs!!

Thankyou [/I]

I have to hold down the function <fn> button down to eject the cd slot <F12> and also to adjust the brightness and volume using the keyboard... sorry if I am being too obvious for some (!) ... well what I don't know is how to reconfigure the 'right click button' and what I'd really love to know is how I can set Ubuntu to recognize a left click when I tap on the trackpad, that really makes me blue with question marks :confused: 

help and thanks

---

### Post by hulleye on 2006-08-05
left-click is easy for the powerpc platform. Open up a terminal window and type the following:

sudo trackpad tap

feed in your password and you now have a left-clickable trackpad.

Btw, when I first saw your post, I didn't know there was such a command... am just realising how much I depend on the user community that I hadn't even thought of just opening up Ubuntu's help files and searching for the term "trackpad"

Other options available are: 

1. notap - to disable left clicking
2. drag - allows click and drag
3. lock - allows a draglock
4. show - show's the current settings for the trackpad


right-clicking is still a mystery to me... the F12 method is really annoying

---

### Post by hulleye on 2006-08-08
Well, figuring out how to tap left-clicks on the trackpad seems to have been the easy part. Now, does anyone know how to make the command stick so that I don't have to re-enter it every time I restart the computer?

---

### Post by drummerbull on 2006-10-10
bump, i would also like to know if there is a better way to get this right click to work!

---

### Post by ORBiTrus on 2006-10-10
I don't have a Mac, but...

Probably not possible.  Do you know what driver it uses?  It could be in the documentation.  Or likely a simple code change.

Edit: I don't suppose the obvious two-finger tap or three-finger tap does anything?

---

### Post by PsyCHZZZ on 2006-10-14
HI.. I'm running Ubuntu on my iBook G3 600MHz and I initally also faces the problem of right clicking on my iBook... so, after doing a bit of Googling, I found a solution to map right click to Fn+Alt rather than pressing F12. 

Here's how to do it.

1. Login as root.
1. Edit /etc/sysctl.conf.
3. Locate - 
    # Emulate the middle mouse button with F11 and the right with F12
    dev/mac_hid/mouse_button_emulation = 1
    dev/mac_hid/mouse_button2_keycode = 87
    dev/mac_hid/mouse_button3_keycode = 88

    and change the last keycode from 88 to 100.
4. Save the file and reboot.
5. To right+click, press Fn+Alt. :)

That works for me... so, I hope it'll work you you too. 
Cheers~!

Credits to : [http://www.celsius1414.com/ubuntu_linux_on_ibook](http://www.celsius1414.com/ubuntu_linux_on_ibook)

---

### Post by salguod on 2006-10-18
I use a USB two-button external mouse with a scrolling wheel...works fine.

---

### Post by iAndy on 2006-10-18
> **salguod said:**
> I use a USB two-button external mouse with a scrolling wheel...works fine.
It will do.  There are some issues with pure ease of use and simplicity on the Mac trackpads with Ubuntu.

I have just had Ubuntu dual-booted onto my PowerBook, the trackpad works "out of the box" but it is very very very slow and unsensitive!!  Scrolling across the screen takes ages!  A simple USB mouse solves that no problem, but for portability I need a fully functional trackpad.

Even a trackpad with better speed would be a start, wouldn't have to want the extra scrolls and right clicks yet!  (Anyone got any solutions?!)

Thanks for the pointers on the right click...been wondering how to do that for ages!

---

### Post by endy on 2006-10-26
I had to type "sudo modprobe trackpad" to get the trackpad sensitivity to work better, first time it didn't work so I actually had to "sudo rmmod trackpad" then "sudo modprobe trackpad" again. YMMV.

For me though, the trackpad isn't as touch sensitive as it is in OS X; in Unbuntu I seem to have to press down harder on it before it registers movement, and it's no where near as smooth as in OS X. This is on my Powerbook G4.

---

### Post by mr_forest on 2006-11-08
> **ORBiTrus said:**
> I don't have a Mac, but...

Probably not possible.  Do you know what driver it uses?  It could be in the documentation.  Or likely a simple code change.

Edit: I don't suppose the obvious two-finger tap or three-finger tap does anything?

i enabled multi-finger tap editing /etc/X11/xorg.conf as follows:
Comment out the "Synaptics Touchpad" section and put this one in place:

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "auto-dev"
        Option          "LeftEdge"              "50"
        Option          "RightEdge"             "840"
        Option          "TopEdge"               "30"
        Option          "BottomEdge"            "320"
        Option          "MinSpeed"              "0.2"
        Option          "MaxSpeed"              "1.0" 
        Option          "AccelFactor"           "0.1"
        Option          "SHMConfig"             "on"
        Option          "RTCornerButton"        "3"
        Option          "LTCornerButton"         "2"
        Option          "FingerLow"             "12"
        Option          "FingerHigh"            "20"
        Option          "MaxTapTime"            "120"
EndSection
```

This works for me on ibookg4 12", 1.33. don't know if working on other models.

hope this helps

---

### Post by llanitedave on 2006-11-09
I tried that script and it made no difference.  My trackpad is still very, very sluggish.  The usb mouse works great, though.

---

### Post by ivelasco on 2006-11-10
That is not a script.you must add it to the xorg.conf file,and be sure that it is correctly defined yn the server layout section also.

---

### Post by llanitedave on 2006-11-11
I DID add it to the xorg.conf file.  But I'm not familiar with the "server layout section."  How and where do I define it?

---

### Post by blue_chili on 2006-11-11
> **PsyCHZZZ said:**
> 
Here's how to do it.

1. Login as root.
1. Edit /etc/sysctl.conf.
3. Locate - 
    # Emulate the middle mouse button with F11 and the right with F12
    dev/mac_hid/mouse_button_emulation = 1
    dev/mac_hid/mouse_button2_keycode = 87
    dev/mac_hid/mouse_button3_keycode = 88

    and change the last keycode from 88 to 100.
4. Save the file and reboot.
5. To right+click, press Fn+Alt. :)

Credits to : [http://www.celsius1414.com/ubuntu_linux_on_ibook](http://www.celsius1414.com/ubuntu_linux_on_ibook)

Thanks! That's much easier than using f12!:)

---

### Post by defau1t on 2007-07-04
as was noted earlier in this post, i found that it was possible to use a three-finger tap to active the right click function on my iBook g4 12" 1.33 ghz

---

### Post by APU on 2007-07-04
Hi!

You can install the QSynaptics Package and configure your trackpad with a GUI Application. I used to configure my trackpad in the xorg.conf file as well and it worked OK, but now i have configured it using QSynaptics and its really fine to use now.

Currently I run Debian but I also used the app back in the Dapper Drake days so there should not be any problems. If you want the trackpad settings to persist after a reboot you have to put the command "qsynaptics -r" into your Startup Items or the Gnome/KDE equivalent (i use XFCE myself so I am not sure how this is called in other desktop environments).

---


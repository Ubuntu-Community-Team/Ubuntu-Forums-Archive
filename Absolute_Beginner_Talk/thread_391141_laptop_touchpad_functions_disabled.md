---
title: "laptop touchpad functions disabled"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by gonzo5680 on 2007-03-22
hi, on my laptop whenever it put it in suspend, on return my touchpad will loose function.  The overall sensitivity and speed will increase and the right side will also loose the abilities to act as a scroll wheel.

---

### Post by martinw89 on 2007-03-25
Hi Gonzo,
It appears that this may be related to several confirmed bugs:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84133](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84133)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86820](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86820)

At the moment there is a workaround I use, although it requires a little effort on your part after resuming.
First, edit your xorg.conf file to include the line *Option "SHMConfig" "true"* in the Synaptics Touchpad device section.  Make sure to make a backup first!
```
sudo cp /etc/X11/xorg.conf /etc/X11.xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
```So, for example, this is an excerpt from my xorg.conf```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
    **Option        "SHMConfig"        "true"**
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/wacom"    # Change to 
                            # /dev/input/event
                            # for USB
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

```This, in a nutshell, lets other programs change settings for your touchpad.  Restart your computer to let these changes take affect.  Now, get the program qsynaptics:
```
sudo apt-get install qsynaptics
```This program will not be in the menu by default but you can add it later if you want.  To run qsynaptics press Alt+F2 and type "qsynaptics" (without quotes).  Changing the settings and pressing apply always resets everything back to a working state for me after standby.  That should be it, hope this helps.

---

### Post by ceovsenik on 2007-03-25
yep, it works beautifully now =)

---

### Post by elusivespoon on 2007-04-05
So what exactly is the SHMconfig option? I have a similar issue where the scrollwheel on my mouse stops working after a suspend. I only noticed that I couldn't use my touchpad to scroll after reading a post here.

Is there a similar fix for my mouse scrollwheel?

---

### Post by martinw89 on 2007-04-05
I'm sorry elusivespoon, I don't have an answer to that.  I have a quick change to what I said above though.  The command "qsynaptics -r" reapplies all of your settings.  You can add this to your startup programs and you won't have any more problems.

---

### Post by DizzyTech on 2007-07-12
This is still happening with me, and the tip above doesn't work.

---


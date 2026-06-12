---
title: "Need Mouse Help"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by kyrhash on 2007-04-28
I am running Ubuntu (feisty) with VMware in WinXP to get used to it before i completely convert.  I am used to everything but i cant get my mouse to scroll.  Got Linux 2 days ago so go step by step.

---

### Post by Xarok on 2007-04-28
When you are using the live CD (without VMware) does the mouse sprolling work?

---

### Post by kyrhash on 2007-04-28
Correction I am using 6.10 edgy not fiesty

---

### Post by SoggyCornflake on 2007-04-28
> **kyrhash said:**
> I am running Ubuntu (feisty) with VMware in WinXP to get used to it before i completely convert.  I am used to everything but i cant get my mouse to scroll.  Got Linux 2 days ago so go step by step.
The most likely problem is due to your configuration file used for running Xwindows.  This is installed in the directory** /etc/X11** and is entitled **xorg.conf.**

You can use your favorite text editor to read this, but to change it you must be in "Super User" mode.


Open yours up. and scroll down to the InputDevice section and look to see if the "Protocol" for you mouse is "ImPS/2"  If it is not then you'll have to edit it.

For example, this is the relevent part of my xorg.conf
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

```

To edit it, use the same text editor, but open it from a command window by typing
```
sudo foo /etc/X11/xorg.conf.
```

save your newly edited xorg.conf file and restart your Xserver.  (The easiest way is to press **[Ctrl][Alt][Backspace]**)

---

### Post by SoggyCornflake on 2007-04-28
> **SoggyCornflake said:**
> To edit it, use the same text editor, but open it from a command window by typing
```
sudo foo /etc/X11/xorg.conf.
```

save your newly edited xorg.conf file and restart your Xserver.  (The easiest way is to press **[Ctrl][Alt][Backspace]**)

Oops - Foo was supposed to mean your favorite text editor..

And another thing.  You may want to make a copy of xorg.conf prior to making this change - just in case something get's messed up - it shouldn't - but you know it's not a bad idea.

---

### Post by kyrhash on 2007-04-28
what is the default text editor; i haven't changed it yet?

---

### Post by SoggyCornflake on 2007-04-29
> **kyrhash said:**
> what is the default text editor; i haven't changed it yet?

Honestly, I've forgotten.  Find a text file and open it by double clicking on it.  Your system should open it with the default text editor.

I have installed Ubuntu, but added the KDE GUI stuff and use **kate** as my text editor.  It has a lot of nice features for working with scripting files & source code.

---

### Post by kyrhash on 2007-04-29
yes that did the trick!  FYI the text editor was gedit.

---


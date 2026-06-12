---
title: "Need some help configuring my mouse with Xorg.conf"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Mardok45 on 2008-01-22
Here's my mouse section in my xorg.conf file:

Section "InputDevice"
     Identifier "Configured Mouse"
     Driver "mouse"
     Option "CorePointer"
     Option "Device" "/dev/input/mice"
     Option "Protocol" "ExplorerPS/2"
     Option "Resolution" "800" #optional
     Option "Buttons" "10"
     Option "ZAxisMapping" "4 5"
     Option "ButtonMapping" "1 2 3 6 7"
EndSection

Buttons 1, 2, 3, 4, and 5 work fine (Firefox can use the forward/back buttons perfectly), it's the 6th button that has some problems.

The model I have is the Logitech MX518.  The Application Switcher is the button that's not working the way I want it to.  It seems that Linux is detecting it as another middle mouse button, every application I try to use that button in acts just like the middle mouse button.

I want that button to be a completely separate button, there's some bindings I'd like to make to my Compiz-Fusion preferences.

Does anyone know what's wrong?  Or is it not possible to fix this?

---

### Post by ajmorris on 2008-01-23
Hi there,
you can try the patch here: [http://www.linux-gamers.net/modules/news/article.php?storyid=761](http://www.linux-gamers.net/modules/news/article.php?storyid=761)

or the how-to here: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Typhoon](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Typhoon)

or here:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+lomoco](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+lomoco)

then there is also this:
[http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

---


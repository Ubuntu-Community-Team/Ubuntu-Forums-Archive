---
title: "synaptics?"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Sugz on 2007-10-16
Hi all!
I've just been almost forced to use ubuntu by my university, but i am not at all unhappy about this :)
anyway, I use ubuntu on my Advent laptop, and ive been really annoyed at how the way Ubuntu uses my mouse, as Vista (synaptics) has all sorts of features. 
I have done alot of reading about how to enable or disable Syanaptics i believe this block of text needs to be present in my xorg.conf doc. 

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

heres the catch.. my config does not have this anywhere. all i have is Configured mouse. and Synaptics is no where to be seen anywhere? 

Any help will be greatly appreciated.

---

### Post by LowSky on 2007-10-16
just add it underneath the mouse  lines... FYI if it breaks your xorg, its not my fault

---

### Post by bodhi.zazen on 2007-10-16
See this thread : [http://ubuntuforums.org/showthread.php?p=975421](http://ubuntuforums.org/showthread.php?p=975421)

And this wiki page : [http://wiki.debian.org/?SynapticsTouchpad](http://wiki.debian.org/?SynapticsTouchpad)

---

### Post by bodhi.zazen on 2007-10-16
> **LowSky said:**
> FYI if it breaks your xorg, its not my fault

LOL

---

### Post by monado on 2007-10-16
I believe it should look like:
```
Section "InputDevice"
Identifier "Configured Mouse"     # Or "Configured mouse" ?
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection
```

Your config doesn't have it anywhere because it's not there :)
You can use the code that you posted if you replace every "Configured Mouse" to "Synaptics Touchpad" in your xorg.conf

And *please* make a backup of xorg.conf

---

### Post by Sugz on 2007-10-16
Oh ****!
yup you guessed it! ive screwed it up haha! i can no longer access my GUI, despite following the tutorial to the letter. 

OK so now i have a new problem, how to manually get into the xorg.conf file and edit the line that i have a feeling is wrong > damn it.. :mad: 

Again, (i think more before) any help WILL be greatly appreciated

---

### Post by Perfect Storm on 2007-10-16
```
 sudo nano /etc/X11/xorg.conf
```
to edit via CLI

[ctrl]+[o]=save
[ctrl]+[x]=exit

---

### Post by bodhi.zazen on 2007-10-16
Either :

1. Restore from back up. You did back up ?

[indent]If not, open a terminal and type :> I will back up system files before I edit them 100 times.[/indent]

2. Enter this command (selects defaults for everything but resolution)

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Sugz on 2007-10-16
lovely! thank you, ill try that now

---

### Post by Sugz on 2007-10-16
Fantastic im back in the game! i will now dish out 5 kick me up the *** cards. 
Ok, so now that i have control again i will backup the file in question and will try aghain to get Synaptics up and running, by the way will this be a easier process in 7.10?

---

### Post by arashiko28 on 2007-10-16
First of all, welcome to the Linux community!!!:guitar: Second, try to find a compatibility list with gusty and you laptop, as far as I've read, all those misdemeanors with touchpad and mouse, has been resolved, or in their most. If not, remember what you've just done and repeat it after you have installed gutsy, or better yet, just backup all your data and make an upgrade from terminal.:) Trust me, you'll forget all about windows.:lolflag:

---

### Post by Sugz on 2007-10-16
Lol, thaks you for those very encouraging words :) yeh i plan to upgrade straight to Gutsy in two days time. by the way at the moment im using wubi on Vista (which is fine) to run my Ubuntu, will i be able to upgrade to Gutsy with relative ease?

---


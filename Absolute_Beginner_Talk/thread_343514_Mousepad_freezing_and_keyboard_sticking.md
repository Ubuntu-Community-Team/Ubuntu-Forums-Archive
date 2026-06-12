---
title: "Mousepad freezing and keyboard sticking"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by ndworecki on 2007-01-21
Well i have a synaptic touch pad mouse i think. Well what happens is it freezes from time to time and it wont move for about 15 seconds.

Secondly my keyboard keys on my laptop tend to stick a lot, i don't mean pressed down because they aren't down but they continue to write that key, so i dont know what is going on.


I have a hp dv8000 laptop.



Thanx,
            Nathaniel

---

### Post by mikewhatever on 2007-01-21
I do not know how to fix the keyboard, but there is a good fix for the synaptics touchpad. I've got it installed on HP 5000 which should be similar to yours, just smaller. To install type the following in the terminal ```
sudo apt-get install gsynaptics
```
After that, you'll have a new entry: System->Preferences->Touchpad. In order to use it, you have to edit your xorg.conf file.
First back up: ```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
```
sudo gedit /etc/X11/xorg.conf
``` will open the file. Find the following section
```
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    **Option         "SHMConfig" "true"**
EndSection
```
add the line in bold to it, and save the file. Now you should be able to configure with the new Touchpad entry.

---

### Post by ndworecki on 2007-01-21
ive tried this and it didnt work for me any other ideas but thanx

---

### Post by mikewhatever on 2007-01-22
What version of Ubuntu have you installed?

---

### Post by ndworecki on 2007-01-23
6.10

---

### Post by nrwilk on 2007-01-30
> **ndworecki said:**
> ive tried this and it didnt work for me any other ideas but thanx

Yup, I have this all done as well, and my synaptics pad still "freezes" for about 5 seconds every 10 minutes or so.

I hate it.  I'm running Edgy and I'm all updated.  It never happened on the same machine in Dapper.  In dapper, the touchpad was absolutely perfect.

---


---
title: "Help!! synaptics touchpad mouse"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by ndworecki on 2007-01-16
on my dv8000 my mouse is freezing and not moving at periods of time and i dont know wut to do!!

its a synaptics touchpad or something, if u need more info i going to have to know how to get it



Thank you very much,
                                      Nathaniel

---

### Post by The Joe on 2007-01-16
Can you make this a bit clearer? Are you using Synaptics or are you getting an error about Synaptics?

---

### Post by ndworecki on 2007-01-17
im using a synaptics touchpad

---

### Post by mikewhatever on 2007-01-17
Have you tried installing gsynaptics: ```
sudo apt-get install gsynaptics 
```
Once installed, you'll get Touchpad entry under System->Preferences. To open it, you'll need to add this line: ```
 Option "SHMConfig" "true" 
``` to the touchpad section of your /etc/X11/xorg.conf file.

---

### Post by ndworecki on 2007-01-17
it cant find the file???

---

### Post by mikewhatever on 2007-01-17
I am sorry if I was not clear enough. To edit the file in question, you need to type the following command:
```
sudo gedit /etc/X11/xorg.conf
```
and then enter your password.
There is a lot of stuff in that file, so find the touchpad section and add the line. Below is the section from my xorg.conf file. The line in bold was manually added. Don't forget to save.

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    **Option         "SHMConfig" "true"**
EndSection

---

### Post by ndworecki on 2007-01-17
i had the problem with the install i wasnt clear sorry

the apt-get said that the file couldnt be found

---

### Post by mikewhatever on 2007-01-17
No wonder you did, I've mistyped gsynaptics. This is the right one:

```
sudo apt-get install gsynaptics
```

Sorry about that. Hope it works OK now, and I'd better edit the earlier post.

---


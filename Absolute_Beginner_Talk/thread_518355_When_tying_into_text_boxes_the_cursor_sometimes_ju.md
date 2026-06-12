---
title: "When tying into text boxes the cursor sometimes jump to another text box"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by mitchelljj on 2007-08-05
When typing into text boxes the cursor sometimes jumps to another text box, and other times if  I type too fast then the keystroke is not registered.  This happens in FireFox and it did not occur when  I used to have windows on this  computer.

Any suggestions?

Thanks,

John

---

### Post by jackmc on 2007-08-06
its a stretch, but are you using a laptop? qsynaptics may help. I had an issue when I was typing, and accidentally touched the mousepad that sounded similar

---

### Post by mitchelljj on 2007-08-08
Yes, I am using a laptop.

What is qsynaptics?

Thanks,

John

---

### Post by WakkiTabakki on 2007-08-08
Yup, jackmc. Sounds very familiar, I do it all the time (sometime making document totally unreadable). qsynaptics is a great tip, I'll try it straight away!

Mitchelljj, you can read about it here:
[http://packages.ubuntu.com/feisty/x11/qsynaptics](http://packages.ubuntu.com/feisty/x11/qsynaptics)
and here
[http://qsynaptics.sourceforge.net/](http://qsynaptics.sourceforge.net/)

Install by writing the following in a terminal:
```
sudo apt-get install qsynaptics
```
You need to have the 'universe'-repository enabled (check under the menu 'System/Administration/Software Sources').

Good luck
/N

Edit: Mitchelljj, once installed, you start the configuration by typing this in a terminal window
```
qsynaptics
```
Enabling the smart tapping under the Tapping tab would be the way to solve your problem...

Edit 2: WICKED! Apparently my touchpad supports multi-finger tapping! I've now configured two-finger tap as middle button, and three fingers as right mouse button. Thanks jackmc, you've so totally geeked my day :D

---

### Post by notwen on 2007-08-08
I'm having similar issues, but when I download qsynaptics and start it, none of the options are available and are greyed out.  Here is the output when I run it using sudo

```
notwen@notnix-ii:~$ qsynaptics
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
users home is /home/notwen
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
restore old settings...
syndaemon: no process killed
Can't access shared memory area. SHMConfig disabled?
retVal is 0
notwen@notnix-ii:~$ sudo qsynaptics
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
users home is /home/notwen
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?
Can't access shared memory area. SHMConfig disabled?

```

---

### Post by WakkiTabakki on 2007-08-09
Have you got your touchpad device properly configured in /etc/X11/xorg.conf?
This is how my section looks like
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/mouse0"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection

```

I think the "SMHConfig"-line could be the trick...

/N

---

### Post by mitchelljj on 2007-08-11
Hi,

I tried to configured /etc/X11/xorg.conf, but it says that I am not the owner.  The owner is root.  How do I log on as the root owner?

Thanks,

John

---

### Post by WakkiTabakki on 2007-08-12
'sudo' does the job...
```
sudo gedit /etc/X11/xorg.conf
``` 

/N

---

### Post by schorsch on 2007-08-12
It's better to use

```
gksudo gedit /etc/X11/xorg.conf
```

...

---

### Post by mitchelljj on 2007-08-12
> **WakkiTabakki said:**
> Have you got your touchpad device properly configured in /etc/X11/xorg.conf?
This is how my section looks like
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/mouse0"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection

```

I think the "SMHConfig"-line could be the trick...

/N


The Qsynaptics application is still greyed out after doing the above and it still says to "please install the synaptics touchpad driver  and please enable X shared memory config in XF86Config"

---


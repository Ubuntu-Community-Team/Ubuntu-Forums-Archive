---
title: "Lucid/aiptek"
date: 2011-10-30
forum: Art &amp; Design
---

### Post by mystmaiden on 2011-10-30
It's been ages since I used my tablet so I wanted to set it up again. Things have changed a lot since I did it the last time so I'm a bit fuzzy on the instructions and needing a little hand holding. From the Ubuntu help pages [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet)  I found - 
 > at startup, udev by default will identify our tablet as an evdev input  device, so we must write an udev rule to tell xorg to load aiptek  driver: in /lib/udev/rules.d add a file (e.g. 69-xserver-xorg-input-aiptek.rules) with something like this: 

```
ACTION!="add|change", GOTO="xorg_aiptek_end"
KERNEL!="event[0-9]*", GOTO="xorg_aiptek_end"

ATTRS{idVendor}=="08ca", ENV{x11_driver}="aiptek", SYMLINK+="input/aiptektablet"

LABEL="xorg_aiptek_end"
```

There is another file to create as well. How exactly do I create them though? I already messed up once by thoughtlessly trying to configure it like I did on other versions of Ubuntu and as a result some of the applets I use on the tool bar disappeared or were broken ( I *think* I have all that fixed now.)


thanks in advance

mystmaiden

---

### Post by mystmaiden on 2011-10-31
Giving this a little bump. I should have said that what I need is the command line to create the needed file, I really didn't say it clearly

thanks in advance

---

### Post by Favux on 2011-10-31
Hi mystmaiden,

You have to be root (sudo) to create a system file.  Since you'll want to use gedit, which is a gui based editor, you want to use gksudo, so:
```
gksudo gedit /lib/udev/rules.d/69-xserver-xorg-input-aiptek.rules
```
Just copy and paste the contents in and Save.

To be sure it is an Aiptek tablet look for the tablet line in the output of:
```
xinput list
```
or
```
lsusb
```

---

### Post by mystmaiden on 2011-10-31
Thanks so much, Favux.

Here is the output of xinput

```
 Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=9    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=8    [slave  keyboard (3)]

```

and lsusb
```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

No mention of aiptek...

---

### Post by Favux on 2011-10-31
It is a usb tablet, correct?  Was it plugged in?  If not plug it in and rerun *lsusb*.

---

### Post by mystmaiden on 2011-11-02
Favux, 

thanks again - plugged it in and all is well

```
mystmaiden@hal:~$ lsusb
Bus 003 Device 002: ID 08ca:0021 Aiptek International, Inc. APT-2 Tablet
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

It's working now, better than it used to.

---


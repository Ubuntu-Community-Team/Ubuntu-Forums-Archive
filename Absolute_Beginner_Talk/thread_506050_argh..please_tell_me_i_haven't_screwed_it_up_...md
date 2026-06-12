---
title: "argh..please tell me i haven't screwed it up .."
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2007-07-21
if i run ktorrent or deluge nothing happens - i get the spinning 'wait' icon on my mouse pointer and nothing.

i've done 

apt-get update
apt-get upgrade
apt-get check
apt-get clean

all with no problems, i've rebooted and still nothing ..

even if i sit and wait for 5 minutes in case it's taking it's time to load up - nothing happens.

---

### Post by swoll1980 on 2007-07-21
> **jasonwatkins said:**
> if i run ktorrent or deluge nothing happens - i get the spinning 'wait' icon on my mouse pointer and nothing.

i've done 

apt-get update
apt-get upgrade
apt-get check
apt-get clean

all with no problems, i've rebooted and still nothing ..

even if i sit and wait for 5 minutes in case it's taking it's time to load up - nothing happens.

run it from a terminal see if you get an error message if you do let us know if it runs from the terminal than its a messed up link we can fix it

---

### Post by jasonwatkins on 2007-07-21
you're psychic because that's exactly what i've just done :)

> Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
Qt: Warning: QServerSocket: failed to bind or listen to the socket

*edit

I did try running the script to compile and run the CVS Cedega package earlier on, so i don't know if that's created any problems or conflicts ..

---

### Post by swoll1980 on 2007-07-21
When I run my ktorrent in a terminal I get the same error but it opens anyways. I can't figure that one out. It happens when I run virtualbox and kate too. and opens them  anyways

---

### Post by Nythain on 2007-07-21
> **swoll1980 said:**
> When I run my ktorrent in a terminal I get the same error but it opens anyways. I can't figure that one out. It happens when I run virtualbox and kate too. and opens them  anyways
its going to happen anytime you run any graphical program from the terminal untill you comment out a couple useless sections of your xorg.conf... basically its trying to initialize the wacom drivers for tablet pcs... if you really want to get rid of those errors (wich have nothing to do with your problem) you can edit your /etc/X11/xorg.conf file to look something like this
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
EndSection
...
...
#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "stylus"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "stylus"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "eraser"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "eraser"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "cursor"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

```
that will cure your bad device errors, but i cant help you much with deluge/ktorrent

---

### Post by benx009 on 2007-07-21
> **jasonwatkins said:**
> if i run ktorrent or deluge nothing happens - i get the spinning 'wait' icon on my mouse pointer and nothing.

i've done 

apt-get update
apt-get upgrade
apt-get check
apt-get clean

all with no problems, i've rebooted and still nothing ..

even if i sit and wait for 5 minutes in case it's taking it's time to load up - nothing happens.

are you trying to run ktorrent in gnome or kde?  if in gnome, do you have kde installed???  if not, ktorrent will not work.

---

### Post by kostkon on 2007-07-21
> **benx009 said:**
> are you trying to run ktorrent in gnome or kde?  if in gnome, do you have kde installed???  if not, ktorrent will not work.

Actually you don't need to install the whole KDE only the KDE libs, whatever that actually means.

---

### Post by jasonwatkins on 2007-07-22
> **benx009 said:**
> are you trying to run ktorrent in gnome or kde?  if in gnome, do you have kde installed???  if not, ktorrent will not work.

i assume i'm running it in gnome because i'm just double clicking the icon on the desktop - it had previously run with no problems, so i really couldn't figure out what i did to basically kill it.

anyway, i've found that deluge is working fine at the moment, so i've just uninstalled ktorrent and i'll go with deluge for now.

---


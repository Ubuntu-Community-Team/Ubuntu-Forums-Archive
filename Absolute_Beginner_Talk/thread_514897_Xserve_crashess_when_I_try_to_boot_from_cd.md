---
title: "Xserve crashess when I try to boot from cd"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by tricyclethief on 2007-08-01
I am trying to install Ubuntu. At first I had a problem during boot with it saying "/bin/sh: can't access tty; job control turned off". I did the following from the thread [http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control](http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control)

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

It worked up to a certain point. Then the screen turned all blue and white and said something about Xserve not working. From what I've read this has something to do with graphics. I have a Nvidia GeForce 8400. I don't really know what to do.

---

### Post by eapache on 2007-08-01
You've solved the first problem, and the second problem should be fairly simple. After the error message, it should dump you to a command prompt. Type the following:
```
sudo nano /etc/X11/xorg.conf
```
This should open a basic text editor. Please scroll down to the sections that say "Device" instead of "InputDevice" and copy those sections here.

---

### Post by tricyclethief on 2007-08-01
Section "Device"
[INDENT]Identifier "nVidia Corporation NVIDIA Default Card"
Driver    "nv"
BusID      "PCI:1:0:0"[/INDENT]
End Section

---

### Post by eapache on 2007-08-01
Is there a section for "Monitor" and "Screen" as well? (I don't need all the screen subsections, just the first few lines).

---

### Post by tricyclethief on 2007-08-02
Section "Screen"
[INDENT]Identifier "Default Screen"
Device "nVidia Corporation NVIDIA Default Card"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"[INDENT]Depth 1
Modes "1280x800" "1024x768" "800x600" "640x480"[/INDENT][/INDENT]

This continues for Depths through 24.

Thanks for helping :)

---

### Post by eapache on 2007-08-02
This is very odd, as it appears to be configured correctly. I have several things you can try. First, near the top of the xorg.conf file is a section of modules. Make sure that one of the lines loads the "nv" module. If not, try adding that line, use ctrl-o to save, ctrl-x to exit, then use the command
```
startx
``` to try restarting the crashed display.

If that crashes as well, try the following: ```
sudo apt-get install nvidia-glx
``` Then go back into xorg.conf and make sure that the "glx" module is listed. Also, change the driver listed for your graphics card from "nv" to "nvidia". Finally, in the screen section, between the monitor line and the default depth line, add ```
Option "RenderAccel" "true"
``` Save and exit, then run ```
startx
``` again. If this doesn't work either, could you please examine the error message and see if you can find any bits that look important.

---


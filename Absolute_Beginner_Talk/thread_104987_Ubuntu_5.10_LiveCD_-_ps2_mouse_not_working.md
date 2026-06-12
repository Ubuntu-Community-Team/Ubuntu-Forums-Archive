---
title: "Ubuntu 5.10 LiveCD - ps/2 mouse not working"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by PilotEd on 2005-12-17
Greetings..I've just booted (using LiveCD) and the ps/2 mouse is not working.  I'm using a laptop with a touchpad that works fine.

The same hardware works fine with DSL 2.0 so it appears to be a configuration issue.

Suggestions?

---

### Post by Gurgeh on 2005-12-17
I had problem with the live CD, ran it on my desktop nothing worked - bit the bullet and installed it, ran fine. Bit weird that....

---

### Post by bscbrit on 2005-12-17
I do not know about your laptop specifically, but I have one where I must choose between the touchpad and the external mouse by pressing a CTRL-ALT-Function button, if I remember correctly.
As it seems to have detected the touchpad, might you also have to tell the live disk to look for your external mouse?  Just a guess.

---

### Post by PilotEd on 2005-12-17
Thanks, Gurgeh and bscbrit, for the feedback.

I have installed to the HD but the mouse still doesn't work.

The laptop doesn't have a ctrl-alt function to activate the proper mouse and I'm not familiar on how to tell the os to look for the mouse.

Hmmm....

---

### Post by bscbrit on 2005-12-17
Please post the contents of your /etc/X11/xorg.conf, or at least the section of that file relating to the mouse set up.  Lets see if we can find something there that will help solve this problem.

---

### Post by PilotEd on 2005-12-17
Here are the mouse sections of the xorg.conf file.  These are as-is from the install process (ie, there have not been any changes).


Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection


FYI...there have been quite a few postings on this forum regarding ps/2 mouse problems...

---

### Post by bscbrit on 2005-12-18
Try commenting out the section regarding the touchpad mouse and restarting X.  Of course, if you do and it doesn't solve your problem you will have to recover to the previous configuration without using a mouse!  A backup is always wise before any changes (Why do I rarely listen to my own advice?......)
Other than that, I haven't got much to offer in resolving this problem.  I wonder if there is a 'mouse guru' out there?

---

### Post by PilotEd on 2005-12-18
Tried your suggestion to no avail...I did keep a copy of xorg.conf before making the change so recovery wasn't too bad....

I'm very open to any other suggestions.....

---

### Post by bscbrit on 2005-12-18
unfortunately, I've run out of intelligent suggestions on this one.  And as it's been viewed by 43 other people and no-one has made any offerings I suspect that nobody has anything to say.  I'll go and do a bit of googling or pull one of the big books from off my bookshelf.

---

### Post by bscbrit on 2005-12-18
I've just been googling, and some problems with a PS/2 mouse have been cured by changing IMPS/2 to PS/2 in xorg.conf.  Worth a try....

---

### Post by PilotEd on 2005-12-18
Changing from imps/2 to ps/2 didn't work...

---

### Post by PilotEd on 2005-12-19
After hours and hours of googling and trying various things, a fix has been found!

Modify the /etc/modules file and add proto=bare to the psmouse line.  My modified /etc/modules file is shown below:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with '#" are ignored.

lp
mousedev
psmouse proto=bare


------
Source:
[http://www.redhat.com/archives/fedora-test-list/2004-February/msg00717.html](http://www.redhat.com/archives/fedora-test-list/2004-February/msg00717.html)

Phew!!!

---

### Post by bscbrit on 2005-12-19
Well I'm glad that you've got it sorted.  I have never seen proto=bare before, I will have to add it to my list.

---

### Post by PilotEd on 2005-12-19
Thanks for your assistance and helpful websites that were provided...

---

### Post by gesho on 2006-05-23
i tried both: change xorg.conf
ImPS/2 to PS/2
and changing /etc/module

still my logitec ps/2 mouse doesn't work

---


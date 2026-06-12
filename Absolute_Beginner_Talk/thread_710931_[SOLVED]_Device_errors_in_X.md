---
title: "[SOLVED] Device errors in X"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-02-29
I seem to get the following errors, or ones very similar, quite often.  This one happened when I just logged in and did gksudo ls -al.  In fact, if I just type gksudo and press enter, I get the same errors before I get prompted (using KDE) for what I wanted to run.


I also get this or very similar errors when starting up a process I must have running before I use Skype.  The author of that process says the error is not from the program.

Any ideas what's going on?  I assume I probably have something set wrong again.  :)



X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


EDIT:

Here's the errors when I start the other application:

dave@dave-desktop:~/usb_telbox/driver$ kb2kskype
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by gimfred on 2008-02-29
I vaguely remember they were attributed to a usb device. I had them and they never seemed to stop anything from working. If I remember correctly this occurs when you start a windowed program from the command line?

---

### Post by anewguy on 2008-02-29
> **gimfred said:**
> I vaguely remember they were attributed to a usb device. I had them and they never seemed to stop anything from working. If I remember correctly this occurs when you start a windowed program from the command line?

The starting a windowed program from the command line would apply to the second case, but not to the gksudo.  Also, curious about the USB devices.  Could it be that I have 2 USB devices that currently aren't powered on - specifically my scanner and my printer?  I'll do some testing and report back.

Thanks! :)

EDIT:

Well, it's not the printer, not the scanner and not my USB telephone box.  It would seem to indicate some device error in X.    I'm wondering if it's the waccom stuff  since for some reason they are mentioned as input devices in my xorg.conf.   I'll try taking them out next and restarting X, then posting back here.


EDIT-EDIT:  Problem solved.  Not USB devices at all, but the waccom tablet devices defines in xorg.conf still be defined as input devices for the session.  Removed those definitions in xorg.conf and the errors went away.

---


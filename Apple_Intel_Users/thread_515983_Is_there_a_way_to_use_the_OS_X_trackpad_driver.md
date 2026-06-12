---
title: "Is there a way to use the OS X trackpad driver?"
date: 2007-08-02
forum: Apple Intel Users
---

### Post by bitsent on 2007-08-02
I've been using Ubuntu 7.04 on a MacBook as my main computer for a month now, and I love it.  However, I just cannot get the mouse to work well.  Everything works--two-finger clicking, scrolling, lower enter key as right click, etc., but the appletouch driver has a lot of quirks and does not feel right.  The problems are so significant that my wife won't even use Ubuntu on her MacBook until they're fixed.  I won't go into the specific problems here because I've already scoured the forums and Google and spent many days tweaking [FONT="Courier New"]/etc/X11/xorg.conf[/FONT]

My question is:  is there any way to run the actual OS X trackpad driver (or the Windows one from BootCamp)?  Something similar has been done for network card drivers from Windows (ndiswrapper), but I hadn't heard of doing this for mouse drivers.  Any ideas?

---

### Post by cyberdork33 on 2007-08-02
nope you are pretty much stuck with synaptics. This is still new hardware for macs, bugs are being worked out. Give it some time.

---

### Post by benanzo on 2007-08-02
The **appletouch** driver is the low-level kernel module that talks directly with the touchpad hardware.  It receives (raw) data when you move your finger which it then passes to the **synaptics** X.org module for interpretation.  Once the **synaptics** module figures out what to do with the data it passes its instructions onto the other relevant parts of the X server and then you see your cursor move, or you click a button, etc.

There are (baring hardware failure) two possible places that spawn erratic trackpad behavior: the kernel module (appletouch) or the X.org module (synaptics.)  If it's the kernel module that's causing the problems it's usually because the communication with the hardware is spotty, or it's misinterpreting touch-actions and passing bad data to the synaptics module, which then passes bad instructions to X, which then makes your mouse jump around the screen for 5 seconds, or freeze altogether.

If it's the synaptics module that's causing the problems, it's almost always caused by misconfiguration.  The easiest way to figure out if the problem is one or the other is simply to determine if the erratic behavior is intentionally duplicatable.  If the appletouch kernel module is the culprit you'll almost never be able to instigate bad behavior by performing some repeatable action on the touchpad.  If the synaptics module is the bad guy, you'll almost always be able to repeat the problem intentionally.

I have a first-gen MacBook and, I must say, I don't have any trouble with the appetouch module.  Any problems I've had have been exclusively the fault of synaptics.

If you haven't already, have a look [here]("http://ubuntuforums.org/showthread.php?t=493758") to see if there's any configuration change you should make.

Good Luck!

---


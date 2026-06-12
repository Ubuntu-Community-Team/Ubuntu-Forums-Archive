---
title: "USB keyboard issue / Monitor recognition?"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by nowinvisibly on 2005-10-10
In [my earlier thread ]("http://ubuntuforums.org/showthread.php?p=399209#post399209") I had an issue installing Ubuntu.  

Turns out, in the installation, the installer program would not recognize my USB keyboard.  Plugging in my old PS/2 keyboard solved the problem.  After install, I could use my USB keyboard and mouse.

The only problem that I have is with my monitor.  

I use a KVM switch to share my keyboard, mouse and monitor between my PC box and my Mac.  After the install, I can use the KVM switch with Ubuntu just fine, recognizing both the mouse and the keyboard.  It recognizes the monitor, however it doesn't allow me to adjust the resolution.  The only option that I'm given in the screen resolution preference is "640x400" at 60Hz.  When pulling down the options, there are no other options to choose.  

Is there any way to manually add my monitor or force a specific resolution to it?

Your help is greatly appreciated!
:)

---

### Post by mlomker on 2005-10-10
Try

```

sudo dpkg-reconfigure xserver-xorg

```

Take the defaults if you're not sure about an answer.

---


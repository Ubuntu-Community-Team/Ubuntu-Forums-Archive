---
title: "OpenGL Overlay"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-09-27
What is this? Im looking at the etc/x11/xorg.conf file and it says 

[I]Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off" [/I]

What does it do? What will happen if I enable it?

---

### Post by got_nix on 2006-09-27
I've been wondering the same thing.. and the problem that led me to check out my xorg.conf file is my system was randomly logging me out and returning me to gdm login i stated timing it and realized that its always the same time interval from when i leve the system idle and immediately figured "screen saver" i'm wondering if it has anything to do with opengloveerlaying and it being disabled.. the screensaver needs it so it crashes gdm when it tries to invoke it and realize its not available.

---


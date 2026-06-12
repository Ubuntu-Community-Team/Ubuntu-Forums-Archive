---
title: "Non-USB Sidewinder"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by pmooney78 on 2008-02-15
Xubuntu auto-detected almost all of my hardware when I switched over from Windows. It did a far better job than Windows did, in fact. But one of the two pieces of hardware that didn't get auto-detected was my gamepad: a non-USB Microsoft Sidewinder. (That's the standard Sidewinder, not one of the later derivatives.) It's plugged into my sound card (an Ensoniq ES1371 built into the motherboard), not into a USB port.

Yes, I know this is an old gamepad. Is there anything I can do to get it to work? Everything I've been able to find refers to the USB Sidewinder and/or asks me to compile software. (I know what compilation means, and had some [hobbyist-type] experience programming classic Mac OS 7.x ten or twelve years ago, but would hesitate to try to recompile the Linux kernel as my first programming experience since then.)

I'm running Xubuntu 7.10, kernel 2.6.22-14-generic, on a 550MHz Pentium III. My current version of Xfce is 4.4.1.

---

### Post by Sam Lars on 2008-02-15
I too have a gameport joystick...
[http://ubuntuforums.org/showthread.php?t=338457&highlight=game+port+joystick](http://ubuntuforums.org/showthread.php?t=338457&highlight=game+port+joystick)
I haven't gotten it working yet, but maybe that will help you...

---

### Post by pmooney78 on 2008-02-16
Thank you, that gets jscalibrator to read the gamepad, but I have to do this in a terminal after every reboot:

sudo modprobe joydev
sudo modprobe ns558
sudo modprobe sidewinder

Doesn't seem to matter whether I modify the files /etc/modules, /etc/modules.conf, and /etc/modprobe.d/options, as the author of the post suggests ... I still have to execute the above commands every time I boot. Any suggestions on making the modules load automatically?

Thanks again,
Patrick

---


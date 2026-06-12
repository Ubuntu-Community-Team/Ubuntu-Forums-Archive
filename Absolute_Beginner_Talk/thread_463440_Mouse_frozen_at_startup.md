---
title: "Mouse frozen at startup"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by jankind on 2007-06-03
Hi all,
First post for me. 
I've been doing my homework on Ubuntu for a few months now and finally took the plunge this week. Did a dual boot install with XP and have had a really positive experience so far. Very few problems... I know I'll have a few questions for everyone so I'll keep this one short...

My Logitech USB mouse is frozen at startup but if I simply unplug and plug it back in, it's fine. This is not a huge issue for me since that is such an easy fix, but I'm trying to convince my wife why this is better than using XP and well... this is a red flag for her. ;) 

Is this common, or is there an easy fix?
Thanks!

---

### Post by pappapump on 2007-06-03
Are you using any other USB devices?
Mine hangs when I try to use my USB wireless stick.

---

### Post by jankind on 2007-06-03
> **pappapump said:**
> Are you using any other USB devices?
Mine hangs when I try to use my USB wireless stick.

At the moment the only USB devices I have are the mouse and keyboard.

---

### Post by aidanr on 2007-06-03
i don't know any solution, but there's a workaround you could try

```
sudo gedit /usr/local/bin/mousefix
```
```
#!/bin/bash
rmmod usbhid && modprobe usbhid
```
```
sudo chmod +x /usr/local/bin/mousefix
```
```
sudo visudo
```
add the following to the end of the file
```
%admin ALL=(ALL) ALL, NOPASSWD:/usr/local/bin/mousefix
```
and then go to system -> preferences -> sessions -> startup and add sudo mousefix

edit:// just did a bit of googling there because this has come up before, and a few suggestions were: make sure it's plugged into the motherboards usb not a hub, check the bios for options relating to usb, use a usb/ps2 adapter and also there's a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84762")

---


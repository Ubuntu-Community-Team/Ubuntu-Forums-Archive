---
title: "USB support in Wine?"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by pointyblue on 2007-09-30
Do any of you know how to make usb work in Wine?

Or is there a better script for making usb work for Windows programs in linux?

---

### Post by Linux_Man on 2007-09-30
Just save them to your virtual C drive then copy and paste to your USB drive that would the the easiest solution

---

### Post by pointyblue on 2007-10-25
No what I mean is I want to plug a piece of hardware (a gps) in to the usb port and make Wine detect it. Any ideas?

---

### Post by zakeen on 2007-10-25
I need help with this too. I hope someone can help.

---

### Post by pointyblue on 2007-10-25
Hi Zakeen,

What is it you are trying to get to work with Wine?

---

### Post by zakeen on 2007-10-26
Ive got a program that  has a device that downloads data via a serial USB adptor.

When I connect the usb serial adptor I see it in the "deivce manager" So Im assuming it works, but not in wine.

does that make sence?

---

### Post by pointyblue on 2007-10-26
I know exactly what you mean. It's like Wine doesn't know the USB ports exist.

In this thread [http://ubuntuforums.org/showthread.php?p=3633412#post3633412](http://ubuntuforums.org/showthread.php?p=3633412#post3633412) rdoolen tries to help out with an idea on what to do. I haven't had the time to find out exactly what it is I'm supposed to do just yet so I don't know if it works.

Please post back if you solve the problem.

---

### Post by zakeen on 2007-10-26
Thanks, I will have a go at this tonight and keep you updated how I go.

---

### Post by gecko94 on 2007-10-29
You need to create a symbolic link from COM device to TTY like this:
```

l n -s /dev/ttyUSB0 ~/.wine/dosdevices/com2

```
This will create the symbolic link from COM2 to ttyUSB0.

---

### Post by zakeen on 2007-10-30
Ive made these links and I can see them in tde dosdevices directory but it seems to do nothing. Is there a way in wine to test if these links work?

---


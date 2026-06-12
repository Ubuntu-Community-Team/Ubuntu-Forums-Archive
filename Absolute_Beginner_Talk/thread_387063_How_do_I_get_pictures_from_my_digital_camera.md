---
title: "How do I get pictures from my digital camera?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by MysticAurora on 2007-03-17
Hi. I have a Canon PowerShot A430 and since Windows didn't want to cooperate and get the pictures from my camera, I figured Linux would be able to do it with less fuss. I'm currently running Xubuntu and the cam is connected through USB. What do I need to do to get the pictures off of my camera? I've plugged it in and turned it on, but nothing seems to recognize it like it does with CDs. And I don't know how to mount a cam..

Any help would be greatly, greatly appreciated. I'm at my wit's end.

---

### Post by oilchangeguy on 2007-03-17
it's great you're giving linux a try. but why would you ditch windows just because it would not get pics from your camera? what version of windows were you running? do you have the cd that came with the camera? and did it ever occur to you to go to canons website and download the driver?

---

### Post by MysticAurora on 2007-03-17
Oh, I still have Windows on another hard drive. I'm just trying everything I can think of to get the pictures from my camera without having to buy an SD card reader. I tried using the software that came with the camera, but I could never get access to the camera because it said "Camera is in use by another program." I restarted, canceled processes, tried the built-in Windows programs... everything I could think of. I uninstalled the camera and software and reinstalled just to make sure. Windows has proven that it cannot do the job for me. The only thing I _haven't_ done so far is contact Canon's Tech Support.

---

### Post by oilchangeguy on 2007-03-17
sd readers are cheap. and with xp you'll have to load a driver cd for it to work. and in ubuntu it should put an icon on your desktop when you plug the reader in.

---

### Post by johnc4510 on 2007-03-17
With your camera hooked up to the usb, type this in a terminal:
lsusb
This should tell you what devices are hooked up via usb.

If it is not listed, try rebooting with camera attached to the usb.

---

### Post by maxamillion on 2007-03-17
If you are running Xubuntu, you will need an application life F-Spot or gThumb to import pictures (both available in the repositories)

---

### Post by MysticAurora on 2007-03-17
Okay, I checked to see if it was there using 'lsusb', and it is. The output relevant to it is:

```
Bus 001 Device 011: ID 04a9:30f8 Canon, Inc.
```

What can I do with this info?

---

### Post by johnc4510 on 2007-03-17
When you put a cd in, does it show the mounted volume on your desktop?

---

### Post by MysticAurora on 2007-03-17
Yeah, the CD appears on the desktop, but it only contains software for Windows/Mac. Nothing for Linux.

---

### Post by johnc4510 on 2007-03-17
I guess I am confused, does the camera show a mounted volume like the cd does? If it does, just right click on the volume icon and select open with. Probably fspot or gthumb.

---

### Post by MysticAurora on 2007-03-17
Nah. The camera isn't displayed on the Desktop. Only the CD. 'lsusb' shows that it detects the camera in the port, though.

---

### Post by oilchangeguy on 2007-03-17
the usb card reader is the way to go. it's faster. and you won't run down the camera battery. and you can always use a memory card for easy document storage. and a memory card fits easily in your pocket.

---

### Post by MysticAurora on 2007-03-17
Well I'd like to avoid that if I can. I mean, I've already found a nice one for ~$22, but isn't there a way I can mount the camera and get the pictures that way?

---

### Post by johnc4510 on 2007-03-17
Open your home file browser and click on the Computer Icon along the title bar and see if the camera is listed there.

---

### Post by oilchangeguy on 2007-03-17
found this about an a630
[http://www.ubuntuforums.org/showthread.php?t=372132&highlight=digikam](http://www.ubuntuforums.org/showthread.php?t=372132&highlight=digikam)

---

### Post by jcconnor on 2007-03-18
My camera was working perfectly - I could get pictures off of it with the Picasa2 software running under wine (which I recommend by the way) but it quick working over the last few days.

It was acting just like yours - would show up in dmesg as a device and in lsusb but I couln't get to the pictures.  Picassa would recognize it but it wouldn't see any photos.

A quick search brought up a bug that occurred over the last few days.

Go here

[https://launchpad.net/ubuntu/+source...to2/+bug/91250]("https://launchpad.net/ubuntu/+source...to2/+bug/91250")

And see if that fixes it for you.

It worked for me.

John

---

### Post by DougieFresh4U on 2007-03-18
I am running Xubuntu-Feisty and I just plugged my camera into USB and icon appeared on desktop which I clicked open and pictures I got using GQview !!

---


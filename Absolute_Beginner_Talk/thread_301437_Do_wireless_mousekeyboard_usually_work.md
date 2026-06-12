---
title: "Do wireless mouse/keyboard usually work?"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Sunnz on 2006-11-17
I have got a Logitech bluetooth mouse/keyboard, I am wondering if it usually work like in live mode on Ubuntu 6.06?

Thanks.

---

### Post by izmaelis on 2006-11-17
If it works on Ubuntu 6.06 LiveCD then it should be no problems using it on installed Ubuntu. As far as I know it is no difference is mouse/keyboard, actually, cordless or not. Bluetooth signal is used just to replace cord and USB takes all the hard part of enbling a device.

---

### Post by Sunnz on 2006-11-17
It doesn't quite work with Live CD.

It worked before the login thing.

It stops working as soon as the splash screen comes up.

---

### Post by Sunnz on 2006-11-18
So, anyone know what should I do?

Is this a usual problem on Ubuntu?

I am actually trying to install this on a friend's computer who is using Windows... but without the keyboard and mouse... well, I guess he'll stick in Windows hell. (I'll might try Mepis or Gentoo though I really hope to get this to work, Ubuntu is the best.)

---

### Post by Nightdrive on 2006-11-19
I have got a cheap cordless mouse and keyboard working (though not in GRUB), but as soon as I tried switching to a Belkin bluetooth kb and mouse, I have little success. I can get them to work for a while, by issuing a sudo hidd --search command, but once they go into sleep mode, it's pretty random whether they'll wake up, and if the PC reboots, they stop working. I've had numerous advise on how to get the hidd command to run on startup, but none have been successful.

See my post
[http://ubuntuforums.org/showthread.php?t=293753&highlight=bluetooth+keyboard]("http://ubuntuforums.org/showthread.php?t=293753&highlight=bluetooth+keyboard")

Good luck, but I don't think anyone on this forum has the answers.

---

### Post by Sunnz on 2006-11-19
So, may I conclude that if you have a wireless keyboard/mouse, that you are not ready for Linux?

---

### Post by Scorpuk on 2006-11-19
I'm not sure, but I would hazzard a guess that an RF wireless keyboard and mouse would work as that is independent of the OS.

Only bluetooth requires you to setup the device, whereas an RF, radio frequency, type only requires you to press buttons to get the two devices to connect.

The only downside to this version is the range of the device. :)

---

### Post by lorenzo on 2006-11-19
I have got a Logitech bluetooth mouse/keyboard too! They are connected to the PC via USB. So I suppose no bluetooth configuration is needed.... The keyboard is recognised by the bios (i suppose) since in grub I can use it. But in Ubuntu/gnome: no way!

Any idea? I reeeeeeeeeeeeally would like to use it....

Thanks,
Lorenzo

UPDATE:
It works! I was trying to connect it to the usb port of the docking station, and it does not work. But if I plug it directly to the usb port of the laptop it works fine. Nothing to configure. It is recognised as a normal usb keyboard/mouse.

---


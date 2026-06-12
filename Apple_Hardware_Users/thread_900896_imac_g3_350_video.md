---
title: "imac g3 350 video"
date: 2008-08-25
forum: Apple Hardware Users
---

### Post by markosjal on 2008-08-25
I have Ubuntu 6.06 installed on an imac G3 350. As far as the OS goes all seems well. However, I can not seem to change the monitor refresh , nor resolution. The 1024x768 75 hz is the only option. Also , I also would like to manage color depth as 32 bit depth can cause a substantial performance hit over say 16 bit graphics.  

I was wondering if perhaps the installer did not install the right Driver????

How can I check what it is supporting? I do not know for sure if this has the ATI Rage Pro or the earlier video , and how might I confirm this? I have seen  a lot of conflicting information on these slot loading blue imacs from the late 2000.

Mark

---

### Post by ristosu on 2008-09-01
I believe it is a hardware limitation: the monitor will not sync on anything but 60 kHz horizontal frequency. This means that if the resolution is set to 1024x768, the refresh must be 75 Hz, and with 640x480, it must be 117 Hz. With wrong horizontal frequency, the screen stays black.

The color depth limitations may be driver dependent.

I think I own a very similar machine than yours.

```
cat /proc/device-tree/model

```
gives:

```
PowerMac2,2

```
I think the driver is the correct one. It is called 'ati'. There are not so many possibilities.

I might try changing the color depth myself, and report it here.

Risto

---

### Post by stream303 on 2008-09-02
Be sure to see this about the G3 iMacs.  I'd make sure that your /etc/X11/xorg.conf follows these guidelines:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

You may have to add a separate "modules" section at the end.  I'd definitely run it at it's native resolution of 800x600, and perhaps with the values in the wiki, you'll be able to change down to 800x600 at 24 bits.

---


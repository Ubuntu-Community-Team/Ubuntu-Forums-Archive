---
title: "Nvidia Help."
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-07-05
Okay, I have a nvidia GFX card. But I don't know what drivers to install because last time i did it i had a HDD error and had to reinstall ubuntu. In the synaptic package manager it says i have, "nvidia glx" and "nvidia glx legacy" which one, I know i have to chang xorg.conf to "nv" to "nvidia". I just wanna make sure I download the right drivers. thanks.

---

### Post by Nekiruhs on 2007-07-05
If you just installed 6.06 again I would advise installing 7.04 instead. 7.04 has much better proprietary driver management through the Restricted Drivers Manager GUI tool. It also includes Codec Buddy for added codec support.

---

### Post by phizikal on 2007-07-05
Yeah that what I was thinking, but I have a while until my CD's arrive. =/

---

### Post by Nekiruhs on 2007-07-05
Do you have a friend who could burn one for you? You might be able to get it that way. Or you could have a forum member here from Missouri burn one and mail it to you.

---

### Post by avik on 2007-07-05
Here's a list of the cards that require the legacy driver: [http://ubuntuforums.org/showthread.php?t=233241]("http://ubuntuforums.org/showthread.php?t=233241").  If your card isn't on there, install the regular nvidia-glx driver.

And I believe you don't have to change the xorg.conf file as the installer will take care of that.  If 3D Acceleration still doesn't work, try using:

```
sudo nvidia-glx-config enable
```

and restarting the X Server (hit Control-Alt-Backspace).

---

### Post by phizikal on 2007-07-05
Ok, I forgot how to make the permissions on that xorg.conf file permissionable so I can save it.

---

### Post by Nekiruhs on 2007-07-05
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by phizikal on 2007-07-05
Ok, I have it working and all. But when right before the NVIDIA logo shows up, I get a few HDD errors for a few seconds and then I get on.

---

### Post by stchman on 2007-07-05
> **phizikal said:**
> Yeah that what I was thinking, but I have a while until my CD's arrive. =/

If you have high speed download the .iso.  If you are on dialup then it will take some time.

I see you are in St. Louis, I live in St. Louis as well.  I can make you a CD of 7.04 and get it to you.  The free CDs sometimes take months.  PM me later.

Feisty has great support for Nvidia cards.

---


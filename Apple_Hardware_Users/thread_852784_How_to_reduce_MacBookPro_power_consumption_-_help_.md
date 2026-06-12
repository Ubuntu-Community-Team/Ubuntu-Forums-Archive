---
title: "How to reduce MacBookPro power consumption - help needed"
date: 2008-07-07
forum: Apple Hardware Users
---

### Post by wilbur.harvey on 2008-07-07
I am running Hardy, a clean install, on a Core2Duo (gen 2 I think) Macbook Pro.

Power top says I am using about 30-32 watts. Following the power top recommendations will get me down a watt or two.

It runs quite hot, and the battery life is very short. Much shorter than when running MacOSX.

What should a typical power number be?

There seem to be very little information on reducing power consumption under Hardy for the Macbook Pro.

---

### Post by DonnieP on 2008-07-07
> **wilbur.harvey said:**
> There seem to be very little information on reducing power consumption under Hardy for the Macbook Pro.
If you don't mind the use of root, the following will give you the ability to throttle cpu frequency which could result in reducing power consumption.  Note that Hardy defaults CPU frequency throttling to 'ondemand'.  First do this:

```
sudo dpkg-reconfigure gnome-applets
```

Then add the CPU frequency scaling monitor applet to your Gnome Panel.  This will let you run the applet as root which will give you left click access to manually changing the CPU performance profile.  You can add an applet for each processor you have, selecting it in the preferences.

---

### Post by cyberdork33 on 2008-07-08
This thread has a lot of power-saving talk. It is not Hardy specific, but that really shouldn't change things much.

[http://ubuntuforums.org/showthread.php?t=590867](http://ubuntuforums.org/showthread.php?t=590867)

---

### Post by wilbur.harvey on 2008-07-11
I have done it before with no luck, I tried it again, both with the minimum cpu setting of 1.0GHZ and power save, I am stuck at about 33W.

---

### Post by wilbur.harvey on 2008-07-11
I went through his tips.
The gnome power manager stuff seems to be different in Hardy.
Anyway by killing everything except for the bluetooth, which is how I connect to the intenet, I got it down to 28W. A lot higher than he got his down to.
Any other ideas?

---

### Post by cyberdork33 on 2008-07-11
> **wilbur.harvey said:**
> I went through his tips.
The gnome power manager stuff seems to be different in Hardy.
Anyway by killing everything except for the bluetooth, which is how I connect to the intenet, I got it down to 28W. A lot higher than he got his down to.
Any other ideas?
I think he was using a MacBook as opposed to a MacBook Pro as well. That might be a big difference.

For the gnome power manager stuff, all I can say is just search around as that kind of thing shouldn't be all that specific to Macs. try and get the same settings changed with the new gnome utility.

Bluetooth and WiFi are power hogs. I don't know that 28W is all that bad considering. Maybe try turning of Bluetooth temporarily to see the effect. at least then you will know how much it is adding to the mix.

---


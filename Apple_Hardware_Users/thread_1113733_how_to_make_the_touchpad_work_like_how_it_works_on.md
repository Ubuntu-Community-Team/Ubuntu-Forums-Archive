---
title: "how to make the touchpad work like how it works on macbook?"
date: 2009-04-01
forum: Apple Hardware Users
---

### Post by genal on 2009-04-01
I just installed the ubuntu on my macbook white (5,2), how to make the touchpad works like that on OSX?
many thx!

---

### Post by inphektion on 2009-04-02
Jaunty? [https://help.ubuntu.com/community/MacBook5-1/Jaunty](https://help.ubuntu.com/community/MacBook5-1/Jaunty)
intrepid? [https://help.ubuntu.com/community/MacBook5-1/Intrepid](https://help.ubuntu.com/community/MacBook5-1/Intrepid)

---

### Post by cyberdork33 on 2009-04-02
> **genal said:**
> I just installed the ubuntu on my macbook white (5,2), how to make the touchpad works like that on OSX?
many thx!
and you will have to be more specific than "works like on OSX". What functionality are you looking for specifically.

---

### Post by genal on 2009-04-02
tapping two finger on the touchpad will pop up the menu

---

### Post by genal on 2009-04-02
i am using hardy...Orz...

---

### Post by cyberdork33 on 2009-04-03
> **genal said:**
> i am using hardy...Orz...
well, hardy is pretty old especially considering you have one of the very newest hardware revisions. I would get intrepid at least (and honestly, I would get Jaunty... it comes out very soon).

then you can follow the direction in the wiki page posted to setup your touchpad.

---

### Post by skylen on 2009-04-03
I just got the two-finger (and three-finger for middle button) tap-to-click working on my MacBook Pro 5,1.  I still have a couple of serious issues, but maybe you'll have better luck and the sensitivity will work OK for you.

I got the trackpad on my MacBook Pro 5,1 *mostly* working by doing:
(On a fresh install of Jaunty Beta)

1. Install all the mactel PPA packages.
2. Blacklist usbhid
3. Put bcm5974, usbhid in modprobe's "modules" file to force bcm5974 to load first.
4. Put the file posted by P. Dunbar in bug #337935 on 2009-03-31 in /etc/hal/fdi/policy

See bug #337935 at [https://bugs.launchpad.net/mactel-support/+bug/337935]("https://bugs.launchpad.net/mactel-support/+bug/337935") for details on the blacklisting/force-usbhid-order trick.  It's not great but it seems to get around the problem of the trackpad device being claimed as a generic pointing device.

I could then tweak the .fdi file in a minor way and had the following features:

- tap-to-click
- one/two/three-finger tap clicks for left/right/middle button
- two-finger scrolling (both vertical and horizontal)

There are still some big problems that make the trackpad completely unusable for me unfortunately. The main problems are:

1. Sensitivity is *WAY* too low.
2. Can't click and hold with thumb while dragging with another finger.

Maybe this won't help you since I'm using Jaunty beta and you are using something else, it sounds like, but I'm posting my experience just in case it helps.

Regards,
Colin

---


---
title: "Wireless goes from 0-99% and back"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-03-26
Hello all,

The past couple of months I have been experiencing a problem with my wireless.

I use 6.06, nm-applet, and gnome-network-manager to connect wirelessly

The issue is after about 30 minutes of connectivity my wireless connection spontaneously terminates, it then automatically reconnects after about ten seconds.

After it reconnects it begins to cycle between 0%-99% about every 30 seconds and does not stop.

my /etc/network/interfaces

auto lo
iface lo inet loopback

and everything else is commented out

The laptop is a HP dv6000t with the intel 3945 a/b/g card, it's only about 7 months old (the laptop that is)

any ideas???

---

### Post by eljalill on 2007-03-26
Mine used to do that too, with NM, when I had questionable connectivity.
WiCD never does it, but then the try icon sometimes just disappears...
I like WiCD better though.

---

### Post by charles.g.moore on 2007-03-26
> **eljalill said:**
> Mine used to do that too, with NM, when I had questionable connectivity.
WiCD never does it, but then the try icon sometimes just disappears...
I like WiCD better though.

Is WiCD in the repo's?

Does it pretty much do the same as NM?  Am I able to pull down a drop menu with all of the available wireless networks?

Does it work with WPA/WEP, mainly WPA_supplicant?

I did some research and found that this seems to be happening more and more:
[https://launchpad.net/ubuntu/+source/network-manager/+bug/64173](https://launchpad.net/ubuntu/+source/network-manager/+bug/64173)

---

### Post by eljalill on 2007-03-26
WiCD is not in the repos, you have to download it from here:
[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/) .

It doesn't do drop down, but opens a new window with the available networks if you go rightclick>connect , but that's all the same for me :)

And yes, it does WPA (supplicant) an apparently also hidden networks and such, but I haven't tried the latter out.

More is of course on the website.

---


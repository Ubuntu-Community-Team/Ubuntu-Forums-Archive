---
title: "Just Installed Ubuntu"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by thepaul on 2006-10-26
Hi all

I just installed Unbuntu on my desktop as a dual boot with Windows XP.

Just a few requests for help, either instructions or places to find the help:

1) playing MP3's.  What's the best player with ubuntu, and I'm using 6.06.  I tried to play a few mp3 files, but not happening.

2) internet...how do I connect??  I have an ethernet connection into the computer, which works fine in windows but not in ubuntu.

any and all help will be appreciated.

---

### Post by voodoonirvana on 2006-10-26
Install automatix:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Everything you need for multimedia.

As for the connection I dont know.

---

### Post by Aberrix on 2006-10-26
Yes, use automatix to install the restricted codecs so you can play mp3's and such.

As far as playing music, I've found Amarock to be the best substitude if your akin to iTunes.

```
sudo apt-get install amarok
```

---

### Post by Jagot on 2006-10-26
Or if you don't want to let Automatix do it for you:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Cartwheels4amile on 2006-10-26
Uh, guys, he can't get on the net to download any of this stuff you're suggesting.

---

### Post by Jagot on 2006-10-26
Ah, yes, well spotted.  thepaul, go to System, Admin, Networking.  Is there a wired connection there?

---

### Post by tchoklat on 2006-10-26
> **Jagot said:**
> Ah, yes, well spotted.  thepaul, go to System, Admin, Networking.  Is there a wired connection there?
yry the sticky post on codecs at the top of the beginners forum page - worked for me!

tchoklat

---

### Post by thepaul on 2006-10-26
> **Jagot said:**
> Ah, yes, well spotted.  thepaul, go to System, Admin, Networking.  Is there a wired connection there?

when I went to network....there is ethernet and modem. The modem was highlighted and so I clicked on the ethernet, but still nothing.

---

### Post by Rackerz on 2006-10-26
Did you tick the box next to the wired connection? It might not have been enabled. Also check its properties, do you have a router, static IP or dynamic IP?

---

### Post by Bartender on 2006-10-26
If you've already gone into "Networking" under System>Administration and enabled your ethernet device, let me ask you this - does Synaptic go online?  If it does but Firefox doesn't, type 'disable IPV6' into Search and follow the directions. If Synaptic doesn't connect, or connects sporadically, there are also directions for disabling IPV6 across the whole operating system.
Here were the exact symptoms I came across - on a friend's PC, Firefox would connect to the Quick Links that went directly to the Ubuntu website, but not to Google, Yahoo, or anything else.  Turning off IPV6 within Firefox fixed the problem.  We did not have to turn off IPV6 systemwide.
Also, we saw some lights blinking on the modem, but they were very sporadic.  If you see absolutely no sign of modem activity then IPV6 may not be your prob.
Also, an ethernet plug generally works better than USB.

---

### Post by thepaul on 2006-10-27
I went back to ubuntu and checked the network... the comment in the box of the ethernet is eth0 is active.

---


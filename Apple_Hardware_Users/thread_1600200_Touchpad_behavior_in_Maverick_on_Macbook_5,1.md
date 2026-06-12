---
title: "Touchpad behavior in Maverick on Macbook 5,1"
date: 2010-10-18
forum: Apple Hardware Users
---

### Post by michael.allen on 2010-10-18
Hey guys,

So I've been forced to use ubuntu for various things at work now, and I'm trying to get settled in. However, one serious problem I've had is getting my touchpad to be anywhere usable.

Since there isn't any sort of Maverick-related info page, I've been checking out the stuff for MacBookPros. In fact I'm pretty sure they all have the same  trackpad anyway. 

This is what I was looking at:
[https://help.ubuntu.com/community/MacBookPro5-3/Maverick#Touchpad](https://help.ubuntu.com/community/MacBookPro5-3/Maverick#Touchpad)

They mention that "click and drag" works. Does that mean click and drag with one finger, or click and drag one finger clicking and the other "dragging"

My main problems are that I currently am accidentally activating the double-tap automatic drag accidentally. Secondly is anyone able to do the two-finger drag?

I've managed to get two-finger scrolling going though.

It's really unusable right now though. I really need that two-finger click-drag though.

I also managed to change some of the settings via synclient, but never really got it working to where it wasn't constantly getting in the way.

---

### Post by Niels den Otter on 2010-10-19
I'm not sure what parameters you would want to change, but the synaptics driver gives lot of options. What I change myself at login is following:

==
more ~/otter@sambal:~$ more ~/bin/startup.sh 
#!/bin/sh

xinput set-prop "bcm5974"  "Synaptics Palm Detection" 1
xinput set-prop "bcm5974"  "Synaptics Locked Drags"   1
==

The following URL provides a long list of possible parameters (not sure if it is the latest):

[http://www.x.org/archive/current/doc/man/man4/synaptics.4.html](http://www.x.org/archive/current/doc/man/man4/synaptics.4.html)


Good luck,

Niels

---

### Post by michael.allen on 2010-10-23
Thanks for the help Niels, I actually just found what I was looking for here, for future reference:

[http://ubuntuforums.org/showthread.php?t=1334696&page=26](http://ubuntuforums.org/showthread.php?t=1334696&page=26)

---

### Post by Jhime on 2010-10-23
Hi, I just installed Ubuntu today would like to know what the solution is (step by step if possible). I'm not really sure if I'm running the synaptics driver or not... nothing is mentioned in xorg.conf.

Can anyone help me?
Thanks.

Edit: Ah, so there already was a step by step solution [here]("http://ubuntuforums.org/showpost.php?p=9193610&postcount=130"), guess I didn't look close enough.

---


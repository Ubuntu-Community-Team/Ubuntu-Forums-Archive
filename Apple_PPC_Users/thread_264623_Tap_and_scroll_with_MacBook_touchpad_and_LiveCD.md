---
title: "Tap and scroll with MacBook touchpad and LiveCD"
date: 2006-09-24
forum: Apple PPC Users
---

### Post by rscow on 2006-09-24
I may be imagining things, but I have noticed this:

When I booted from the LiveCD to start installing Dapper on my MacBook, I was able to use the trackpad to tap and scroll whilst entering the initial information in the steps leading up to the install.

Now that I'm running it natively, I can't.  This is a desired option.  I know that in the Gentoo world they've had some success, but apparently by making the OS think it's a pure Synaptics touchpad.

Where would I look to compare settings between the LiveCD and the working OS I am using?  /etc/X11/xorg.conf ?
Could the differences related to the touchpad input device be carried over and work?

Just a thought.

Best,

Roger

---

### Post by nhemingway on 2006-10-06
You saw this on the normal Dapper live-CD!?!? I've installed Dapper, Knot2, and Knot3 from live-CD, and have never seen my touchpad work properly. According to the Gentoo wiki, it appears appletouch has to be loaded before usbhid, but I've had no luck with this myself.

---


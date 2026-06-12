---
title: "Apple wireless keyboard doesn't work w/ Ubuntu, yet DOES work with Damn Small Linux!"
date: 2008-04-09
forum: Apple Intel Users
---

### Post by Tadpole on 2008-04-09
This is quite a paradox. How does a miniscule 50MB linux distro out-do Ubuntu in hardware support when it comes to bluetooth mac keyboards?

I bought the new Apple wireless keyboard in hopes that I could use it with Ubuntu. Could anyone offer tips on how to get Ubuntu to detect it? Thank you.

---

### Post by ronocdh on 2008-04-10
Have you tried searching in Synaptic for bluetooth packages you could configure? I know the [MBP wiki]("https://help.ubuntu.com/community/MacBookPro") has a section on getting the Apple bluetooth keyboard to work.

---

### Post by cyberdork33 on 2008-04-10
bluetooth is a mess in ubuntu...

---

### Post by warp99 on 2008-04-10
Per the Ubuntu help guide:

[https://help.ubuntu.com/community/BluetoothInputDevices?highlight=%28bluetooth%29%7C%28keyboard%29](https://help.ubuntu.com/community/BluetoothInputDevices?highlight=%28bluetooth%29%7C%28keyboard%29)

---

### Post by cyberdork33 on 2008-04-10
> **warp99 said:**
> Per the Ubuntu help guide:

[https://help.ubuntu.com/community/BluetoothInputDevices?highlight=%28bluetooth%29%7C%28keyboard%29](https://help.ubuntu.com/community/BluetoothInputDevices?highlight=%28bluetooth%29%7C%28keyboard%29)
That would be nice if that worked. It does for some though.

---

### Post by incubus on 2008-04-11
I remember it was a pain to get it to work on Feisty and Gutsy, but now on Hardy it worked without much effort.  I just had to put it on pairing mode and get the bluetooth applet to find it.  Once paired, I never had to do that again.

On Feisty and Gutsy I had to use hidd and pretty much edit the files on /var/lib/bluetooth to force the keyboard key to appear in the right places.  I also had to edit a file on /etc/bluetooth, I think, to get it to connect on reboot.  So, in other words, it seems to be working well on Hardy.

One problem I do have, though, is that when the keyboard sleeps, it doesn't resume the connection.  I have to put it on pairing mode again, then it reconnects, but this is honestly getting annoying.

---

### Post by cyberdork33 on 2008-04-11
yep that is one of the current bug reports, and it looks like it might not get changed since the release date is so near now.

---

### Post by russo.mic on 2008-04-11
> **cyberdork33 said:**
> bluetooth is a mess in ubuntu...

I have to disagree on some level.  I turn on my phone, it connects.  I turn on my mouse, it connects.  I turn on my keyboard, it connects.  It took a bit of setup, maybe 10 min. or so.  

It's def. better with KDE, as i've switched recently.  Not any much nano of xorg.conf.  And it's def. better with Gusty than with Feisty.

Russo

---

### Post by cyberdork33 on 2008-04-12
I am talking about hardy. They completely changed the bluetooth stack.

---

### Post by russo.mic on 2008-04-12
ahhh,  I haven't found the time to start screwing with it yet.  

That's a shame.  Maybe they'll pull it together in time for the release!  Have faith!

---

### Post by groupmsl on 2008-06-10
> **cyberdork33 said:**
> bluetooth is a mess in ubuntu...

Agreed!

---


---
title: "Not your average wireless driver question."
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by cnico88 on 2007-11-28
I know wireless drivers can be a pain to install in Linux, however I don't think I am in that situation. I am using an Edimax EW-7128g which uses a Ralink RT61 Turbo chipset. This thing was made for windows and Linux and it worked with Ubuntu 7.04 Live CD out of the box with no tinkering. However when I installed Mint on the VMware virtual box, there is no option available for a wireless driver. I really want to get the internet working so I can get wine and so on. My first question is why doesn't internet work because I have Vista booted and the internet works there, I assume vm is just another open window unless it has to go through some loops. Anyway, if I can get any light on how to configure this thing, I know for sure it works but I don't know where to start. I have to CD with the drivers and again I have no idea what to do. Thanks.

PS: Oh, and if anyone asks why I don't post in the Mint forums: I did and it's been weeks without a response ([http://www.linuxmint.com/forum/viewtopic.php?f=90&t=6999](http://www.linuxmint.com/forum/viewtopic.php?f=90&t=6999))

[IMG]http://i37.photobucket.com/albums/e67/cnico88/screenshot.jpg[/IMG]

---

### Post by Dr Small on 2007-11-28
Cool. What window manager is that in the screenshot ? :D It looks like mine ;)
Oh, back to the question. Have you gone into your Networking Options and try setting it up from there ?

---

### Post by Dark_X on 2007-11-28
If its in a virtual machine it doesn't need wireless drivers.  It uses the network you have as if it was wired.  I haven't used vmware so I don't know how to configure it.
> **Dr Small said:**
> Cool. What window manager is that in the screenshot ?

I think that would be Vista.... XD

---

### Post by cnico88 on 2007-11-28
yeah, I am running Vista. The network works on my Vista machine but once I go into VmWare, it's dead, and no matter if I try to use wirelless or wired, this is what I get:
[IMG]http://i37.photobucket.com/albums/e67/cnico88/network.jpg[/IMG]

---

### Post by Dark_X on 2007-11-28
Look in the settings for network or internet in vmware.  I think you have to set vmware up to use your wireless card instead of the wired one you probably have.

---

### Post by Dr Small on 2007-11-28
> **Dark_X said:**
> If its in a virtual machine it doesn't need wireless drivers.  It uses the network you have as if it was wired.  I haven't used vmware so I don't know how to configure it.


I think that would be Vista.... XD
Ooohhh. Well, that looks like my IceWM :)

---

### Post by Dark_X on 2007-11-28
I just looked at that pic again.  Can you change Ethernet to wireless (or anything else)?

---

### Post by antharr on 2007-11-29
Could it be a problem with bridging or NAT options when you set up your VM?

---

### Post by cnico88 on 2007-11-30
Network is enabled, I don't see any other options where I should turn it on.

[IMG]http://i37.photobucket.com/albums/e67/cnico88/start.jpg[/IMG]

---

### Post by cnico88 on 2007-12-02
Do I need to install any additional stuff either for Mint or for VMWARE?

---

### Post by cnico88 on 2007-12-02
^bump^

---


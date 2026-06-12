---
title: "Intel 82865G graphics chip + wide res. support"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by kerneld2000 on 2007-05-29
An absolute newbie question guys,

I've just completed installing 7.04 on a Dell Optiplex (P4@2,4) with integrated graphics via the Intel 82865G chipset, and everything is working fine. Only problem so far is the screen resolution. The dell is hooked to an LG 20,1" wide monitor and the current 1280x1024 resolution becomes tiresome after a while, which means that I need to install intel linux drivers and hope that they support wide resolutions of either 1440x900 or (ideally) 1680x1050.

Since this is my first attempt with ubuntu (and linux) I definetly need help with installing the intel driver since I can't make sense of what is required (e.g. kernel recompilation?) and the instructions I've found at [_intellinuxgraphics.org_]("http://intellinuxgraphics.org/install.html") look like greek to me (and I'm greek!!!).

So any help or suggestions will be highly appreciated.

---

### Post by viciouslime on 2007-05-29
I think the driver that ships with ubuntu will do what you want it to just fine. It's just a case of configuration. You probably want to edit xorg.conf and add the resolution you desire to it. If that means nothing to you, post back and I'll try and guide you through it...

---

### Post by justleen on 2007-05-29
i had to install the package "915resolution"  in order to get wide screen on my laptop (i have a 815 chipset.. )
it will create a file in /etc/default/915resolution.
edit this (fill in your wanted resolution), and then edit xorg.conf (create a backup!). Make sure the same resolution is under the "Screen"   section..

---

### Post by viciouslime on 2007-05-29
> **justleen said:**
> i had to install the package "915resolution"  in order to get wide screen on my laptop (i have a 815 chipset.. )
it will create a file in /etc/default/915resolution.
edit this (fill in your wanted resolution), and then edit xorg.conf (create a backup!). Make sure the same resolution is under the "Screen"   section..

Oh yeh, I'd forgotten about that. I have to do the same for my macbook. I would try this first, at worst it will say there is no supported chipset found.

---

### Post by kerneld2000 on 2007-05-29
> **justleen said:**
> i had to install the package "915resolution"  in order to get wide screen on my laptop (i have a 815 chipset.. )
it will create a file in /etc/default/915resolution.
edit this (fill in your wanted resolution), and then edit xorg.conf (create a backup!). Make sure the same resolution is under the "Screen"   section..

Where exactly can I get the necessary package? (I assume somthing like 865resolution)

---

### Post by daverich on 2007-05-29
what worked for me was installing the latest intel video driver.

I did install the 915 res fix thing beforehand though but until i installed the driver with a 9 prefix - not the 8 which some forum posts were recommending - it wouldn't work.

once i installed that driver and booted the screen was automatically at 1400x900.

Kind regards

Dave Rich

---

### Post by kerneld2000 on 2007-06-03
I found installed 915resolution from synaptic.

I have also downloaded the intel driver file i915Graphics.tar.gz

How do I install this? I can't make synaptic see any of the files inside this package.

---

### Post by rusty4r on 2007-06-03
try looking at this it may help you
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---


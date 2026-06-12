---
title: "minor things bugging me"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by cvitullo on 2007-08-13
I love ubuntu, except for a few things that have been bugging me. first and most severe, i can't connect to wifi. i can see the networks, but can't connect.
second, when i activate the desktop effect "workspaces on a cube", it reduces the number of workspaces to 1. then, when i adjust it to have more workspaces, the effect doesn't show up. it  just does the normal transition.
third, how do i disable tap to click? i absolutely hate that, especially since i play a lot of games.

---

### Post by Ek0nomik on 2007-08-13
> **cvitullo said:**
> I love ubuntu, except for a few things that have been bugging me. first and most severe, i can't connect to wifi. i can see the networks, but can't connect.
second, when i activate the desktop effect "workspaces on a cube", it reduces the number of workspaces to 1. then, when i adjust it to have more workspaces, the effect doesn't show up. it  just does the normal transition.
third, how do i disable tap to click? i absolutely hate that, especially since i play a lot of games.

Regarding your wireless, what type of wireless card do you have?  I have a Dell 1500 and I am using ndiswrapper with the Windows drivers to make use of my wireless.  I know that in order to get my wireless to work I have to try to connect to a different network, and *then* try to connect to the one I want to connect to.  For some reason I can't connect to a network by the default loading of it.  Did you follow a tutorial on getting your wireless to work?  If you don't know what kind of wireless card you have, type the following and paste the relevant output:

```
lspci
```

Regarding the tap to click, I don't know if this will solve your problem but you can look at these:

[https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/92128](https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/92128)
[http://ubuntuforums.org/archive/index.php/t-498968.html](http://ubuntuforums.org/archive/index.php/t-498968.html)
[http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/)

---

### Post by Hobo Joe on 2007-08-13
Are you using Beryl for the Desktop effects? There is a weird bit of confusion about this part, and I'll help to the best of my memory. Instead of changing the option that says something like 'number of virtual desktops', change the option that says 'virtual desktop size', or something to that effect. I'm pretty sure thats it.

However, if you are using Beryl, I'd recommend switching to Compiz Fusion.

---

### Post by cvitullo on 2007-08-13
I have a intel 3915abg PROset/wireless card, and i can't even find a way to connect to any wireless network. i can only see them.

---

### Post by cvitullo on 2007-08-13
i'm using the default, preinstalled desktop effects, so..... yeah.

---

### Post by Ek0nomik on 2007-08-13
> **cvitullo said:**
> I have a intel 3915abg PROset/wireless card, and i can't even find a way to connect to any wireless network. i can only see them.

39**1**5 or 39**4**5?

Sorry, I just find it weird that I can't find a single thing for 3915.

---

### Post by Hobo Joe on 2007-08-13
> **cvitullo said:**
> i'm using the default, preinstalled desktop effects, so..... yeah.
Oh, in that case, you really need to install Compiz Fusion! :D

---

### Post by cvitullo on 2007-08-13
yeah, it's 45, sorry.

---

### Post by cvitullo on 2007-08-13
sorry, to be a n00b, but how do you install things?? i've tried, thoroughly read the direction on all sites i've downloaded from, and it's just not working...

---

### Post by Ek0nomik on 2007-08-13
> **cvitullo said:**
> yeah, it's 45, sorry.

Well, you can look at this thread which is pretty long and has a lot of responses:

[http://ubuntuforums.org/showthread.php?t=140085](http://ubuntuforums.org/showthread.php?t=140085)

What version of Ubuntu are you using?

---

### Post by cvitullo on 2007-08-13
fiesty fawn

---

### Post by Ek0nomik on 2007-08-13
> **cvitullo said:**
> sorry, to be a n00b, but how do you install things?? i've tried, thoroughly read the direction on all sites i've downloaded from, and it's just not working...

I just want to point out that installing Compiz/Beryl from hand isn't exactly very pretty.  It can get complicated, especially if you are new to Ubuntu.  Compiz is still beta software, so it is unstable and may give you some headaches.  That said, installing Compiz won't mess up your system.  You will need to type a command to run Compiz, so you should be safe in not messing anything up all that badly.  :)  If Compiz crashes or freezes, a simple reboot should get you back to normal.

[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

---


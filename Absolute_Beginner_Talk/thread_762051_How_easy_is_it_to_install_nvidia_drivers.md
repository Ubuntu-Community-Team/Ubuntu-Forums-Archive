---
title: "How easy is it to install nvidia drivers?"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by MrTickle on 2008-04-21
I need to install the nvidia drivers on my fresh install of ubuntu 7.10

Could someone please explain the necessary steps for installation as tho they're teaching a complete novice.

Thanks for your time & for reading.

Mike

---

### Post by jken146 on 2008-04-21
Go to System --> Administration --> Restricted Drivers Manager.  Tick the box next to the nvidia driver.

---

### Post by Crafty Kisses on 2008-04-21
> **jken146 said:**
> Go to System --> Administration --> Restricted Drivers Manager.  Tick the box next to the nvidia driver.

That's the easiest way, there's also Envy, that might work too: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Periswell on 2008-04-21
wait till hardy herron comes out as they have a program (cant remeber what it is called) that can help you with your problem. only 3 more days to wait.

---

### Post by jken146 on 2008-04-21
> **Periswell said:**
> wait till hardy herron comes out as they have **a program** (cant remeber what it is called) that can help you with your problem. only 3 more days to wait.

What's that?

---

### Post by Crafty Kisses on 2008-04-21
> **jken146 said:**
> What's that?

He's probably thinking of Envy.

---

### Post by jken146 on 2008-04-21
> **Codename said:**
> He's probably thinking of Envy.

Ah yes, I didn't realise envyng was in Hardy.

---

### Post by Crafty Kisses on 2008-04-21
> **jken146 said:**
> Ah yes, I didn't realise envyng was in Hardy.

It might be, but that's what he's probably thinking of.

---

### Post by PeterJS on 2008-04-21
I think he's referring to Jockey, which is a re-write of the current restricted drivers manager to be more flexible and easier to add other hardware too.

---

### Post by perlluver on 2008-04-21
envyng is in the hardy repos, I found it under synaptic.

---

### Post by Ub1476 on 2008-04-21
It isn't. The name in Administration is renamed to "Hardware Drivers" instead of "Restricted Driver.." Can't recall what's the real name of it is, but it looks the same at least:)

---

### Post by PeterJS on 2008-04-21
> **perlluver said:**
> envyng is in the hardy repos, I found it under synaptic.

Wow, it is in there. Does this mean that envyNG is better behaved and won't break your system at the drop of a hat like it's predecessor?

---

### Post by perlluver on 2008-04-21
> **PeterJS said:**
> Wow, it is in there. Does this mean that envyNG is better behaved and won't break your system at the drop of a hat like it's predecessor?

That is how I installed my Nvidia video card, and It worked pretty good, for a Nvidia Geforce FX 5400, I don't know about the rest.

---

### Post by aktiwers on 2008-04-21
I made a small guide once too. It should work perfectly if you want to do it manually. Just remember to change the driver file version name to the one you downloaded:
[http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735](http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735)

---

### Post by PeterJS on 2008-04-21
> **perlluver said:**
> That is how I installed my Nvidia video card, and It worked pretty good, for a Nvidia Geforce FX 5400, I don't know about the rest.

Have you gone through any kernel upgrades since installing the driver with envy? if so how did it do?

---

### Post by MrTickle on 2008-04-26
Thanks guys :KS  I've had real bad man flu since starting this thread and all i've done is sleep & work :(

Thanks again... *goes to install latest drivers*

---


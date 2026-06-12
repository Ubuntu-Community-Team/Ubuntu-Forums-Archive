---
title: "[SOLVED] MacBook Pro freezes when using fglrx, 8.04"
date: 2008-06-13
forum: Apple Hardware Users
---

### Post by Dacobi on 2008-06-13
Hello

I just installed Ubuntu 8.04 on my MacBook Pro (original version)
with an ATI x1600.

When using the open source drivers things are good, but
when I enable fglrx (tried both the one in apt and from ati's site)
my system freezes about 30 sec after login in. (have to cold boot)

I can't seem to find others on the net with the same problem, 
so my question is if this could be a hardware problem?

/Dacobi

---

### Post by cyberdork33 on 2008-06-13
It "could' be a hardware problem but doubt that it is.

Uninstall and try using envy.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Dacobi on 2008-06-13
Thanks

Envy works perfectly with more eye candy than I can shake a stick at :)

Only problem is that I manually have to load the fglrx.ko module and then restart gdm. don't know if this is because there's one both in 
/lib/modules/2.6.24-18-generic/updates/dkms/ (which is the one i load)
and
/lib/modules/2.6.24-18-generic/volatile

How do I make the module load automatically?

/Dacobi

---

### Post by cyberdork33 on 2008-06-13
do you have fglrx as the driver in your xorg.conf?

---

### Post by Dacobi on 2008-06-14
Hmm...

I reinstalled Ubuntu and Envy all together and now the module loads but I get random freezes and one time a cold boot...?
This always seems to happen in relation to the compiz effects.

I still think it maybe hardware since I also have some artifacts in OS X all though no crashes.

/Dacobi

---

### Post by cyberdork33 on 2008-06-14
> **Dacobi said:**
> Hmm...

I reinstalled Ubuntu and Envy all together and now the module loads but I get random freezes and one time a cold boot...?
This always seems to happen in relation to the compiz effects.

I still think it maybe hardware since I also have some artifacts in OS X all though no crashes.

/Dacobi
definitely could be hardware if you have artifacts in OSX as well. Have you tried things like clearing nvram? resetting the SMC?

---

### Post by Dacobi on 2008-06-15
I've tried resetting the SMC, but how do I clear the nvram?

One thing I'm thinking is heat, since the system crashes seems do be most frequent when using a lot of 3d effects. If I just leaves the system alone I will go on for hours without crashing.

How do I control the fan speed in 8.04?

/Dacobi

---

### Post by cyberdork33 on 2008-06-15
> **Dacobi said:**
> I've tried resetting the SMC, but how do I clear the nvram?

One thing I'm thinking is heat, since the system crashes seems do be most frequent when using a lot of 3d effects. If I just leaves the system alone I will go on for hours without crashing.

How do I control the fan speed in 8.04?

/Dacobi
[https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl](https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl)

---

### Post by Dacobi on 2008-06-16
Most definitely a heat problem, just installed the tempmon scripts and applesmc and have had my system running for 5 hours with extensive opengl usage and no crashes :)

My fans simply weren't running before...

Only problem now is with Quake4 where the mouse stops responding when i press and hold a key on the keyboard...?

/Dacobi

---

### Post by cyberdork33 on 2008-06-16
> **Dacobi said:**
> Only problem now is with Quake4 where the mouse stops responding when i press and hold a key on the keyboard...?

You should start new threads when not related to the topic.
Mouseemu:
[http://ubuntuforums.org/showpost.php?p=5160609&postcount=2](http://ubuntuforums.org/showpost.php?p=5160609&postcount=2)

---


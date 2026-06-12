---
title: "graphics card  problem"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by petite on 2007-10-27
I have a nvidia graphics card, and I suspect that the hardware may be faulty. Using the nvidia drivers on unbuntu, the desktop refuses to start. We have a dual boot XP install, which also goes pear shaped when we try to use grapics accelleration.

Anyone have any ideas on how to proceed? It would be nice know for sure before we go buying a new card.

---

### Post by Qwerty_ on 2007-10-27
I take that you installed the restricted drivers?

System>Administration>Restricted Drivers Manager.

I would then proceed and reconfigure you xserver.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by NickFortune on 2007-10-27
(petite's technical advisor chipping in)

I got as far as installing the restricted drivers; Only I was under the impression that the configuration script ran automatically as part of the restricted drivers installation process. Certainly something altered xorg.conf, because the desktop was broken after the install, and the only way we could get it working was to copy the xorg.conf from the install cd.

Does dpkg-reconfigure perform a more rigorous configuration than we get from synaptic?

---


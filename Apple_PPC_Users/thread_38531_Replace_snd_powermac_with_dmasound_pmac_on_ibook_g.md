---
title: "Replace snd_powermac with dmasound_pmac on ibook g4?"
date: 2005-05-31
forum: Apple PPC Users
---

### Post by craks on 2005-05-31
snd_powermac plays not well on my ibook g4 1.2G, always include noice, so i change the module snd_powermac to dmasound_pmac, that works fine.

---

### Post by ripounet on 2005-06-02
[QUOTE=craks]snd_powermac plays not well on my ibook g4 1.2G, always include noice, so i change the module snd_powermac to dmasound_pmac, that works fine.[/QUOTE]

Yeah, works for me too! Thanks for the trick!
I manually edited as root the file /etc/modules   (don't know if other ways exist).

iBook G4 933 white

---

### Post by craks on 2005-06-02
[QUOTE=ripounet]Yeah, works for me too! Thanks for the trick!
I manually edited as root the file /etc/modules   (don't know if other ways exist).

iBook G4 933 white[/QUOTE]

this file is also needed to be changed:
/etc/modprobe.d/alsa-base

find snd-powrmac and replace it

---


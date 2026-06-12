---
title: "What is the synaptic?"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by amazingjxq on 2008-03-02
I'm confused by the synaptic system. What's the difference between ubuntu software and third-party software? How does ubuntu know what we should update? from the repository?

---

### Post by Oldsoldier2003 on 2008-03-02
> **amazingjxq said:**
> I'm confused by the synaptic system. What's the difference between ubuntu software and third-party software? How does ubuntu know what we should update? from the repository?
Ubuntu software is software that is maintained by the community. third party software is software developed and maintained by other sources, The repositories maintain a listing of the most current files and when Ubuntu checks that list against what is installed on your system it returns a list of sofware that has newer versions available

---

### Post by JoshuaRL on 2008-03-02
Ubuntu software is software developed and/or maintained by Canonical or the community.  Third-party software is from outside developers.

Ubuntu looks everwhere listed in /etc/apt/sources.list and looks for newer versions of the programs you have.  That's part of the automagic of APT.  Those are the repositories.

---

### Post by steveneddy on 2008-03-02
Synaptic mainly has the "Ubuntu approved" software that is known to run well on your distro version.

It will also show the software available from additional repos that you may have added manually.

---

### Post by Oldsoldier2003 on 2008-03-02
> **JoshuaRL said:**
> Ubuntu software is software developed and/or maintained by Canonical or the community.  Third-party software is from outside developers.

Ubuntu looks everwhere listed in /etc/apt/sources.list and looks for newer versions of the programs you have.  That's part of the automagic of APT.  Those are the repositories.
 I did neglect to mention Canonical when I explained the difference im my post above, I guess my last browse through Synaptic kind made the community maintained sofware jump to the front of my brain lol.

---

### Post by JoshuaRL on 2008-03-02
> **Oldsoldier2003 said:**
> I did neglect to mention Canonical when I explained the difference im my post above, I guess my last browse through Synaptic kind made the community maintained sofware jump to the front of my brain lol.

Thats okay, I forgot to put in the community at first.  When I saw your version, I jumped back in and edited my post!  :p

---


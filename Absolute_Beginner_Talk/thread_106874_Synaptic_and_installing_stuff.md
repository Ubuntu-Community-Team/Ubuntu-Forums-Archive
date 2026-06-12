---
title: "Synaptic and installing stuff"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by Connollyir on 2005-12-21
I am a new user and I want to know which way of installing programs is better - using Synaptic or using the sudo apt-get command in terminal? My original distro was Gentoo Linux where all installation (and pretty much everything else) happened through the terminal and I want to know which way is better, safer, or more politically correct as it were(I switched because I went through about 2 weeks of agony trying to install a RAID 0 array only to have a disk fail 4 days after I finished).

---

### Post by Sutekh on 2005-12-21
Synaptic is just a front-end for apt-get.  So it's completely up to your preference.  

I use both at different times; Synaptic is easy to browse when I don't really know what I want, and apt-get is easy to just copy and paste commands to . If you are following howto's, they usually list apt-get commands

---

### Post by matthewv on 2005-12-21
Both synaptic and apt-get do the same thing. Which one you want to use is up to you. On these forums you'll often be told to use apt-get, probably because its easier to tell someone a command than trying to direct them through a gui. Basically, the Add Applications (the easiest install method, Applications --> Add Applications) is a front-end for synaptic, which is a front-end for (i think) apt-get, which is a front-end for dpkg and some other thing...

---

### Post by Connollyir on 2005-12-21
Yeah thats what I thought, but since Ubuntu has disabled the su login for security reasons (I'm pretty sure I read that somwhere...) I didn't know if there was some built in security factor behind it.

Thanks


-Ian

---

### Post by Sutekh on 2005-12-21
Yeah that's correct, although the root account can be enabled.

Synaptic and apt-get both use the user's *sudo* password.

---


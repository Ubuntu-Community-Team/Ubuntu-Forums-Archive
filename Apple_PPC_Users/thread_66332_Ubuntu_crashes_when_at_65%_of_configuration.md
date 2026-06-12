---
title: "Ubuntu crashes when at 65% of configuration"
date: 2005-09-16
forum: Apple PPC Users
---

### Post by Elijahg on 2005-09-16
Hi,

I have installed Ubuntu on an iMac G3 (Rev D, overclocked from 333 to 400mhz :D ). The install completes OK, but after restarting it gets to 65% of the configuration and hangs.  When I reset the iMac, it says "Some modules were not installed" and drops me to the command line login. Anyone have any ideas?

The iMac has 160(!) mb RAM.

I've installed Mac OS X on it and it works fine, it never hangs or crashes.

I haven't downloaded & burnt a new CD, which I'll try if no one can help.

Thanks!

Elijah

---

### Post by pvz on 2005-09-17
Try 'sudo base-config' to continue your configuration. On what point does it hang, is it during package installation? In that case try 'sudo apt-get -f install'.

---

### Post by Elijahg on 2005-09-17
Thanks for the reply :)

It hangs after the iMac restarts and ejects the CD, during the "extra" package installation, the title of the page is "Ubuntu Configuration". 

I'll try "sudo apt-get -f install" later today, and see if that works.

Thanks! :)

---

### Post by king_arthur on 2005-09-17
[QUOTE=Elijahg]

I've installed Mac OS X on it and it works fine, it never hangs or crashes.


Elijah[/QUOTE]

I know quite a few people may disagree but this is the truth.
It even runs faster, no matter what anybody says, as OSX takes full benefit of the Quartz engine (i.e. full video accelleration and optimisation) which the X engine from Ubuntu doesn't.

Having been trough all this myself, I will end in saying:
Why worrie?
:D

/P

---

### Post by Elijahg on 2005-09-17
[QUOTE=king_arthur]I know quite a few people may disagree but this is the truth.
It even runs faster, no matter what anybody says, as OSX takes full benefit of the Quartz engine (i.e. full video accelleration and optimisation) which the X engine from Ubuntu doesn't.

Having been trough all this myself, I will end in saying:
Why worrie?
:D

/P[/QUOTE]

I would just like to give Ubuntu a go really, as an alternative to OS X (it's free too). I would probably use it as a web and print server.

I don't think the iMac really supports any type of Quartz. It's only got a Rage Pro with 6Mb of SGRAM... :)

---


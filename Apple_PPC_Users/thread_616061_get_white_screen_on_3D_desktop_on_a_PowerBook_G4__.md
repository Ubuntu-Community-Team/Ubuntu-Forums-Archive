---
title: "get white screen on 3D desktop on a PowerBook G4  1Ghz Nvidia GeForce 5200"
date: 2007-11-17
forum: Apple PPC Users
---

### Post by biogenex on 2007-11-17
HI Guys, 
Recently i installed ubuntu 7.04 Feisty Fawn in a PowerBook G4 1Ghz 768 RAM 60 HD 12'' with Nvidia GeForce 5200 Graphics Card. i use tiger 4.10.11. It works great, but sincerely the most deep reason was to see working the Comp Fuzion 3D Desktop effects. 

I downloaded beryl and installed but when prompts to it get the white screen and have to reset the system because nothing happens.
I see it is already installed and when i try to activate it just get a white screen for 40 seconds or so.

After try a lot of methods it seems everything comes to the Nvidia GeForce 5200 graphics card. even try to uninstall the included drivers, and reinstall them but nothing happened, then i read in some guys website about turning the nvidia card to accelerate but still nothing happens.

In some webforums they say it's rather difficult (close to impossible!!??) to get Beryl or any other 3D Desktop environment if you use a ppc with nvidia. But I do still believe it can be done.
 Actually i saw a youtube video who showed another guy PB G4 using beryl.  

Please somebody explain to me how can put my PB G4 back on track as to use this cool 3D app?

Thanks and forgive the extension of this post

Biogenex:confused:

---

### Post by Auria on 2007-11-17
> 
In some webforums they say it's rather difficult (close to impossible!!??) to get Beryl or any other 3D Desktop environment if you use a ppc with nvidia. But I do still believe it can be done.


honestly i would say the same. Nvidia provide no PPC Linux drivers, so i don't believe you can use your card without driver :( there's the open source driver you currently have, but i don't think you can count on it.

in the long term, the nouveau.freedesktop.org project gives hope, but it's not usable yet

some very knowledgeable users may have a few tips though

---

### Post by frog_pilot on 2007-11-18
AFAIK the freee nvidia driver "nv" doesn't support direct rendering. It has unfortunately only 2D support.

And as Auria said, there is no nvidia driver for Linux developed by nvidia corporation for the ppc-architecture...

---

### Post by stmiller on 2007-11-19
The Nouveau project has a driver out with limited 3D, though you'll have to fetch the sources and compile to try it out.

---

### Post by biogenex on 2007-11-19
HI Auria, Thanks for the message, quite sorry to hear that. Because it certainly set you on limb. However i'd give a look at the project you mention.

---

### Post by biogenex on 2007-11-19
Ok, i'd give it a try. Thanks

---


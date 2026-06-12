---
title: "nvidia-glx upgrade problems"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by deuchar1 on 2007-05-23
Hey peeps,

Would the following error, when trying to install an automatic update for my graphics card, mean anything to any of you?.....

E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb: subprocess pre-installation script returned error exit status 2

---

### Post by Happy_Man on 2007-05-25
Uh-oh.... that's not good. I suggest trying a different set of servers.

---

### Post by deuchar1 on 2007-05-29
Bummer. Do you mean different repositories? I'm using the default ones with Multiverse and Universe enabled.

---

### Post by tseliot on 2007-05-29
try this:
```
sudo rm /var/cache/apt/archives/nvidia-glx_*.deb
```

then try to update the system again

---

### Post by deuchar1 on 2007-06-01
Still getting the same problem. 
Out of curiosity, what did that line of code do? Was it removing the archived .deb file so it could be redownloaded?

Any more suggestions guys? It has me stumped :(

---

### Post by Happy_Man on 2007-06-01
Yes, that's exactly what it was doing. Here's a bit more of a breakdown:

"sudo" Run w/ root permission for the command

"rm" remove

"/var/cache/apt/archives/nvidia-glx_*.deb" Path to the file, the * indicates anything at all. 

And, so, yeah!

Jeez, I'm bored.

---

### Post by bouncingmolar on 2007-10-03
> **tseliot said:**
> try this:
```
sudo rm /var/cache/apt/archives/nvidia-glx_*.deb
```

then try to update the system again

 I had the same problem (same error code) when trying to install the nvidia-glx driver. This solution looked like it was working (the deb file was removed) and then when I tried to install the package, it had to download it. It was all looking good until it tried to configure it and then it gave the same message 

> E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-16.29_i386.deb: subprocess pre-installation script returned error exit status 2

---

### Post by misterclaw on 2007-10-04
I have been using ubuntu since dapper and I have yet to be able to use anything but the NV drivers.  When I try to use the glx-new drivers I get the same error:

nvidia-glx-new subprocess pre-installation script returned error exit status 2

Even after I updated to gutsy I get the same error.  It mystifies me to no end.

---

### Post by orentini on 2007-10-06
I have been having the exact same problem,

Envy solved it for me ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)).

Good luck.

---


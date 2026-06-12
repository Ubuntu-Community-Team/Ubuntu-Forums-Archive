---
title: "RoseGarden -No audio!"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-07
Other then this program, my audio seems to be set up ok. Got this message...:

System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
This may mean you are using a Linux system with the kernel timer resolution set too low. Please contact your Linux distributor for more information.

---

### Post by dbbolton on 2007-06-07
> **FleetAdmiral74 said:**
> Other then this program, my audio seems to be set up ok. Got this message...:

System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
This may mean you are using a Linux system with the kernel timer resolution set too low. Please contact your Linux distributor for more information.
do you have jackd installed? do you have a low-latency kernel?

---

### Post by FleetAdmiral74 on 2007-06-07
Well I just installed jackd via synaptic, same message.

I have no idea if I have a low latency kernel. Messing around with that sounds like it could mess up my system though...

in terminal, among other things i get ```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

---

### Post by dbbolton on 2007-06-07
> **FleetAdmiral74 said:**
> Well I just installed jackd via synaptic, same message.

I have no idea if I have a low latency kernel. Messing around with that sounds like it could mess up my system though...

in terminal, among other things i get ```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```
booting a different kernel won't hurt your system. 

you might give [Ubuntu Studio](http://ubuntustudio.org) a try. it comes with a low latency kernel, and a lot of audio software (like jack and rosegarden) pre-installed.

---

### Post by FleetAdmiral74 on 2007-06-07
Is ubuntu studio directly related to this Ubuntu foundation, or just some people who took the code and modified default stuff? Cause I like the solid support and userbase here...if Ub Studio is different enough then I think I will stay...

---

### Post by dbbolton on 2007-06-08
> **FleetAdmiral74 said:**
> Is ubuntu studio directly related to this Ubuntu foundation, or just some people who took the code and modified default stuff? Cause I like the solid support and userbase here...if Ub Studio is different enough then I think I will stay...
the link that i gave you will answer those questions. the site says that these forums are the official support for ubuntu studio. but, if you're not comfortable switching, don't do it.

---

### Post by rofthorax on 2007-08-21
Ubuntu Studio site is not up, they are in transition.. I suppose I could use the Wayback Engine to find out what was on the site in its last location, but these smart individuals (I'm being sarcastic) didn't bother to put a date on the message.. 

[http://web.archive.org/web/*/http%3A//ubuntustudio.org/](http://web.archive.org/web/*/http%3A//ubuntustudio.org/)

[http://web.archive.org/web/20070509020930/http://ubuntustudio.org/](http://web.archive.org/web/20070509020930/http://ubuntustudio.org/)

Well that is about as much as you can get.. It looked like a professional operation, but not professional enough to constitute a 10 dollar web account..  That's pathetic..

Evidently Ubuntu Studio is dead..  

Note, get the "wayback search" bookmarklet here, its a great way to look at pages that may have come down or may no longer be in esitence, or to look at web pages that have changed:

[https://www.squarefree.com/bookmarklets/search.html](https://www.squarefree.com/bookmarklets/search.html)


Kiernan

---

### Post by FleetAdmiral74 on 2007-08-22
Can someone else confirm Ub Studio is dead?

---

### Post by very_japi on 2007-08-28
Ubuntu studio is alive, just checked. Didn't work for me cuz they only distribute i386 and i need AMD64. Linux is great, don't get e wrong, but since everything is so configurable and flexible (to the extent of the system's latency) everything gets really complicated as well.

My personal solution, dual boot with windows(or OS) and get Sibelius, FInale, Acid, or something like that. Linux is NOT made for artists. (at least not yet).

---


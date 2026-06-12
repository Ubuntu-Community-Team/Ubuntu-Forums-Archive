---
title: "confused...Again"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-05-15
yes i need more help
i've got Linux up and running but my graphics card is not installing corectly, nor is nost of my hardware, eg. cd drives mmc, and ow i tried to listen to some music and apparently i need some kind of sound plugins???...
what are these things and where might i find them
heres hoping for a fast response that will help me with my problems

---

### Post by Hobo Joe on 2007-05-15
Get [Envy.]("http://www.albertomilone.com/nvidia_scripts1.html")
Install the proper driver for your card.

For sound drivers:
To check the you don't have the driver installed, run:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
Then run:
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Then reboot.

Tell me what happens next.

---

### Post by 99bluefoxx on 2007-05-15
i do this through the terminal right?

---

### Post by Hobo Joe on 2007-05-15
Right.

In case you don't know how to get to it, you go applications>accessories>terminal.

---

### Post by 99bluefoxx on 2007-05-15
all right
got it
thanks
i'll repost once it finishes downloading, only 100mbps connectionp

---

### Post by 99bluefoxx on 2007-05-15
uh oh
downloaded the envy but it says "error:dependancy is not satisfiable: modual-assistant", in red bold text; in the status bar
now what??

---

### Post by AAM on 2007-05-15
yes

---

### Post by 99bluefoxx on 2007-05-15
> **AAM said:**
> yes

huh??
yes what?

---

### Post by Hobo Joe on 2007-05-15
Ok,I just found out that Envy is in Synaptic.

Make sure all your repo's are enabled,(settings>repositories while in Synaptic) then search Envy and install it.

---

### Post by 99bluefoxx on 2007-05-15
i tried tthose terminal commands yiu gave me and after restarting it wrecked my gui, so i did a fresh install
keep in mind that this is only my second day using linux
thanks for help so far though

---

### Post by 99bluefoxx on 2007-05-15
i tried those terminal commands yiu gave me and after restarting it wrecked my gui, so i did a fresh install
keep in mind that this is only my second day using linux
thanks for help so far though

---

### Post by 99bluefoxx on 2007-05-15
i tried those terminal commands yiu gave me and after restarting it wrecked my gui, so i did a fresh install
keep in mind that this is only my second day using linux
thanks for help so far though

---


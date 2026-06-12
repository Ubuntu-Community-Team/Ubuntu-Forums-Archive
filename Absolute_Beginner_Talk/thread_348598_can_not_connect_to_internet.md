---
title: "can not connect to internet"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by outfade on 2007-01-29
I am a complete 99% linux n00b.

I built a new pc, 300 gb hard drive Western Digital.
1gb (2 512 sticks) of ddr ram.
intel pentium 4 processor (3.0 ghz)
regular cd rom reader.

P4M800PRO-M motherboard

standard peripherals, ubs mouse.
nvidia geforce video card, etc.

everything works great, however, I have NO IDEA how to install the drivers for the motherboard etc. My network card, I can not connect to the internet.

I know ctrl+alt+F1 opens up my console, and ctrl+alt+F7 opens back up my x-window environment.

I planned on purchasing windows, but my buddy turned me on to the Ubuntu distribution of Linux, which I was very pleased with messing around on his computer.

If i could get my internet connection active (using a router/modem, high speed internet LAN) and get world of warcraft and ventrillo installed, I would be a happy camper. If anyone can possibly help hold my hand through this process, there is no other knowledge I seek.

I can be contacted on AIM, via the screen name Jefbuchanan for quicker responses.

thank you so much in advance if you will be my shephard.

---

### Post by Denn1s on 2007-01-29
wich do you say is your network card?

---

### Post by outfade on 2007-01-29
VT8237R integrated LAN.

---

### Post by outfade on 2007-01-29
bump, someone please help me.

---

### Post by outfade on 2007-01-29
VIA VT823x PCI Fast Ethernet Adapter

is the onboard Lan device.

---

### Post by skyhopper88 on 2007-01-29
I'm a newb too, so I probably can't help much. What does 'sudo ethtool ethx' give you in a terminal? (x=# your adapter was assigned)

---

### Post by outfade on 2007-01-29
do i type that into terminal? i have no idea what to put in the place of the x, I do not know what number it was assigned.

=((

---

### Post by IanW on 2007-01-29
> **outfade said:**
> do i type that into terminal? i have no idea what to put in the place of the x, I do not know what number it was assigned.

=((


If it's the only network device you have installed, then try eth0

---

### Post by outfade on 2007-01-29
there is no network device installed, and I do not know how to install a network device

---

### Post by outfade on 2007-01-29
also, I tried eth0, eth1, eth2, to no avail saying each did not exist.

---

### Post by skyhopper88 on 2007-01-29
Yeah, terminal. It's probably 0 or 1, try those. If not, look under system-asministation-networking. It should have it listed there in the pull tab. I'm on Windows right now so I'm wingin this. Bare with me.

---

### Post by skyhopper88 on 2007-01-29
Hm, it might not be supported then, most are recognized when you install, mine was. What does 'ifconfig' give ya?

---

### Post by outfade on 2007-01-29
ifconfig says stuff about local loopback, and loopback running, bet yeah I really appreciate it.

the pull tab does not present anything other than what looks like a dummy connection meant for setting up a dial-up modem connection.

nothing for my highspeed. and yeah, i been looking at other forums where people have had similar problems with this LAN device coming with other chipsetted motherboards.

i would like a simple solution, 10 bucks for a PCI ethernet card, could I just pop it in and bid my problem adieu?

---

### Post by skyhopper88 on 2007-01-29
I've been considering doing that for myself actually. Just look and see if what you're looking to buy is well suppored. Ubuntu can see my onboard, so I'm not doing that just yet. Good luck, I'm booting back into Ubuntu to see if I can get my connection up again.

---


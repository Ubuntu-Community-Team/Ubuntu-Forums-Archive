---
title: "Asus G73SW USB sound issue."
date: 2011-08-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Sudo-Geek on 2011-08-31
I am currently trying to completely commit to Linux/Ubuntu, and never use that other OS again (you know who), unless I absolutely have to. I have an ASUS g73SW and have come across a whole gaggle of issues that I in some weird way enjoyed ferreting out and solving. However, as of today I do believe I have met my match and cannot fix this issue alone. I am unable to get my unit to produce sound via USB. The 3.5mm works great, my on-board speakers also work great, but I have an Insignia brand USB soundbar that I really enjoy that I cannot get to work. Tried several times to no avail. Sound bar MN is NS-NBBAR. 

root@jay-G73Sw:~# lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 13d3:5122 IMC Networks 
Bus 001 Device 003: ID 8086:0186 Intel Corp. WiMAX Connection 2400m
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by MikeMcM on 2011-10-18
Let me share in your first cup,  Sudo-Geek. 

Have you checked to see whether or not it is simply being muted in the ALSA mixer settings?  I also have a G73SW,  and I have noticed when I plug/unplug my headphones,  I must go into my mixer panel and un-mute the speakers or the headphones.  

Just a thought.
:)

---


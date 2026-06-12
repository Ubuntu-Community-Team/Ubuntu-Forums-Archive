---
title: "Internet Issues"
date: 2007-12-05
forum: Apple Intel Users
---

### Post by kshannon on 2007-12-05
This has probably been answered a million times but it just isn't in terms I understand.  Sorry I am a beginner.  I have tried to do this several times using the wiki but i just can't figure it out.  I have a macbook Intel Core Duo that I run OSX and windows through bootcamp.  I just yesterday decided to try to run Ubunto using Parallels desktop and place Ubuntu on my external harddrive.  It worked but now I just don't understand how to get my wireless working.  Like I said I am a huge Noob and it would be appreciated if you could respond in a way I can understand. 

Thank You 

kshannon

---

### Post by Smutronic on 2007-12-05
You have to be more specific.
Did you work through the Tutorial in the Sticky-Post? What exactly doesnt work? Is your hardware detected? Which driver do you use?

---

### Post by kshannon on 2007-12-05
The hardware is not detected....and i attempted to follow the steps in the sticky

---

### Post by Smutronic on 2007-12-05
Try this and post the output:

```
sudo lshw -C network
```

---

### Post by kshannon on 2007-12-05
kevin@Kevin-Ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@00:05.0
       logical name: eth0
       version: 00
       serial: 00:c6:3f:21:25:ce
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=10.211.55.4 latency=0 multicast=yes
       resources: ioport:4c00-4c1f irq:10

---

### Post by cyberdork33 on 2007-12-05
you are in a VM, you should not have to directly access the hardware on your machine. It is all virtualized in the VM.

---


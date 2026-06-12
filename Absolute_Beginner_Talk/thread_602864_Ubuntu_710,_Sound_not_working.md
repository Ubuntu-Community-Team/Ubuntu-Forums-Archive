---
title: "Ubuntu 710, Sound not working"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by A dreamer on 2007-11-04
Hi,
I have installed Ubuntu 710 and there is no sound. If I install kubuntu there is sound. Is there anybody who have an idea of what might be wrong. The sound system on my motherboard is:NVidia nForce, Realtec ALC650D.
BR,
A dreamer

---

### Post by Pumalite on 2007-11-04
What's the output of:

sudo lshw -C sound

---

### Post by A dreamer on 2007-11-04
> **Pumalite said:**
> What's the output of:

sudo lshw -C sound

  *-multimedia:0 UNCLAIMED
       description: Multimedia audio controller
       product: nForce Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: c2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0 maxlatency=12 mingnt=1
  *-multimedia:1
       description: Multimedia audio controller
       product: nForce Audio
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       version: c2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0

BR,
A dreamer

---

### Post by Pumalite on 2007-11-04
The UNCLAIMED thing is a problem. You might want to try this first:

sudo apt-get install linux-backports-modules-generic

Reboot

---

### Post by A dreamer on 2007-11-04
Hi.
Thanks, I'll try that. But just a question:
what is back-port-modules ?

BR,
 A dreamer

---

### Post by Pumalite on 2007-11-04
It's supposed to make the kernel load the module for the card. (I think)

---


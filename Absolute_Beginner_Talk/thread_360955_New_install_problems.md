---
title: "New install problems"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by serverdude on 2007-02-13
Having an issue installing Ubuntu 6.10 for the first time.  Copied ISO to CD, and tried installing default, and basic configs.  Getting the following message on both attempts:

[118.206121] <0>Kernel panic - not synching: Attempted to kill init!
[118.206121] _ (blinking cursor)
Server just hangs out here.


Attempting to install OS for first time on Compaq Proliant G1 server, (4) x 200Mhz processors, 512Mb RAM.

Also had issues attempting to instal CentOS on this server.

Any suggestions?

---

### Post by nhandler on 2007-02-13
You can try downloading the alternate installation disk. That isn't a live cd, and doesn't have as nice an installation, but it might work.

---

### Post by sacedric on 2007-02-13
I saw this as well. But I think it had something to do with installing on my AMD64 and not having that version of Ubuntu? Have you tried re-burning the ISO slower?

---

### Post by coolen on 2007-02-14
I had a similar problem on my AMD64 processor. My solution was to either install the x86 version (which I did), or boot with the noapic option (which was suggested by the error message).
My guess is your processor can't handle something the kernel wants to do. Google your processor type for known kernel issues. You'll just have to go to a command line and type "live <option>".

---


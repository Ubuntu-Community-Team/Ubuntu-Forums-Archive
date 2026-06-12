---
title: "rt kernel fail to resume"
date: 2009-06-26
forum: Apple Hardware Users
---

### Post by Rog-Mahal on 2009-06-26
I recently upgraded to Ubuntu Studio 9.04 on my Macbook 2,1. Everything is working great so far, except for the rt kernel. 

I guess my first question is: do I need the rt kernel? I've read some things about multicore processors and things like ext4 (which I'm using) that cut down on latency anyway. 

Anyway, to the actual problem: My computer goes to sleep without a problem, but when I try to resume I get a few errors, the last of which is "USB 5-1 failed to initialize" or something like that. If it's referring to the same designation as lsusb, that means my whole usb hub isn't reinitializing.

```
Bus 001 Device 006: ID 05ac:8501 Apple, Inc. Built-in iSight [Micron]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 05ac:8205 Apple, Inc. Bluetooth HCI MacBookPro
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 05ac:8240 Apple, Inc. IR Receiver [build-in]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ac:021a Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I know the rt kernel is notorious for issues, but does anyone have a fix for this?

Thanks a lot!

---


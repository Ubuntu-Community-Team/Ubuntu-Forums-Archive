---
title: "Is there a way to use a Cisco Console cable on Ubuntu?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by ire on 2007-04-30
Hi there.

New user to Ubuntu here, came over from the Solaris world.

Anyhow, I am running 6.10 on a Lenovo t60 and I'd like to be able to connect to routers and what not via USB -> Serial Adapter using a Cisco Console cable.

In the solaris world, I used 'tip', but I don't think that's an option here.

Any suggestions on how I could go about this?

Thanks in advance

- Pete

---

### Post by wirelessmonkey on 2007-05-01
Keyspan usb/serial adapters actually have a kernel driver which is enabled by default in the generic kernel.
minicom is a perfectly suitable terminal emulator and works fine w/ cisco equipment, but is, IMO, a pain to configure.



WM

---


---
title: "[SOLVED] Resolution of Hardy running on VMware Server"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by ubegginer on 2008-02-05
I just installed Hardy Heron on a VMware Server virtual machine.  The problem however i have found is it only lets me use 640x480 or 800x600 as the resolution.  Is this just the way Hardy is right now or is there any way i can run this at a 1280x800?

---

### Post by dcstar on 2008-02-05
> **ubegginer said:**
> I just installed Hardy Heron on a VMware Server virtual machine.  The problem however i have found is it only lets me use 640x480 or 800x600 as the resolution.  Is this just the way Hardy is right now or is there any way i can run this at a 1280x800?

Have you correctly installed VMware tools?, because I can run it at whatever res I like.

---

### Post by Shazaam on 2008-02-05
Did you install VMware Tools to the guest?
If you can't you could try adding the resolutions you want to xorg.conf after backing up your original.

---

### Post by ubegginer on 2008-02-06
thanks, installing VMware tools did allow me to change my resolution.

---


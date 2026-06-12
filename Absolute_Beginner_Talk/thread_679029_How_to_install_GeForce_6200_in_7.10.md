---
title: "How to install GeForce 6200 in 7.10?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Djbb on 2008-01-26
I recently bought a Geforce 6200 (PCI). Before I shut off my computer I typed into the terminal sudo dpkg-reconfigure and switched to a vesa driver. Then after shutting down the computer I stuck the Geforce in and turned the power back on. It goes through the loading splash screen, but after that it goes to a black screen with some text that says stuff like

Starting ana(c)hronistic cron anacron [ok]
Starting deferred execution scheduler atd [ok]
Running local boot scripts [ok]

And it stays there. Forever.

---

### Post by taurus on 2008-01-26
Can you boot your machine into recovery mode from GRUB menu?

If you can, reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
```
You can pick either **vesa** or **nv** from the list, NOT nvidia, and once you get your machine up and running again, then install an nvidia driver for it from the System -> Administration -> Restricted Drivers Manager.

---


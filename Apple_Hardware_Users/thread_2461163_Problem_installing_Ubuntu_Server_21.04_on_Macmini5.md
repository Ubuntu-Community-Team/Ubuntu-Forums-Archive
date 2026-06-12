---
title: "Problem installing Ubuntu Server 21.04 on Macmini5,2"
date: 2021-04-25
forum: Apple Hardware Users
---

### Post by rbrdvr on 2021-04-25
I tried installing Ubuntu Server 21.04 on Macmini5,2. No problem booting the USB or during installation process but the machine freezes when when trying to boot from its EFI, right away, before grub menu, so no diagnostics. I tried using all defaults as far as partitions or file systems go.

I don’t think it’s related to 32bit vs 64bit EFI since this version of mini is supposed to have 64bit, according to [https://everymac.com/systems/apple/m...011-specs.html](https://everymac.com/systems/apple/m...011-specs.html) . But if anyone have any ideas on how to test it, please let me know, I’m a newbie.

The contents of EFI partition looks ok, with all usual files and directories present.

Same problem with Kubuntu 21.04.
Fedora 34 beta boots fine as well as no problem with Ubuntu 18.04 (bodhi 5.x distro).

---

### Post by awamunro on 2021-04-26
Yes I have the same problem on both my MacBook and iMac. 21.04 will not boot left with frozen blank screen. Had to revert to 20.10 on both machines.
Desktop edition not server!

---

### Post by awamunro on 2021-04-27
[COLOR=#666666][FONT=Ubuntu]Bug #1926181[/FONT][/COLOR][COLOR=#666666][FONT=Ubuntu] [/FONT][/COLOR][Ubuntu 21.04 boot fails on MacBook and iMac]("https://bugs.launchpad.net/ubuntu/+bug/1926181") has bee filed.

---

### Post by awamunro on 2021-05-05
A fix has been released

---

### Post by rbrdvr on 2021-05-10
> **awamunro said:**
> A fix has been released

what is the fix? where do I get it? do I just re-download the 21.04 image from the ubuntu site?

thank you!

---

### Post by rbrdvr on 2021-07-29
soved

---


---
title: "Hat is the latest version I can use on a 2006 white MacBook Core2 Duo?"
date: 2018-10-07
forum: Apple Hardware Users
---

### Post by Aggienator on 2018-10-07
After a long time away I thought I would return to Ubuntu. I have an old 2006 white Macbook maxed out at 2Gb of RAM and have installed 14.04 server on it. I wondered how far I can upgrade, and whether it will run the Lubuntu desktop?

Part of the reason for 14.04 server is that I could find a mac iso for it, and can't get any more recent iso to boot in the MacBook.

Any thought gratefully received.

---

### Post by gsahli on 2018-10-07
Try 18.04:
[https://lubuntu.net/downloads/](https://lubuntu.net/downloads/)

---

### Post by francoisdelabre on 2018-10-08
On a Macbook 2,1 late 2006 with 2Gb of RAM, I have installed Ubuntu desktop 16.04.5 LTS (Xenial Xerus) 32 bits.

I have burnt the ISO to DVD, restarted from the DVD and made a standard installation, erasing the entire drive (that should result in BIOS emulation, no pure EFI).

To boot consistently in graphics mode, GFX must be in text mode.
Otherwise, boot will fail every other start (crash on the first boot, boots ok in failure mode the second boot, etc.).
Just add the next line to */etc/default/grub* and run *sudo update-grub* :
GRUB_GFXPAYLOAD_LINUX=text


Everything seems fine : trackpad, wifi, keyboard.

I could even upgrade to Ubuntu 18.04 LTS (Bionic Beaver) 32 bits.
Crash on boot after upgrade, Wayland must be disabled in GDM.
Simply uncomment the line WaylandEnable=false in /etc/gdm3/custom.conf.

No sleep mode.

---

### Post by francoisdelabre on 2018-10-08
Actually, sleep mode works.
It's just been "hidden" in Ubuntu 18.04 (you have to use 'Alt' key when clicking on the power menu to show the suspend control)!

To clarify, I used the "standard" Ubuntu desktop 16.04.5 LTS 32 bits ISO.
It's not a "mac specific" ISO (it seems these mac iso do not exist any more).

---

### Post by mistervito on 2018-10-25
I've installed Ubuntu Mate 18.04 -32bit on a 2006 MacBook with 2gb RAM, Core 2 Duo.  I created 3 partitions, EFI, Root, Swap. Everything installed normally and all the of hardware works. On start up, the screen goes black, however if I hold down the option key on start up I'll see the "Window" drive icon. When I click on that, it will boot to the grub menu and then boot normally, sometimes it fails and I have to do this twice. Will changing GFX to text mode and disabling Wayland fix this and allow the boot to grub normally on start up?

---

### Post by francoisdelabre on 2018-11-03
I had the same issue with EFI mode and finally reinstalled in "BIOS emulation" mode (standard installation, no EFI System Partition). Perhaps it can boot properly in pure EFI mode, but I didn't manage to do it.

---


---
title: "Solution for externel display via thunderbolt"
date: 2013-12-01
forum: Apple Hardware Users
---

### Post by dim-l on 2013-12-01
Hi there! I have Macbook Pro 10,1 and spent a lot of time trying to fix this issue since 13.04

There are a lot of topics about problems with external display so my solutions about problem "how to make fcuking thunderbolt human-friendly":

13.04 Nvidia 310-319:
Everything works fine with hotplug (without the need of plug display before booting)

13.10 Nvidia 325:
The same

The main problem appears when you try to connect external display on i915 drivers (integrated graphic card). I use i915 and vga_switcheroo because for me it's more important to have more battery time and working screen brightness. As you can realize in OS X (with gfxcardstatus) Macbook switches forcible from Intel card to Nvidia when you plug display cable into thunderbolt. So it means you can't connect external screen with only Intel card also in Ubuntu. When I want to plug display I did **echo ON > /sys/kernel/debug/vgaswitcheroo/switch** and then plug it in. Behavior of the system depends on Ubuntu distro - see below:

13.04 Nouveau 1.0.9:
Display detects and appears in display settings but in few seconds I got bug with [kworker-100%-cpu-usage]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1248256"), and a lot of freezing on external display. So it's impossible to work...

13.10 Nouveau 1.0.9:
The same **** but few less freezing

13.10 Nouveau 1.0.10 (from Trusty)
****! It works with no freezing but also with kworker bug. But you can forgot about this bug if you don't care about fan speed and noise.


So conclussion:
If you want to save power using i915 and vgaswitcheroo and also want to use externel screen you have to do this:
1. turn on discrete card using vgaswitcheroo
2. plug in cable into thunderbolt
3. enable screen in display settings

So what I want more:
Still looking for solution about kworker bug =((( Anybody knows for 13.10 and 3.11?

Anybody here with Macbook Pro 11,1 with ONLY Intel card (Iris)? What about thunderbolt on yours devices?

---

### Post by bjmc2 on 2014-01-30
> 
13.10 Nouveau 1.0.10 (from Trusty)
****! It works with no freezing but also with kworker bug. But you can forgot about this bug if you don't care about fan speed and noise.


So what I want more:
Still looking for solution about kworker bug =((( Anybody knows for 13.10 and 3.11?

If you've tried this on Trusty (14.04) and the kworker bug is still present, you might want to file another report. On my bug report, [one of the maintainers specifically asked for more recent reports or else they're closing the bug.]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1248256/comments/2")

---

### Post by ben-rosas on 2014-04-09
bjmc2, I've reported that I have the same bug.
I'm using Ubuntu 14.04 GNOME on a Macbook Pro (retina, 10,1), but I've had the same issue with Fedora, openSUSE and Arch on this machine.
I am not using an Apple thunderbolt display either, I'm using a Dell 30" with display port, but that uses the thunderbolt port on the mac.

I wonder if a band-aid might be to completely disable nouveau and use only Intel graphics?

---

### Post by rev-p on 2014-08-14
Can you please post your kernel .config and the xorg.conf?thanksFra

---


---
title: "ATI Radeon IGP 345 M external monitor problem."
date: 2008-09-20
forum: Arch and derivatives
---

### Post by kagashe on 2008-09-20
I have taken the plunge to try Archlinux.

I use a HP COMPAQ Presario 2500 series Laptop (whose screen is broken) as Desktop through external monitor. The graphic card is ATI Radeon IGP 345 M.

The ati driver in Xorg 7.3 (xserver 1.4) has a bug which makes the external monitor blank. On Ubuntu Hardy Heron I was using vesa till the bug was removed in the next version of ati driver. Although, Ubuntu Hardy Heron was not updated with the new driver, I downloaded the .deb package from Debian Sid and replaced the driver on Hardy (without upgrading xserver).

Yesterday I have installed Archlinux for the first time. When I tested X the external monitor was blank (since it has the same driver as Ubuntu Hardy). Since I knew that the next version of the driver works I enabled testing repo on Archlinux and installed it. Unfortunately it asked me to upgrade the xserver as well (to version 1.5). Now I am getting the display but the keyboard and touchpad does not work. I know that xserver 1.5 is under development and this might happen.

Before deciding to upgrade ati driver on Archlinux I had removed it completely and tried X (forcing it to use vesa). Surprisingly, this did not work (it works on Ubuntu Hardy Heron).

I know that Xorg 7.3 does not require xorg.conf and it is not there in /etc/X11 in Archlinux and I need to create one to use a different configuration than default.

Following are possible solutions:
1.0 You tell me how to make Keyboard and touchpad work on xerver 1.5.
2.0 I can downgrade to xserver 1.4 and you tell me how to use vesa.

Personally I would like to use no 1.0 option because when I use ati driver I can switch off the Laptop display with xrandr (which is not possible with vesa).

I have also posted this on Archlinux Forum.

kagashe

---

### Post by kagashe on 2008-09-22
[quote=kagashe]Following are possible solutions:
1.0 You tell me how to make Keyboard and touchpad work on xerver 1.5.
2.0 I can downgrade to xserver 1.4 and you tell me how to use vesa.[/quote]
Well I could apply option 2.0 myself by running:
> # pacman -S hwd
# hwd -u
# hwd -x
The last command generated a file using vesa driver which I renamed as xorg.conf.

I am not marking the thread as "solved" because I would like to use ati driver asap.

kagashe

---

### Post by afonic on 2008-09-23
You shouldn't have enabled testing repository, many drivers are known to be broken with the xorg in testing.

Arch is several versions ahead of Hardy, are you sure the driver version in the standard "extra" repo is not after the release they solved the problem you had?

---

### Post by kagashe on 2008-09-23
> **afonic said:**
> You shouldn't have enabled testing repository, many drivers are known to be broken with the xorg in testing.

Arch is several versions ahead of Hardy, are you sure the driver version in the standard "extra" repo is not after the release they solved the problem you had?Yes. I am sure because it gives blank screen on external monitor.

I am not afraid of using testing only for Xorg on Arch. I know that the ati driver works because I could see the desktop. But how can I make the Keyboard to work?

I am going to wait for a while and try again.

kagashe

---


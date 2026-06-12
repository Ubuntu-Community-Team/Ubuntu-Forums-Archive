---
title: "[SOLVED] ipw3945 on arch linux"
date: 2008-02-19
forum: Arch and derivatives
---

### Post by JohnnyBoy022 on 2008-02-19
hey everyone, I just installed arch and I'm trying to get wireless working. I have intel pro wireless 3945 card. When I installed from the cd it said something about specifying to use the intel wireless driver. I didn't do this, but from what I've heard that is only so the cd installer can use it, is this correct? arch should have installed iwlwifi drivers automatically anyway?

assuming my drivers are working (which im not 100% sure, how can i check?), now I need help setting up my network. I've always had trouble since its encrypted, and usually when I use GUI tools with other distros (like Ubuntu) I have to select a "hex" option. How do I specify that my key is in hex?

last question, is there any way to scan for available networks? Thanks for any help

---

### Post by bwtranch on 2008-02-20
> **JohnnyBoy022 said:**
> hey everyone, I just installed arch and I'm trying to get wireless working. I have intel pro wireless 3945 card. When I installed from the cd it said something about specifying to use the intel wireless driver. I didn't do this, but from what I've heard that is only so the cd installer can use it, is this correct? arch should have installed iwlwifi drivers automatically anyway?

assuming my drivers are working (which im not 100% sure, how can i check?), now I need help setting up my network. I've always had trouble since its encrypted, and usually when I use GUI tools with other distros (like Ubuntu) I have to select a "hex" option. How do I specify that my key is in hex?

last question, is there any way to scan for available networks? Thanks for any help

Hi, yeah, the same shell commands work in arch just like Ubuntu. Need to run the good 'ole favorites:
lspci
lsusb
iwconfig
ifconfig

In Arch run```
nano /etc/rc.conf
``` and look at that one closely. The thing about hex and keys, I don't know about. But, we do need some info on the hardware to get started.

---

### Post by Crooksey on 2008-02-20
[http://wiki.archlinux.org/index.php/Ipw3945#.._using_stock_kernel_.28default.29](http://wiki.archlinux.org/index.php/Ipw3945#.._using_stock_kernel_.28default.29)

iwlwifi is still buggy, please use ipw3945.

---

### Post by JohnnyBoy022 on 2008-02-20
I think iwl3945 is the problem, I'm going to have to have to go back to ipw3945. I got it working, but only about half the time. I can go ahead and marked this as solved though.

---

### Post by PurposeOfReason on 2008-02-21
> **Crooksey said:**
> [http://wiki.archlinux.org/index.php/Ipw3945#.._using_stock_kernel_.28default.29](http://wiki.archlinux.org/index.php/Ipw3945#.._using_stock_kernel_.28default.29)

iwlwifi is still buggy, please use ipw3945.
It's been working perfect for me minus that the led doesn't turn on when I'm using wireless.

---


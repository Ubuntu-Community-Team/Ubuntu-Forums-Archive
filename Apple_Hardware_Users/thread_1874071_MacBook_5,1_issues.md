---
title: "MacBook 5,1 issues"
date: 2011-11-02
forum: Apple Hardware Users
---

### Post by BELzEBUB on 2011-11-02
Hello I use Ubuntu on nearly all of my devices and since a few days it also runs on my MacBook5,1 (late 2008). Because I want to keep me system as simple as possible I decided to boot Ubuntu without BIOS Emulation be installing grub-efi which works fine.

But I still have two issues when I boot Ubuntu via EFI:

1. I can not control the backlight. I read in an old article that is normal but the article was from the last year.
Is there a fix availible or is the statement still up to date?

2. When I switch to virtual terminal e.g. tty1 I only see a blackscreen. Also for this problem I read that it is normal but this article was very old too and I found out that efifb was patched to work with MacBook5,1. And if I disable the kernel parameters "quiet splash vt.handoff=7" I can see kernel messages while booting. But it does not work for virtual terminals.

---

### Post by alexmurray on 2011-11-02
For brightness control, try adding the following to the Device section of your /etc/X11/xorg.conf

```
Option "RegistryDwords" "EnableBrightnessControl=1"
```

And the second issue is the nature of the proprietary nvidia driver not cooperating properly with efifb - AFAIK there is no known fix for this.

---

### Post by HotForLinux on 2011-11-03
I have a different issue when switching to virtual terminals in Natty on macbook pro but,  strange though it may seem, switching to virtual terminals works perfect using a one year old Suse Live-Cd. What is more, the first virtual terminal has even a nice background. Never seen that before!

---

### Post by BELzEBUB on 2011-11-05
> **alexmurray said:**
> For brightness control, try adding the following to the Device section of your /etc/X11/xorg.conf

```
Option "RegistryDwords" "EnableBrightnessControl=1"
```

And the second issue is the nature of the proprietary nvidia driver not cooperating properly with efifb - AFAIK there is no known fix for this.

Didn't work with EFI.

---


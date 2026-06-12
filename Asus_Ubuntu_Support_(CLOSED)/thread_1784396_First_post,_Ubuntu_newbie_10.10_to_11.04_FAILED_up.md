---
title: "First post, Ubuntu newbie: 10.10 to 11.04 FAILED upgrade"
date: 2011-06-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Kufnayr on 2011-06-16
Hello all! This is my first post, let me just start off by stating my equipment. I have a 1005PEB Asus Eee Pc netbook that was running great on 10.10. I tried to upgrade to 11.04, during the installation portion of the upgrade, my internet crashed, my computer froze, then my computer crashed. A series of very unfortunate events. So, currently after the netbook boots, GNU GRUB version 1.98+20100804-5ubuntu3 shows 8 options, 3 of which are recovery modes, two of which are memory tests.

When I try to launch Ubuntu, with Linux 2.6.35-28-generic, i get the following:
```

udevd[372]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{} to match a parent device, in /etc/udev/rules.d/56-hpmud_support.rules:10


udevd[372]: SYSFS{}= will be removed in a future udev version, please  use ATTR{}= to match the event device, or ATTRS{} to match a parent  device, in /etc/udev/rules.d/56-hpmud_support.rules:12

init: udevtrigger main process (378) terminated with status 1
init: udevtrigger post-stop process (381) terminated with status 1
init: udevmonitor main process (377) killed by TERM signal
The disk drive for / is not ready yet or not present
Continue to wait: or Press S to skip mounting or M for manual recovery

```Let my just note that my Eee Pc I do still have the Win7 Starter disk that came with the netbook, however the eeepc does not have a disk drive and im not sure whether or not I need a cd-key for it? If I do, the cd-key sticker on the bottom of my netbook is illegible. I would love to keep ubuntu but I'm not sure what to do. Also, I would love to salvage the old files if at all possible however my tech-savyness is limited. any suggestions?](*,)

---

### Post by PenguinMan2907 on 2011-06-17
Just copy ubuntu 11.04 onto a usb, boot from it and install it over your existing copy.:KS

---

### Post by kamyon on 2011-07-13
I had a similar problem, and this post worked for me:
[http://askubuntu.com/questions/38617/root-filesystem-check-fails-after-power-failure-during-installation/40058#40058](http://askubuntu.com/questions/38617/root-filesystem-check-fails-after-power-failure-during-installation/40058#40058)

---


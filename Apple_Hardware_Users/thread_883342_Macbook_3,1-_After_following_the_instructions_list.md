---
title: "Macbook 3,1- After following the instructions listed here, WIFI still does not work."
date: 2008-08-07
forum: Apple Hardware Users
---

### Post by LuminousPath on 2008-08-07
I extracted the Broadcom driver from the Leopard DVD. I installed NDISWrapper via Add/Remove. After it installed I set it up to use the bcmwl5 driver that I got from the Leopard dvd. It worked and reports that the appropriate hardware is present. I opened up the terminal and typed in sudo modprobe ndiswrapper. When I open network settings there's still only two options: Wired Connection and Point to Point connection. Been at this for two hours so far, anyone have any ideas?

I have a Macbook 3,1 with a Broadcom BCM4328 and Ubuntu 8.04

---

### Post by volanin on 2008-08-07
Try this:

```
$ ndiswrapper -l
```

This will list the drivers installed, and report if the hardware is present.
If everything is ok, try this:

```
$ sudo ndiswrapper -m
```

This will create the necessary aliases/files to let the kernel know that your
hardware should be managed by ndiswrapper. Now this:

```
$ sudo update-initramfs -u
```

To recreate your boot image with the necessary information.
And reboot!
:)

---


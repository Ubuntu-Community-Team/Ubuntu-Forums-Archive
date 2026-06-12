---
title: "Freezes during boot (13.10 on Asus M70Vn)"
date: 2014-01-17
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Frantic_Earthling on 2014-01-17
I have an ageing Asus M70Vn which I was reluctant to part with despite its age.

I decided to remove one of its two hard disks to replace it with an SSD in order to gain a bit of speed.
My choice: a Sata III 120 Gb Kingston disk.
My M70Vn had been running with a Window$8/Ubuntu 12.04 LTS dual boot.
I re-installed both OS on the SSD, but opted for Ubuntu 13.10 this time.
Everything went flawlessly (old BIOS! no UEFI :D) however, I had random freezes when I booted from Ubuntu.
Sometimes it would boot without a hitch and sometimes, it would hang right after the purple background and leave me only with a blinking cursor.

In case someone is stuck with the same problem, this is the fix that did it:

I switched off ncq, which by the way did not seem to make disk accesses any slower.
You need to add "libata.force=noncq" in the GRUB line starting with GRUB_CMDLINE_LINUX

In terminal:

```
sudo gedit /etc/default/grub
GRUB_CMDLINE_LINUX="libata.force=noncq"
update-grub
```

This fix (and others) is well explained here:
[http://www.howtoeverything.net/linux/hardware/ubuntu-freeze-issue-after-ssd-upgrade](http://www.howtoeverything.net/linux/hardware/ubuntu-freeze-issue-after-ssd-upgrade)

---


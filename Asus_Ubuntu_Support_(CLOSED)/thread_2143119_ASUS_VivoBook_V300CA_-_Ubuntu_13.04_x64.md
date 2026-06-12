---
title: "ASUS VivoBook V300CA - Ubuntu 13.04 x64"
date: 2013-05-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by tabsterleir on 2013-05-07
So I purchased this Ultrabook and due to the information on the web being pretty sparse I took the risk of hoping it would run Ubuntu. I'm happy to report it does and I am posting this thread in the hopes that future purchasers of this Ultrabook see this thread.

What works:
- Wireless
- Bluetooth
- Function Keys, all functions working as expected
- HDMI
- Audio (including Jack)
- VGA
- Ethernet
- SD Reader
- Touchpad

What doesn't:
- Nothing, everything worked out of the box

Notes:
- Wifi signal is weak due to the ath9k bug [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1160188"). Should hopefully be fixed soon
- Audio is affected by this bug [here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1175095"). Fixed by using preleased updates (I think kernel 3.8.0-20 fixed it)
- Brightness FN keys have a bug where the Brightness up key doesn't work properly. Change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi='!Windows 2012'" in /etc/default/grub to fix (note the ' marks around !Windows2012)

---


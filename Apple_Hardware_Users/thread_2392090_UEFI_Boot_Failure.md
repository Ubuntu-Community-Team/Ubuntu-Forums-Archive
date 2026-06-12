---
title: "UEFI Boot Failure"
date: 2018-05-16
forum: Apple Hardware Users
---

### Post by pongor on 2018-05-16
Hi guys,

I have an old Macbook Pro (2010) that use UEFI interface. Awhile back when Mac stopped supporting upgrades on this technology I switched to running different flavors of linux on it. Every flavor I tried worked fine and the OSes all performed well. I recently had Ubuntu Mate on the laptop and whilst installing some NASA software the laptop crashed and wouldn't boot. When I woulf start up the laptop I would get to a GRUB> prompt, informing me I have ma minimal command set to work with. I could ls my devices and see my hdd and my filesystem.

I left it to one-side for a few weeks until I had enough time to work on it. I decided I would install Ubuntu 18.04 on there and create a UEFI bootable USB drive. UEFI found the USB drive and starting the process but quickly failed to the GRUB> command prompt and the restrictive instruction set. I wanted to see if anyone had any suggestions for resolving the issue.

I have tried using:
1. The Super_GRUB2 application but this did not work.
2. The Rescatux usb application but again it failed.
3. Obviously, it won't run the live usb.

Any thoughts or help would be greatly appreciated.

Thanks

---

### Post by howefield on 2018-05-16
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by oldfred on 2018-05-16
Do not know Mac, but rEFInd was originally Mac orientated.

[http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/)

You may be able to create a rEFInd boot flash drive and use it to boot or fix things.

---


---
title: "Bluetooth on MacBook3,1 Santa Rosa"
date: 2008-01-23
forum: Apple Intel Users
---

### Post by bluec on 2008-01-23
Hi all, some questions the macbook3,1 ubuntu users.

Is the macbook3,1 bluetooth device connected on the USB or the PCI? Could someone with a working bluetooth please post the output of the detected device from lspci and/or lsusb? Is there some kernel config parameter that I might need to set to make the device available? Or is there even a BIOS option (do these things even have a BIOS?) that I need to set to switch the bluetooth on? What chipset is the bluetooth device?

Reason for me asking:

I have followed the ubuntu wiki instructions and managed to get fedora 8 x86_64 working really well on the MacBook3,1. The *only* thing that doesn't work is the bluetooth and its really weird because the bluetooth device doesn't seem to be found at all - neither lspci nor lsusb pick up any bluetooth device. Weird.

Thanks for your help
Chris

---

### Post by bluec on 2008-01-23
Man, I should learn to research properly before posting. My apologies.

For anyone else, the fix is in the redhat bugzilla: [https://bugzilla.redhat.com/show_bug.cgi?id=371061#c2](https://bugzilla.redhat.com/show_bug.cgi?id=371061#c2)

---


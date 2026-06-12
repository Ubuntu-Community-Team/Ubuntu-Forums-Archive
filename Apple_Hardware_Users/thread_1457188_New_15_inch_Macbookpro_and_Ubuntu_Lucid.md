---
title: "New 15 inch Macbookpro and Ubuntu Lucid"
date: 2010-04-18
forum: Apple Hardware Users
---

### Post by subbushri on 2010-04-18
Just received my new 15" MacbookPro with Core i5 CPU. Lucid install was smooth. Running on restricted Nvidia and Broadcom WL driver.

Couple of issues.

1) Sound not working, but I haven't spent much time investigating it.
2) I have installed pommed but Keyboard backlight is still not working.
3) Linux is unable to find Integrated Intel HD Graphics card.

In Mac OS X card shows up as Device ID 0x0046. In Linux when I run lspci it does not even show up in lspci output. Is it coz Apple is not enabling that card for Bootcamp?

Below is the lspci output.

---

### Post by alexmurray on 2010-04-18
Yep, I'd say you'd need to boot via EFI for the Intel card to show up (just like the in the previous generation MBP's which had dual Nvidia graphics chips).

---

### Post by subbushri on 2010-04-25
As per your suggestion I tried EFI boot method. It is failing to boot and gets stuck at initrd for ever. I am using lucid 10.04 LTS. Any suggestions to figure out what's going wrong.

---


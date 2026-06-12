---
title: "Image loading failed. Reload Image! Error on MacBook 4,1"
date: 2010-07-03
forum: Apple Hardware Users
---

### Post by Tylerjd on 2010-07-03
I have a major problem. I just installed Ubuntu 10.04 amd64 on /dev/sda3 with the bootloader on /dev/sda3. Just like it says in the instructions. The install went without a hitch, rebooted, and choose Linux from the rEFIt menu and suddenly my fan starts to rev up, and the error ```
Image loading failed. Reload image!
``` comes up. Now I have installed Ubuntu many times before on this laptop, and it always went without a hitch. I googled the error, and nothing came up. Mac OSX boots fine, and I have tried installing Ubuntu multiple times, on different images, on different DVD's, even one that came from Canonical. The error comes before a GRUB2 menu loads.

---

### Post by Tylerjd on 2010-07-05
I somehow fixed the error. I think it was coming from an ill-deployed Clonezilla image, which had gotten stopped halway through th process. I re-imaged the machine, then re-installed Ubuntu, and everything works fine now. Weird.

---


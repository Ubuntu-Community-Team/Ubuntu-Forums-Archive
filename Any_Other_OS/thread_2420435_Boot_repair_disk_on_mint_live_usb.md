---
title: "Boot repair disk on mint live usb"
date: 2019-06-05
forum: Any Other OS
---

### Post by jymere on 2019-06-05
I wanted to install Fedora in dual boot with windows. During the Fedora installation I installed a /boot partition and a /boot/efi partition.
The installation process was good and at starting the computer, then there was only one entry for booting fedora (but no entry for booting windows) in the boot menu.

Then I installed Debian to recover the grub and at the final step I didn't install any MBR on any partition of the computer (I installed it on the usb live ...).
Then there was no entry at all at the boot menu.

I really took care not to format any windows partition during the installation of these two distributions.

In the Bios setting, If I choose the windows manager booting, it doesn't boot. In the EFi setting, I have the same behavior.

Now I am using a Mint live usb to use the boot repair utility. Here is the boot info provided by this utility :

[http://paste.ubuntu.com/p/3wzFggFMh3/](http://paste.ubuntu.com/p/3wzFggFMh3/)

Is it possible to recover the windows entry in the boot menu (I don't really care anymore about the linux (debian) entry) ?

---

### Post by howefield on 2019-06-05
Thread moved to the "*Any Other OS*" forum.

---


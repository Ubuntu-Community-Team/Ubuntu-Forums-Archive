---
title: "Macbook Pro 5,4 EFI boot for 12.04"
date: 2012-05-03
forum: Apple Hardware Users
---

### Post by Hatsune Miku on 2012-05-03
Hey everyone! Me and my timid self wants to know if anyone was able to boot a Macbook Pro (5,4/5,5) with EFI. If so, anything special I need to do to help it along? Thanks!

---

### Post by Hatsune Miku on 2012-05-04
*bump*

---

### Post by Paul S on 2012-05-09
I can only answer for an iMac 12,1 (mid 2011) using osx lion. On 12.04, grub-efi works well with with lion osx. But, grub-efi is not part of the installer, and to install it I had chroot into ubuntu from the live cd, then apt-get install grub-efi, then execute "grub-install" to create grub.efi, then manually copy /boot/grub/grub.efi to a mounted /dev/sda1 EFI partition under the name /mnt/EFI/BOOT/BOOTX64.EFI. At this point, grub boots when holding the Option key at boot up. Then I blessed this EFI directory under osx, and that makes it boots first. I'm even surprised that the bluetooth keyboard can up/down arrow and return key in the grub screen.

hth

---


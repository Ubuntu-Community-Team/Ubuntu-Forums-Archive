---
title: "A small advice on making ubuntu liveCD more flexible"
date: 2015-04-15
forum: Apple Hardware Users
---

### Post by dercat on 2015-04-15
I have a late 2012 apple machine. And I have been using Archlinux almost exclusively for two years. Today I decided to try ubuntu on a portable hdd. It is impressively "convenient" and it takes me time longer then expected to install it.
rEFInd is a powerful bootloaders for apple machines. It has some autodetecting ability. An archlinux user knows that his new os is automatically bootable after exec the command "mkinitcpio -p linux" without the aid of grub or anything else.

The problem of ubuntu liveCD is that it will install booting files into the EFI partition. That is a dirty approach(even OS X do not put its booting files in the EFI partition, personally I think only boot loaders should be placed there). This approach becomes completely unacceptable when you want to install Ubuntu in a portable device. And I have to manually delete the boot files of ubuntu, and make a boot file by myself.

So I think ubuntu should use an alternative method. 1) There is a method for the native boot loader to detect a standalone boot.efi which is placed in any partition, 2) ubuntu can also make itself detectable by refind, 3) do nothing, because less is always better.

---


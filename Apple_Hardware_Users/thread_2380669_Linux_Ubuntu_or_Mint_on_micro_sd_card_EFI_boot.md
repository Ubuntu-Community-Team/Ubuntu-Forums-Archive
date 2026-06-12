---
title: "Linux Ubuntu or Mint on micro sd card EFI boot"
date: 2017-12-20
forum: Apple Hardware Users
---

### Post by dizdra64 on 2017-12-20
I have Mac Book Pro early 2015, and installed Hi Sierra & Win 10 with Bootcamp.
I also have another Windows PC with win 7 on it with dual boot with Ubuntu 16.04.
Both PC can boot EFI Linux boot.
My wish is to install Ubuntu 16.04 or Linux Mint 18 on micro sd card  alone bootable to don`t touch Boot from mac (Hi Sierra& win 10) and from Windows &Ubuntu on Win PC.
After several try with some tutorial over internet, such as Virtual player, normal try on ext disk… etc,

 _I didn`t do it, because of my not good knowledge to work with terminal in linux, to get EFI boot, or EFI boot partition on Ubuntu or Linux Mint micro sd card_

[B][U]I always somewhere at the end made some false and after this step, don`t know what to do, and finally give up.
[/U][/B]
Could anybody give me some good tutorial to install Linux Mint or Ubuntu on external HDD with own boot, EFI, to bi be bootable on my both PC-s (Mac & Win PC).
Finally, I would like to install on micro sd card, because both PC-s has micro sd slot and work on both PC-s.
Thank you so much for help.

---

### Post by howefield on 2017-12-20
Thread moved to the "*Apple Hardware Users* forum.

---

### Post by oldfred on 2017-12-20
Can you boot from MicroSD cards on both systems? Not all systems boot them.

Otherwise should be similar to an external flash drive.
External devices with UEFI only boot from ESP - efi system partition and from /EFI/Boot/bootx64.efi.
But default installs of Ubuntu install grub boot loader to ESP on internal drive in /EFI/Ubuntu.
So you have to partition in advance to have ESP partition on external.
After install copy /EFI/Ubuntu to external's ESP and then copy again to /EFI/Boot and rename grubx64.efi to bootx64.efi.
Also change /etc/fstab to have mount of /Boot/efi to UUID of external drive's ESP.

More details:
       Mac full install UEFI boot to flash drive
[http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528](http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528) 
   Manually copy efi files to efi partition on flash drive for booting. Toshiba Satellite S855-5378  by ubfan1
[URL="http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515"]http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515
[/URL]
 UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad 

[URL="http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515"]
[/URL]

---


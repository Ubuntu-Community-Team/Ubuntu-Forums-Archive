---
title: "Install problem on Eee PC 1015PE"
date: 2013-11-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by windfarm on 2013-11-04
Hi,
I've been trying to install Lubuntu 13.10 on an Asus Eee PC 1015PE notebook as a dual boot with the existing Windows 7. It was going well: USB installer created; hard drive partitioned; installer run and reported install was successful.

So when I rebooted after the succesful install, I was expecting to see a menu that allowed me to choose between booting  Windows or Lubuntu. But there is no menu, it just boots to Windows every time. Have I missed something in the install procedure?

I tried booting from the USB stick and running install again, and it tells me that I have both Windows 7 and Lubuntu 13.10 on the machine. So it looks like the Lubuntu install did work, I just can't get to it.

Thanks,

---

### Post by windfarm on 2013-11-04
After booting Lubuntu from the USB again, I found the "Disks" application in the Accessories menu. This told me the Linux partition I had created was not bootable. Clicking on the "More Actions" button below the Volume table and selecting "Edit Partition" I was able to tick a "bootable" box and then click "Change".

When I next rebooted I saw a Grub menu with the options to boot Ubuntu or Windows. All now seems to be working ok.

---


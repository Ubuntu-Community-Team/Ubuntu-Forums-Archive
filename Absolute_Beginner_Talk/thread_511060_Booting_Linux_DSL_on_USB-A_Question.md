---
title: "Booting Linux DSL on USB-A Question?"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by supportbroker on 2007-07-27
Now that I can boot DSL from USB drive...I was wondering

Can I now boot DSL on my USB from any PC or only the one's that have the syslinux file on it

If so, is there any easy way to make it so that it will boot from my USB from any PC

oh yeah-can this be booted up in Linux?

Thanks-BC

---

### Post by NESFreak on 2007-07-27
any pc that supports usb booting will boot it. (or you screwed something up)

from [http://wiki.debian.org/BootUsb:](http://wiki.debian.org/BootUsb:)
To install DamnSmallLinux download the ISO image and as root user go the directory with the dsl-*.iso file and type the following:
```

  mkdir dsl_temp
  mkdir dsl_usb
  mount -o loop dsl-*.iso dsl_temp
  cp -a dsl_temp/* dsl_usb
  cd dsl_usb
  mv boot/isolinux/* ./
  rm -Rf boot 
  mv isolinux.bin syslinux.bin
  mv isolinux.cfg syslinux.cfg
  cd ..
  mkdir usb_pen
  mount -t vfat /dev/sda1 usb_pen
  cp -a dsl_usb/* usb_pen
  umount usb_pen
  umount dsl_temp
  syslinux /dev/sda1
```

---


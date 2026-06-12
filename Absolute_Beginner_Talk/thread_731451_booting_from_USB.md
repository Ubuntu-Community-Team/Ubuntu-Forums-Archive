---
title: "booting from USB"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by the beak on 2008-03-21
I'm trying to set up a USB stick to boot my linux os. I get top the stage where I'm trying to run :

 sudo echo '(hd0) /dev/sdb' > /mnt/boot/grub/device.map

and i get the error :

bash: /mnt/boot/grub/device.map: Permission denied

any ideas?

---

### Post by Nikhil Gohil on 2008-03-21
try changing permissions first. ```
chmod 777 /mnt/boot/grub/device.map
```

---

### Post by the beak on 2008-03-22
Thanks

I'm trying to install grup on the USB at /dev/sdb

when I run this

grub-install --root-directory=/mnt --no-floppy '(hd0)'

gives the error 

/dev/hda1 does not have any corresponding BIOS drive.

but I've never referred to hda1 earlier, what do I need to change from the command?

---

### Post by Nikhil Gohil on 2008-03-22
what tutorial r u using? how large is your usb drive?

---

### Post by the beak on 2008-03-22
I'm using

[http://www.knoppix.net/wiki/USB_Based_FAQ](http://www.knoppix.net/wiki/USB_Based_FAQ)

and replacing sda with sdb in previous lines

---

### Post by anantshri on 2008-03-22
try the other tutorial given in it.

looks much cleaner.

[http://www.knoppix.net/wiki/Bootable_USB_Key](http://www.knoppix.net/wiki/Bootable_USB_Key)

---

### Post by the beak on 2008-03-22
thanks

Can I replace the Knoppix iso for another distro in it?

---

### Post by Nikhil Gohil on 2008-03-22
i dont think you can. you can use [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
for ubuntu gutsy.

realting to the previous method, i dont understand why it dosent work. does ```
sudo echo '(hd0) /dev/sdb' > /mnt/boot/grub/device.map
``` give you any errors? do you by any chance have a mixed scsi and ide drive system?

---


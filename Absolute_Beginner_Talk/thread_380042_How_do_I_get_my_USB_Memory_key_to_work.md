---
title: "How do I get my USB Memory key to work?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by gugglix on 2007-03-09
My USB memory key doesn't appear as a device in Ubunto (Edgy). I know there's power getting to the key because it lights up when it's plugged in. I don't know enough about devices and mounting them. Please help.

Thanks Michael.

---

### Post by george29 on 2007-03-09
most usb memory keys should automount and be present in /media 

if this hasn't happened you can try manually mounting -

make a mount point
```
sudo mkdir /mnt/usbkey
```

then try mounting the usb key
```
mount /dev/sda1 /mnt/usbkey
```

you can then look into automounting if you can access the memory key.

to remove the usbkey
```
umount /dev/sda1
```

---

### Post by gugglix on 2007-03-09
Thanks for your reply.

Your suggestions didn't work. The partition on which Windows XP is loaded is currently mounted as sda1 (this is a dual boot machine).

Cheers, Michael.

---

### Post by DoctorMO on 2007-03-09
so you have scsi or sata hard drive; that shouldn't matter just adjust the sd number;

Are you sure this usb key is a mass storage device, what does it do?

---

### Post by gugglix on 2007-03-09
OK, you wanna hear something weird? I plugged the key into another port and bingo bango bongo it automounted.... I know the first port works because that's what I use in Windows.....

Thanks for your help anyways....!

Cheers, Michael

---


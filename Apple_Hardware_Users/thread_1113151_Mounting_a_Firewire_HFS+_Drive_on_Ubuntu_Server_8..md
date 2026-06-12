---
title: "Mounting a Firewire HFS+ Drive on Ubuntu Server 8.10"
date: 2009-04-01
forum: Apple Hardware Users
---

### Post by gsp8181 on 2009-04-01
Hello

I am trying to get an ubuntu server 8.10 (Running on a spare mac mini) rig to mount a LaCie HFS+ formatted firewire disk. So far, no luck, it does not seem to automount and throws up errors such as 
```
[31535.260418] ohci1394: fw-host0: SelfID is inconsistent [0x807f8896/0x807f8896]
[31535.260465] ohci1394: fw-host0: SelfID is inconsistent [0x807f8896/0x807f8896]
```

mount -a won't do anything

fdisk -l only returns the primary HDD

Tried browsing through /dev and can't find anything usb, firewire or sd* related (apart from the primary HDD sda)

Pointers anyone? :)

---

### Post by cyberdork33 on 2009-04-01
I don't think server will automount. You will need to mount it by hand or add an entry to your fstab.

The error sounds firewire related. Do you have another interface to try?

---


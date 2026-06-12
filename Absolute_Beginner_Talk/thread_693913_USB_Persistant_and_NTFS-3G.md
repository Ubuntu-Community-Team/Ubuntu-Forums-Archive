---
title: "USB Persistant and NTFS-3G"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by scottb613 on 2008-02-11
All.

FYI: Pretty new to linux...

I have my USB Flash Drive loaded with ubunto...
I can mount and read NTFS file systems...
By default - I can not write to NTFS mounted file systems...

I found the references to NTFS-3G package...

Can I load this package on a USB Persistant copy of Ubunto ?
Will the package stay on my chip once loaded - or - will I have to load it each time ???

Thanks,
Scott

---

### Post by HappyFeet on 2008-02-11
boot to usb drive and:
```
sudo su
```
```
apt-get install ntfs-config
```
it will also install ntfs-3g. and yes, it will install permanently.

---

### Post by Ek0nomik on 2008-02-11
> **HappyFeet said:**
> boot to usb drive and:
```
sudo su
```
```
apt-get install ntfs-config
```
it will also install ntfs-3g. and yes, it will install permanently.

After installing I would also type:

```
exit
```

so you are no longer using the terminal for daily things as root.

I would also suggest formatting the USB device to FAT32 for maximum portability.  (Linux and Windows can both natively read FAT32 filesystems)

---

### Post by scottb613 on 2008-02-12
All,

    Thanks for the great responses !!!
    :)
    Awesome how there always seems to be someone to help...
    Greatley appreciated...

    I guess the same would hold true for the NFS package...
    
Regards,
Scott

---


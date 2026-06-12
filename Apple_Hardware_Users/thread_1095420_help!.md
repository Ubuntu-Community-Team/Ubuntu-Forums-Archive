---
title: "help!"
date: 2009-03-13
forum: Apple Hardware Users
---

### Post by 0ra1suicid3 on 2009-03-13
first i installed refit, then instaled linux then i rebooted with refit  but when i select the linux partition  it gives me this:

using load option "usb" error:not found returned from legacy loader

then it gives me this ward message that the firmware refused to boot partition and that it  dosent support external hd  is supported by apple 

in mac, i type ```
diskutil list 
``` 

```
drmons0501w-142177079108:~ simontremblay$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme     *698.6 Gi         disk0
   1:                        EFI                         200.0 Mi         disk0s1
   2:     Apple_HFS Simon HD            425.4 Gi         disk0s2
   3:                        EFI                         272.9 Gi         disk0s3 
```

the 272GB is the linux partition and in disk utility ( the app) it dosent show up)

so i coant boot from the linux and i cant do enything but boot from live cd...

---

### Post by cyberdork33 on 2009-03-13
it thinks you are booting from an external hard drive.

---

### Post by 0ra1suicid3 on 2009-03-13
i am, my internal hd is broken and soon will go to apple store
i am booting from external, people say it possible and other say itnot, but i think it is and i realky eant to have linux

---

### Post by cyberdork33 on 2009-03-13
> **0ra1suicid3 said:**
> i am, my internal hd is broken and soon will go to apple store
i am booting from external, people say it possible and other say itnot, but i think it is and i realky eant to have linux
See the FAQ. You cannot simply boot from an external drive, you have to use an EFI loader.

---

### Post by 0ra1suicid3 on 2009-03-13
what about grub?

i tryed with efi loader, but that what gave me the error

---

### Post by 0ra1suicid3 on 2009-03-13
i also trying to work fedora core 10, since theres no forum on the fedora website

---

### Post by cyberdork33 on 2009-03-13
> **0ra1suicid3 said:**
> what about grub?

i tryed with efi loader, but that what gave me the error
Yes, Grub-EFI is what I am talking about. You used rEFIt not an EFI bootlaoder. Please read the FAQ. It has a topic specifically addressing this.

---


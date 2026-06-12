---
title: "Feisty unable to mount NTFS usb drive"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by k8fox1 on 2008-03-19
I am running Feisty and trying to read/write to a USB NTFS drive. When I plug in the drive a window opens displaying the drives contents and all appears ok. That is until I attempt to drag a file. I am greeted with a system warning saying that I do not have permission to write to the drive. How can I fix this? I had loaded the NTFS configuration tool but this hasn't helped. The drive appears to be mounted as un-mounting it is an option.

Ideas??:confused: 

Thanks!

---

### Post by wormser on 2008-03-19
Try installing ntfs-config.

```
sudo apt-get install ntfs-config
```

Applications> Sytem Tools> NTFS Configuration Tool> Enable write support for external device.

---

### Post by k8fox1 on 2008-03-19
Thanks but I don't believe it allows me to make that selection. I'll take another look in the morning.

---

### Post by wormser on 2008-03-19
> **k8fox1 said:**
> Thanks but I don't believe it allows me to make that selection. I'll take another look in the morning.

Its there.

---

### Post by k8fox1 on 2008-03-19
OK thanks!! I'll let you know what I find tomorrow.

Thanks again!

---

### Post by Ginger Towel on 2008-03-19
i had an issue like this a while back and it sounds like you have a permision error not a mounting issue try entering:

```

Sudo nautilus

```

open that then navigate to the usb drive and try the drag again.

---

### Post by k8fox1 on 2008-03-19
Thanks i'll give it a try in the morning.

-Mike

---

### Post by k8fox1 on 2008-03-20
Wormser- it was the selecting of the "write to external hard drive check box. 

Thanks to all!!

:)

---


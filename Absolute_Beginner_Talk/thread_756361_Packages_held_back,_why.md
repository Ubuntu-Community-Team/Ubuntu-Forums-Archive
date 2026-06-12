---
title: "Packages held back, why?"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by iClouseau88 on 2008-04-15
Hi,

Lately I have been updating Hardy Heron Beta. Most of the time the process runs smoothly.  However there are quite a few packages that are not installed because either  they are being held back or automatically kept back.  For example:

1)_** Packages being held back**_:

grub, initramfs-tools, linux generic, linux headers generic, udev, vlc and xserver-xorg.

2) _**Packages automatically held back**_:

linux-image-generic, linux restricted modules generic, vlc-nox and xserver-xorg-video-amd

Could you tell me why and what should I do to get them installed?

Thanks a lot for your help.

---

### Post by Inxsible on 2008-04-15
They are held back because the installation requires a higher version of some dependent libraries which are not installed on your machine. Wait a few days and you should have the latest.

Since its Hardy which is in beta, you might see issues like these where not all dependencies are met.

---

### Post by iClouseau88 on 2008-04-15
Thanks for your quick reply.  This is what I had suspected.

---

### Post by bodhi.zazen on 2008-04-15
You can try to resolve this with :

```
sudo apt-get dist-upgrade
```

---


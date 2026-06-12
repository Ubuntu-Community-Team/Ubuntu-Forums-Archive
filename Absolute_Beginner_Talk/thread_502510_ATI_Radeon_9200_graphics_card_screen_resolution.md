---
title: "ATI Radeon 9200 graphics card screen resolution"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by zapyourit on 2007-07-16
Hello all.

I just recently installed Ubuntu. I am basically a noob in the Linux world currently.

I'm running an ATI Radeon 9200 graphics card on a Vaio desktop from a few years ago (3.0 GHz with 512 Ram). Currently, my screen resolution is running at 1024x768 where i was running 1280x1024 in Windows XP Home. I installed fglrx to see if that helped (it seemed to be the only thing that I found on the forums which made sense to try). However, the resolution is still set at the aforementioned point. Is there any advice anybody can give me to get back to my 1280x1024 resolution?

Thanks very much.

---

### Post by wolfen69 on 2007-07-16
in terminal, type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Motoxrdude on 2007-07-16
> **wolfen69 said:**
> in terminal, type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Accept the defaults except use the "fglrx" and when it asks you for your screen resolution.

---

### Post by jasonlfunk on 2007-07-16
If that doesn't work, post the contents of your /etc/X11/xorg.conf file as well as the make and model of your monitor.

---

### Post by AR_Kozz on 2007-08-17
In case you haven't figured this out yet, DON"T use fglrx. The update included with Feisty will use a version of fglrx that no longer supports the Radeon 9200. I have beat my head on this issue to no avail. In Dapper it worked, but I've no access to the older driver.

  use the "ati" driver. Even though it stinks

---


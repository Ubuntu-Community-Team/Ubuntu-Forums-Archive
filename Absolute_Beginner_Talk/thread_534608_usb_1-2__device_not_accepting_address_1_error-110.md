---
title: "usb 1-2 : device not accepting address 1: error-110"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by context45 on 2007-08-25
Hi,

 Needless to say , that ubuntu is by far the best linux version I had seen, with no configuration what so ever, got everything working , but the only issue  is it could not detect my additional USB harddrive. whenever the OS is booting, I get the error-110
"usb 1-2 : device not accepting address 1: error-110 "

intially my USB portable hardrive did got recognized, & I also downloaded some wallpapers to check the privileges & other stuff. But after 8 reboots, I got this message & the OS wouldn;t even recognize the hardrive. USB hardrive is in NTFS format. could anyone point me out on how to get  the hardrive recognized..?

Thanks,:)

---

### Post by meindian523 on 2007-08-25
I dunno whether the problem is with NTFS or the USB,but a newbie approach to the problem would say:

Try reinstalling ntfs-config to enable access to NTFS drives.

```
sudo apt-get reinstall ntfs-config
```

if you already have downloaded it,else

```
sudo apt-get install ntfs-config
```

If these don't work,try plugging the USB into some other USB port.Of course,it's your choice if you want to wait some more experienced guys/gals to help you out.:)

---


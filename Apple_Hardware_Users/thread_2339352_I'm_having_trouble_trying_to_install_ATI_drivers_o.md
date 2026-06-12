---
title: "I'm having trouble trying to install ATI drivers on my Mid 2007 iMac + wifi"
date: 2016-10-07
forum: Apple Hardware Users
---

### Post by johncena1 on 2016-10-07
I have looked over guides on the internet many many times and I can't seem to get this working no matter what I try to do.  I have manged to install Ubuntu on the iMac, but can only get it to work by setting the "nomodeset" option on the GRUB menu, which is really annoying having to do that all the time so I want to install the driver.  I have downloaded what I think is the correct driver on the AMD website, but when I double click on the file after downloading it, it opens up a text editor which isn't what it's supposed to do.  I don't know how to get it working properly.

I also don't know where to start on installing the WiFi drivers on this thing.

---

### Post by DuckHook on 2016-10-08
I know nothing about Apple HW, so am assuming that your machine runs an ATI chipset based on your title. Please provide version of Ubuntu you are running (14.04? 16.04).

To avoid having to add nomodeset at every boot, you add it to grub:```
sudo nano /etc/default/grub
```…find the line that says "quiet splash" and change it so that it now reads```
"quiet splash nomodeset
```…save file and exit nano with <Ctrl>+o <Ctrl>+x. Then update grub:```
sudo update-grub
```The next time you reboot, grub will automatically load nomodeset.

Hopefully, an Apple user can respond to your issue. My complete ignorance of their HW severely limits the help I can give you.

---


---
title: "[SOLVED] err: booting Ubuntu from usb pendrive"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by tango_ninja on 2008-04-13
I'm trying to load Ubuntu onto my 1Gb Kingston usb key...

I did everything as spelled out here:  [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

now when booting from USB i have an entirely black screen with 'GRUB' and a flashing underscore in the upper left-hand corner.

Nothing happens after this....any suggestions?

---

### Post by TJCIB on 2008-04-13
I used that same how-to first time and it didn't work also.

I then found [http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2) and it showed me what we going on in a little more detail and I was able to figure it out.  Works fine now.

for me, the edit for the syslinux.cfg file didn't come out right, so I manually edited it to match and it worked.

It took me three tries, but I finally got it.

---

### Post by tango_ninja on 2008-04-13
OK I figured it out..... well, I think I figured it out - either way its working now :)

for those interested, the problem was with stps 14/15 of the install process....
```
apt-get install syslinux mtools
syslinux -sf /dev/sd*x*1
```

syslinux with option **-s** is the safe,stupid mode. i simple got rid of the f, making the code:
```
syslinux -s /dev/sd*x*1
```

---


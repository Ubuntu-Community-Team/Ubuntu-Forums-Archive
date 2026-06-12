---
title: "[SOLVED] Can't seem to edit: /etc/init.d/mountdevsubfs.sh"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Steve Angelidis on 2008-04-08
I'm trying to activate USB recognition in VirtualBox on Gutsy. The Ubuntu Documentation says:

      In Gutsy one must uncomment this section:

/etc/init.d/mountdevsubfs.sh

    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

I navigate to the file and use edit to remove the 4 # symbols starting at the mkdir line. Everything appears to go fine, but when I try to save, I'm told that I don't have permission.

What am I doing wrong?

Please, if you can help, keep it as step by step as possible as I'm a total newbie.

Thanks.

SteveA

---

### Post by scragar on 2008-04-08
```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```
will let you edit the file with permtitions.

---

### Post by Steve Angelidis on 2008-04-08
Thank you so much, Scragar.

Worked like a charm.

---


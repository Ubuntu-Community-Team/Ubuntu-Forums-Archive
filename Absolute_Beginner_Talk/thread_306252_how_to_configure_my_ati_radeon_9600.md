---
title: "how to configure my ati radeon 9600?"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Micah Nungesser on 2006-11-24
Hello i just installed Ubuntu and i can't get my radeon to work properly.
when i run the 3d test(glxinfo | grep rendering) it says...
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No

```

i have reconfigured to use the fglrx driver and i have also installed the XFree86-DRI Driver and it still won't work.

also the monitor im using right now is a generic dell monitor(just in case it matters) but once i get back home(im at a friends house) i will be using a NEC.

please help,

Micah.

---

### Post by kd_pease on 2006-11-24
Try [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

Particularly the bit about editing /etc/X11/xorg.conf. That part made DRI work for me.

---

### Post by CowzRule on 2006-11-24
> Hello i just installed Ubuntu...What version? Dapper 6.06 or Edgy 6.10 or ...?> i have reconfigured to use the fglrx driver...How did you do this? Did you follow a How-To or Guide? If so , post the webpage address.> the monitor im using right now is a generic dell monitor(just in case it matters) but once i get back home(im at a friends house) i will be using a NEC.The NEC monitor should work fine, however, if you installed Ubuntu using the Dell monitor, you should reconfigure xorg.conf for the NEC so that the proper resolutions and refresh rates are set up.
Also, paste a copy of your "xorg.conf" file. That along with the other info I asked you for will help us to figure out what we need to do to get your card up and running correctly.

In case you need to know, to view your xorg.conf file, in the terminal type```
gedit /etc/X11/xorg.conf
```

---

### Post by Micah Nungesser on 2006-11-24
i haven't been able to try the site yet but...

im useing edgy.

i didnt follow a guid or anything to configure the driver. i just looked in the documentary(for ubuntu) and it said to leave most of the things at default so thats what i did.

ill try and mess with it later i g2g thanks for the help,

Micah.

---


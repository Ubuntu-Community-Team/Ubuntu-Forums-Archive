---
title: "Mouseemu / uinput"
date: 2007-06-18
forum: Apple Intel Users
---

### Post by AWerner32 on 2007-06-18
I used to have mouseemu installed on my first gen macbook to block the trackpad while typing. I need that feature because of the way i type however i can no longer use mouseemu i am given the error > No uinput device found! Make sure the uinput module is loaded
or CONFIG_INPUT_UINPUT is compiled into the kernel.


any ideas would be great,

Thanks always

---

### Post by dve on 2007-07-22
HI,

I have a similar problem (different program though).  Do you have the "file" /dev/input/uinput? Ubuntu (at least my 2.6.20-16) has uinput device compiled as module and you need to install it. A start is to say:

```
sudo modprobe uinput
```

This should make the uinput device. My question is: How do I probe this automatically at startup? There should be some list of modules to load, but where?

Juha

---

### Post by jdfreshwater on 2007-10-15
Try these instructions found for adding WMD.  I had used this before and it should help.

> Make sure that the uinput module is loaded on system startup and your mythtv user has read access to the created device /dev/input/uinput. I added the following lines to /etc/rc.local

 modprobe uinput
 chmod a+r /dev/input/uinput

found at

[http://www.mythtv.org/wiki/index.php/Controlling_MythTV_using_a_Wii_remote]("http://www.mythtv.org/wiki/index.php/Controlling_MythTV_using_a_Wii_remote")

hope this helps.

---


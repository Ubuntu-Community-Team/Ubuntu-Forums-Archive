---
title: "How to create an Open Indiana live pendrive in linux?"
date: 2012-06-25
forum: Any Other OS
---

### Post by Marcelo Ruiz on 2012-06-25
Hi All!

I would like to know if anyone tried to create an Open Indiana live pen drive in Linux.
I tried to follow the instructions posted here [http://wiki.openindiana.org/oi/Installing+OpenIndiana]("http://wiki.openindiana.org/oi/Installing+OpenIndiana") but I could not make it work.
I tried to install the image into a 1 GB pen drive following their instruccions: 

To create a live USB on any Unix-like system (including Mac OS X), download the standard live USB and the 1G.header file and run the following commands:
```

cat 1G.header <USB image file> | dd bs=1024k of=<path to raw USB storage device>

```

where <USB image file> is oi-dev-151a-x86.usb and <path to raw USB storage device> in my case is /dev/sdc. So after inserting a not partitioned 1GB pen drive to my computer, I cd into my Download folder and type is the following:

```

cat 1G.header oi-dev-151a-x86.usb | dd bs=1024k of=/dev/sdc

```

The command goes well with no errors, but after rebooting I just get to a grub prompt.
Their website is quite poor explaining what to do or how to solve this problem (they just say something went wrong), so I am giving the great Ubuntu Community a shot!
Thanks!

---

### Post by sffvba[e0rt on 2012-06-25
*Thread moved to **Other OS/Distro Talk**.*


404

---

### Post by Marcelo Ruiz on 2012-07-05
Hmm... I guess I'm the only crazy one who wants to give OpenIndiana a try... :lolflag:

---


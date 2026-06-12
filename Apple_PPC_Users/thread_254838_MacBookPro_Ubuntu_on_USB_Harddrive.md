---
title: "MacBookPro: Ubuntu on USB Harddrive"
date: 2006-09-10
forum: Apple PPC Users
---

### Post by schdeffan on 2006-09-10
Hi,

I'm struggeling at installing Dapper on an external USB HD with my MacBook Pro. 

I installed rEFIt on the Book and then Ubuntu on the USB Drive using the alternate install CD. I aborted the installation when it fails at installing ELILO. I then installed LILO from the CD and updated initrd.img to support USB drives.

Now I can choose the HD in rEFIt and LILO shows up, but when I attempt to boot Linux all I get is

LILO booting Ubuntu......................... (this takes ages and it is accessing the USB drive regularily)

Then after some time there is an error message (among lots of messages) saying something like

Specify root= option 


LILO seems to be unable to find the vmlinuz image to boot the kernel.

Here's my lilo.conf

```

boot=/dev/sdb
prompt
timeout=200
delay=10
read-only

image=/vmlinuz initrd=/initrd.img
    root=/dev/sdb1
    label=Ubuntu

```

I installed lilo using

lilo -b /dev/sdb

I think I'm close to boot Ubuntu but something seems to be wrong with my LILO config. 

Can anyone point to what I need to do in order to get this working? That'd be very much appreciated.

Stephan

---


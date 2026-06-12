---
title: "Not recognising iPod"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by jontes on 2008-01-20
hi

when i connect my iPod to my computer the first time i did it it worked perfectley the icon came up on the desktop and it says do not disconnect on the ipod screen.

but the second time i tried it it only says do not disconnect on the screen of the iPod and the computer is not recognising it. how do i make the computer recognise it and how do i unmount it without the iPod being recognised and pulling it out. It freezes my ipods screen.

thnx

---

### Post by infurnus on 2008-01-29
I had a problem with my iPod and my usb hub it would only let me transfer files < 500Mb and random disconnection. So plugging directly into the port on the back of the pc resolved this issue. Otherwise to find out what your device name is run:

```

dmesg

```

look for sdx (i.e. sda:sdb:sdc etc)

to mount

```

mkdir /media/ipod
mount /dev/sdx1 /media/ipod

```

to unmount 

```

sudo umount /dev/sdx

```

---


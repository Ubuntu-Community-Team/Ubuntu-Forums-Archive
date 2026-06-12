---
title: "Mouse not detected"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by takeuaway on 2007-05-12
Hi, i just installed Ubuntu feisty fawn on my laptop. However, my usb mouse is not detected, same goes to my usb external hard drive. How do i check whether usb is working, and how do i make it working. Does ubuntu allows plug n play?

Thanks a lot!

---

### Post by Billy McCann on 2007-05-12
In a terminal, type: lsusb.  

Applications > Accessories > Terminal

```
lsusb
```

See if your devices show up.

---

### Post by SoggyCornflake on 2007-05-12
> **takeuaway said:**
> Hi, i just installed Ubuntu feisty fawn on my laptop. However, my usb mouse is not detected, same goes to my usb external hard drive. How do i check whether usb is working, and how do i make it working. Does ubuntu allows plug n play?

Thanks a lot!

Ubuntu does plug and play fairly well in my opinion, but then if my mouse didn't work, I might have a different view.

From a command prompt you can type ```
lsusb
```  It will let you know what your kernel sees as usb.  For example this is what I had.```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

From this you can see that I didn't  have anything plugged into my usb ports.

 Then I plugged in my USB hard drive and did the same thing:

```
Bus 004 Device 010: ID 1058:0901 Western Digital Technologies, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

If your computer recognized your mouse, it would show it in the listing.

From my experience, whenever an external hard drive is plugged in, I get a popup dialog box asking me if I what to open it.

---

### Post by SoggyCornflake on 2007-05-12
> **takeuaway said:**
> Hi, i just installed Ubuntu feisty fawn on my laptop. However, my usb mouse is not detected, same goes to my usb external hard drive. How do i check whether usb is working, and how do i make it working. Does ubuntu allows plug n play?

Thanks a lot!

Another thought:  Laptops are not as standard as PCs, so sometimes things like usb controllers can be quite customized. 
You may want to check [http://www.linux-laptop.net/]("http://www.linux-laptop.net/") to see if others have had the same problems, and how they overcame them

---

### Post by takeuaway on 2007-05-12
Hi, thanks a lot. Somehow, the auto detection just worked after i restarted linux. Maybe the first time i install didnt update the OS. Thanks again :)

---


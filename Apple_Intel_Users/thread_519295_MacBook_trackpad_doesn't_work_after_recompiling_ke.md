---
title: "MacBook trackpad doesn't work after recompiling kernel"
date: 2007-08-06
forum: Apple Intel Users
---

### Post by garyozzy on 2007-08-06
I followed this guide: [http://ubuntuforums.org/showthread.php?t=442941](http://ubuntuforums.org/showthread.php?t=442941)

and after restarting, my trackpad doesn't work. does anyone know what happened/how to fix without a trackpad?

thanks, gary

---

### Post by benanzo on 2007-08-06
In a terminal do:
```
sudo modprobe appletouch
```

If you get any errors you probably didn't enable it in your kernel .config before you compiled.

---

### Post by garyozzy on 2007-08-07
that doesn't work. does that mean i need to recompile the kernel again?

---

### Post by cyberdork33 on 2007-08-07
> **garyozzy said:**
> that doesn't work. does that mean i need to recompile the kernel again?

It would help if you gave the error messages (if any) or at least stated what DID happen, as "that doesn't work" can mean lots of things.

Also, you could try plugging a USB mouse in and see if that works. that would limit the possibilities.

Also, look at this, in the Trackpad / Touchpad Section:
[http://www.jasonparekh.com/?page_id=9](http://www.jasonparekh.com/?page_id=9)

---

### Post by garyozzy on 2007-08-11
i have recompiled multiple times since to no avail. plugging in a usb mouse does work. i have used multiple different configs via xconfig. now wireless and sound and ethernet don't work and they used to. vanilla kernel worked better than after compiling acc. to guide

---

### Post by cyberdork33 on 2007-08-11
my guess is that your custom kernel does not include some hardware drivers that you need.

---

### Post by garyozzy on 2007-08-11
then what do i need and why did those things work with the vanilla kernel?

---

### Post by cyberdork33 on 2007-08-11
> **garyozzy said:**
> then what do i need and why did those things work with the vanilla kernel?

I have no idea what your configs are. Why don't use just use the basic ubuntu kernel. There is nothing wrong with that and should work just fine for you.

---

### Post by ryanwsmith on 2007-12-31
I'm having this same problem, was this problem ever resolved?

---


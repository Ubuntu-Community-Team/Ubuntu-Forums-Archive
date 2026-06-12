---
title: "Ubuntu on a usb harddrive for a macbook"
date: 2008-05-27
forum: Apple Hardware Users
---

### Post by cyanide2 on 2008-05-27
I have a friend, who I'll call "E." E has a macbook, and a 80 gig external harddrive. He wants to install ubuntu on his external harddrive and boot from it on his macbook. How might he go about doing this? I have never owned a mac, so I don't know much about how this might be done. Will the default GrUB install (on the external drive) work on a mac (I've heard something about mac's using a non-BIOS firmware).

---

### Post by EXCiD3 on 2008-05-27
I think this tutorial should be just what you are looking for :) [http://ubuntuforums.org/showthread.php?t=761817](http://ubuntuforums.org/showthread.php?t=761817)

---

### Post by cyberdork33 on 2008-05-27
although the install will go fine, you will likely not be able to boot from the USB drive. This is due to a problem with Apple's firmware. see the FAQ for more information.

---

### Post by cyanide2 on 2008-05-27
> **cyberdork33 said:**
> although the install will go fine, you will likely not be able to boot from the USB drive. This is due to a problem with Apple's firmware. see the FAQ for more information.

Firstly, which FAQ?

Secondly, how might you go about booting it? If the Ubuntu install cd boots, why wouldn't the external harddrive? Don't they both rely on BIOS functions not available on a macintosh?

---

### Post by issih on 2008-05-27
This thread is very long, but covers a lot of the problems:

[http://ubuntuforums.org/showthread.php?t=510030](http://ubuntuforums.org/showthread.php?t=510030)

In essence the apple firmware does not like booting from a usb device. Full Stop, end of. It depends on the model you have, the older ppc machines seem to be capable of it, and even some of the earlier intel machines running core duo processors, but generally the newer core 2 duo machines just will not play in terms of booting from a usb flash/hard drive.

To cover some of your other queries, The general procedure for booting from something other than the main mac harddrive, is to hold down the alt key during boot up, this will then present an option screen (this is how to boot from cd) Alternatively look at installing rEFIt which provides more extensive options at boot time.

If you are determined to run ubuntu from a usb drive on a mac, it is achievable, but until apple provides a new firmware (don't hold your breath) you have to look at jump starting things with a boot cd. This is a cd containing a boot loader and a copy of the linux kernel. The machine is then booted from the cd drive, and the boot loader is used to lauch the linux kernel on the cd, and then redirect the rest of the boot procedure to point to the usb drive.

This does work, I have done it on this machine in fact, but it is a pain to achieve, and you will have to create a new boot cd every time you upgrade the kernel. If you are really determined, look into boot cd's, if you get utterly lost give me a shout

Good luck

---

### Post by cyberdork33 on 2008-05-27
> **cyanide2 said:**
> Firstly, which FAQ?
The FAQ stickied at the top of the Apple Users forum.

issih pretty much covered the whole of it though.

---

### Post by cyanide2 on 2008-05-28
Can a "normal" bootloader (like GrUB) be used on the USB drive (provided it boots, likely through rEFIt)?

---

### Post by cyberdork33 on 2008-05-28
> **cyanide2 said:**
> Can a "normal" bootloader (like GrUB) be used on the USB drive (provided it boots, likely through rEFIt)?
yes, but that doesn't seem to make it work either. I know that thread is huge, but I pretty sure some people have tried that before. We tried ALOT of stuff. Seems the only thing that works is to create a /boot partition only on the internal or create a boot cd to start from the external drive.

---


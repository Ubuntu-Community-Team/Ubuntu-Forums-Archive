---
title: "Mac Mini and MBR only - keyboard not working in GRUB"
date: 2010-06-14
forum: Apple Hardware Users
---

### Post by bigmamab on 2010-06-14
I set up my Mac Mini to dual boot Windows 7 and Ubuntu. I started with Windows only, and allowed it to rewrite the partition table (GPT/MBR). When I tried to install Ubuntu, it didn't see Windows until I used Gdisk to delete the GPT portion. Then it recognized the Windows partition and installed Ubuntu as per normal. 

Now when I boot, I get GRUB and the option to boot Ubuntu or Windows 7. The only problem is that the USB keyboard (Aluminum or standard PC keyboard) doesn't work until an OS is loaded.

Is this an EFI problem? I'm starting to think that EFI is required for USB keyboard support at bootup since it replaces the BIOS functionality. Is this even remotely accurate? Did I mess things up by not going the rEFIt route? 
I'm not sure what I can do at this juncture as I can only boot into Ubuntu.

I *could* install OS X, rEFIt, then Windows and Ubuntu, keeping rEFIt as the boot loader, but if there's an easy solution I'd like to avoid that. More importantly, I'd like to understand what's going on.

Thanks very much!

---

### Post by lewisskinner on 2010-06-14
It's not just a mac issue.  I have the same problem on my PC with Vista and Ubuntu 10.4.  It happened after an update I believe.

---

### Post by lewisskinner on 2010-06-15
any help anyone?

I can't even find my menu.lst file to alter the boot order so my girlfriend can get into Vista.

---

### Post by lewisskinner on 2010-06-16
bump

help please?

---


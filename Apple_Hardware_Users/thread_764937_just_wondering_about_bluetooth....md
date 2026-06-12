---
title: "just wondering about bluetooth..."
date: 2008-04-24
forum: Apple Hardware Users
---

### Post by turcott on 2008-04-24
hey there, just wondering if the bluetooth is activated or on, for example bluetooth in ubuntu 7.10 on my macbook is started on default, i know you can change that.  My question is, wouldn't leaving bluetooth on make you more vulnerable, isn't it possible for someone to connect to the bluetooth device in the macbook and take control, or use it like leaching a wireless network connection?

Anyone ever tried changing the ubuntu source code so that it will recoginize EFI on bootup, that way the white screend delay would be fixed....or has the new version 8.04 corrected this issue?

In order to alter the OS, do you first need to download the kernel, and compiler, before you can change/fix hardware, or OS issues?  Or could i do that now using the ubuntu terminal?

---

### Post by cyberdork33 on 2008-04-24
> **turcott said:**
> hey there, just wondering if the bluetooth is activated or on, for example bluetooth in ubuntu 7.10 on my macbook is started on default, i know you can change that.  My question is, wouldn't leaving bluetooth on make you more vulnerable, isn't it possible for someone to connect to the bluetooth device in the macbook and take control, or use it like leaching a wireless network connection? You can control your bluetooth stuff from the bluetooth applet near the clock.

> **turcott said:**
>  Anyone ever tried changing the ubuntu source code so that it will recoginize EFI on bootup, that way the white screend delay would be fixed....or has the new version 8.04 corrected this issue?You have it backwards. This is not a problem with Ubuntu detecting EFI, it is a problem with the Apple EFI detecting Ubuntu (or any "legacy OS"). The best option would be to use an EFI bootloader to load linux, but that is probably still a long way off.

---

### Post by hellmitre on 2008-04-24
In response to your query about the boot loader, I'd try installing rEFIt in Mac OS X, which is what your computer automatically (by default) wants to boot from. It should give you the option to boot off any bootable drives or partitions connected to your computer at boot.

---

### Post by slacka-vt on 2008-04-24
> My question is, wouldn't leaving bluetooth on make you more vulnerable, isn't it possible for someone to connect to the bluetooth device in the macbook and take control, or use it like leaching a wireless network connection?


1. Bluetooth requires an  encryption key in order for a new device to make a connection.

2. Bluetooth connections are only capable to a maximum of 12 ft (4 meter) to 33 ft (10 meter) range so you *should* have a clear view of the perpetrator and can smack them over the head thusly.

~s

---

### Post by turcott on 2008-04-24
hahahah, ya i could see myself doing that if the perpetrator was in my sight, lol...oh and i can't install rEFIt in Mac OS X, cause it came formatted with no disks, (bought at pawn shop).  Can i install something similar in ubuntu since it's already installed?

---

### Post by cyberdork33 on 2008-04-25
> **turcott said:**
> hahahah, ya i could see myself doing that if the perpetrator was in my sight, lol...oh and i can't install rEFIt in Mac OS X, cause it came formatted with no disks, (bought at pawn shop).  Can i install something similar in ubuntu since it's already installed?
You could install rEFIt if there was a linux equivalent of the OSX command 'bless' but there is not.

---

### Post by russo.mic on 2008-04-27
CD,  correct me if i'm wrong, but for a bit there they had compiling instructions for rEFIt under linux, and it included bless...is that no more?  or was it never and i'm just dreaming that up...

Russo

---

### Post by cyberdork33 on 2008-04-27
> **russo.mic said:**
> CD,  correct me if i'm wrong, but for a bit there they had compiling instructions for rEFIt under linux, and it included bless...is that no more?  or was it never and i'm just dreaming that up...

RussoIf there is, i have never seen it. Would be awesome for those without OSX at all though if it could be done.

---


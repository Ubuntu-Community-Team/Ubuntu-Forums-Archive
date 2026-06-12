---
title: "Unistalling Ubuntu"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by NCAANFI on 2007-06-14
Ok it's just too tough for me to configure hardware. Everything else is fine and is lovely but too much stuff is too hard to configure (can't get 1366x768 resoluton, can't config wireless internet, can't get HDTV card to work). I just don't understand what I'm doing or what the commands are doing.  I've tried using gparted but I can't get rid of the data on the MBR. Any help?

---

### Post by HotShotDJ on 2007-06-14
You need to reinstall the Windows boot loader from your Windows CD.   The command in Windows console is ```
fdisk /mbr
```

---

### Post by NCAANFI on 2007-06-14
> **HotShotDJ said:**
> You need to reinstall the Windows boot loader from your Windows CD.   The command in Windows console is ```
fdisk /mbr
```

I only have Ubuntu on it, I'm still weighing up whether to go Vista or stick with XP. I haven't had a desktop in years and the only XP I have is what's on my laptop

---

### Post by seshomaru samma on 2007-06-14
It's probably best for you to run a dual boot
You can set a new patition for Windows with gparted and when you install Windows it will overwrite the MBR

If you are already dualbooting and want to get rid of Ubuntu completely ,the fixmbr is the way to go
However if you are dualbooting - why don't you give Ubuntu some more time. Whenever you have some time ,boot back in Ubuntu and try to fix some stuff ,when you get tired or frustrated boot back to Windows....

---

### Post by HotShotDJ on 2007-06-14
When you install Windows, it will install what it needs.  Don't worry about it.

---

### Post by NCAANFI on 2007-06-14
> **seshomaru samma said:**
> It's probably best for you to run a dual boot
You can set a new patition for Windows with gparted and when you install Windows it will overwrite the MBR

If you are already dualbooting and want to get rid of Ubuntu completely ,the fixmbr is the way to go
However if you are dualbooting - why don't you give Ubuntu some more time. Whenever you have some time ,boot back in Ubuntu and try to fix some stuff ,when you get tired or frustrated boot back to Windows....

Yeah that's a thought. Is it possible to install it on a USB drive? I have an 80 gig SATA in an external case I use for storage ATM. Right now there a whole list of text commands that I'm not familiar with (I don't know what they are and I don't know what they do, I find I need to know why more than how) and am extremely frustrated because I can't get the PC running properly and there's a whole heap of gear I plan on buying that hasn't had all the driver bugs ironed out.

---

### Post by domat00 on 2007-06-14
> **NCAANFI said:**
> Yeah that's a thought. Is it possible to install it on a USB drive? I have an 80 gig SATA in an external case I use for storage ATM. Right now there a whole list of text commands that I'm not familiar with (I don't know what they are and I don't know what they do, I find I need to know why more than how) and am extremely frustrated because I can't get the PC running properly and there's a whole heap of gear I plan on buying that hasn't had all the driver bugs ironed out.

[http://linuxcommand.org]("http://linuxcommand.org")

---


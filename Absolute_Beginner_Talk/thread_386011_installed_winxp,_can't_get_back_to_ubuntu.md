---
title: "installed winxp, can't get back to ubuntu"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by jexdawg13 on 2007-03-16
A few days ago, I messed up my ubuntu and completely trashed it so that I couldn't start it at all. I had a very small partition left so I decided to install WinXP on it so that I could get online and ask how to fix it. I installed windows and... got online and figured out how to fix it. Now, however, I have no idea how to start my Ubuntu OS on my main partition. When I start the computer, it just loads up winXP. I want to start Ubuntu instead.

Unfortunately, my ubuntu installation disc is scratched and I can't download a new one. In fact, I can't download anything - my winXP doesn't even have a C:/ drive - it barely had enough room to install XP. 

So what do I need to do to boot Ubuntu instead of Windows? This winXP right now is nearly useless since I can't download or install anything - thankfully my printer and internet are fairly plug-n-play with minimal tinkering, so that I could get online andget some work done. Henceforth, I'd really like to get back to my main OS soon so that I'm not stuck on this barely functioning machine.

Thanks for any help you provide. I'm going to need it.

---

### Post by Kobalt on 2007-03-16
You need to restore the Grub boot loader. Here is a guide on how to do that : [http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

---

### Post by Najand on 2007-03-16
Check Ubuntu Wiki Site for solving your problem:
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28recover%29]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28recover%29")

---

### Post by jexdawg13 on 2007-03-16
Both of those look great and they could potentially help me except for two problem:

I don't have a working Live CD... and I cannot download the Grub Super Disk app because I can't download anything.

:(

---

### Post by dstew on 2007-03-16
If you have access to a working linux system you can make a grub boot floppy. I think there is a way to make a grub boot floppy from windows, but I haven't been able to find a link yet.

---

### Post by dstew on 2007-03-16
Here is a link. If you are locked into Windows, you can burn a grub-bootable floppy with SuperGrub:

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

Get the floppy image file from the list of disk downloads.

You have to have an image writing program on your Windows os. A free one is RaWrite:

[http://www.chrysocome.net/rawwrite](http://www.chrysocome.net/rawwrite)

Use RaWrite to burn the .img file to a floppy (must be formatted first), then boot from the floppy.

---

### Post by mahy on 2007-03-16
If you don't have an Ubuntu Live CD, it's high time to get one...

Just my SKK 0.02

---


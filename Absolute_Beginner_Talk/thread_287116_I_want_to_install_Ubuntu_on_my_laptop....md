---
title: "I want to install Ubuntu on my laptop..."
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by MagickalHack on 2006-10-28
As the title says, I want to install Ubuntu on my laptop, but my graphics card isn't supported, it is an ATI Radeon Xpress 1100. Any thoughts on what to do? I'm new to the Linux community, and any help would be appreciated.

---

### Post by gn2 on 2006-10-28
A quick Google suggests maybe it can be made to work in Linux.

[http://www.mail-archive.com/arch@archlinux.org/msg08527.html](http://www.mail-archive.com/arch@archlinux.org/msg08527.html)

There may not be a driver from the manufacturer, but perhaps it can still be made to work.

---

### Post by MagickalHack on 2006-10-28
Will it work the same with this version of linux? 


As I said before, I'm new...

---

### Post by tedrogers on 2006-10-28
The link provided suggests that the problem lies with fglrx ATI driver, which provides 3D acceleration (with some tweaking!).

However, I would imagine that if you're not that bothered by 3d Accel, then you could use the inbuilt vesa (mesa?) driver which is kind of a universal 2D driver.

I see no reason why it shouldn't work. Have you tried the Live CD? You can just download the CD image from the Ubunutu website or via BitTorrent(preferred) and then burn it to CD. Then assuming your BIOS is set to boot from CDROM before the Hard Disk, you can just boot into Ubuntu and see how it fares.

Give it a go.

---

### Post by MagickalHack on 2006-10-28
I want to be able to play WoW, so I need 3d accel...

---

### Post by gn2 on 2006-10-28
You should give the Live CD a try, it won't install anything and is risk-free.

If your graphics card can be set-up in live session it can be set-up installed.

As for playing games that's another issue entirely but it's possible: [http://www.ubuntuforums.org/showthread.php?t=243336&highlight=wow](http://www.ubuntuforums.org/showthread.php?t=243336&highlight=wow)

You could always fit a new hard drive to try Ubuntu out with?

If it installs and runs OK then you can either put original one back in and install a dual-boot and put the new drive in a USB enclosure for additional storage and back-up.
Or put the original one in the USB enclosure wipe away Windows and just run Ubuntu single booted.

---

### Post by MagickalHack on 2006-10-29
The only thing on my system that doesn't seem to work properly is my video. 

What do you think about using Cedega rather than Wine to run WoW.
I ask because I was suggested to use Cedega[Cedega]("http://www.transgaming.com/index.php?module=ContentExpress&func=display&file=index&ceid=29") by a friend.

As for the option of buying a new HD, I'm lazy, and rather just do a full wipe/install... less hassle.

---

### Post by gn2 on 2006-10-29
> **MagickalHack said:**
> 
What do you think about using Cedega rather than Wine to run WoW.
I ask because I was suggested to use Cedega[Cedega]("http://www.transgaming.com/index.php?module=ContentExpress&func=display&file=index&ceid=29") by a friend.

Cedega costs money, Wine doesn't.

---

### Post by MagickalHack on 2006-10-29
Granted, I was just asking because a friend mentioned it would be a bit easier to work with, and as I said before, I'm fairly new to linux...

---

### Post by MagickalHack on 2006-10-29
Bump to save this from page 8.

---


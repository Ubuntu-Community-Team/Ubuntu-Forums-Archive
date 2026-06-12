---
title: "MacBook (nonpro!) and Ubuntu"
date: 2006-08-06
forum: Apple PPC Users
---

### Post by Breepee on 2006-08-06
I might be tempted into buying a MacBook, but my main concern is how I can run Ubuntu on it. I've read verious tutorials, but they all mention the use of Bootcamp, software that I would like to avoid if possible (it being timebombed and all, and I want a pure Linux option ;)). Now I heard Fedora can run directly on it, through Lilo and it's support for Intel EFI. Can this be done with Ubuntu too?

My second question is about the battery-life of Ubuntu on a MacBook. The main reason to go for it, is because of the great battery-life (4-5 hrs, but with OSX). Anyone experience with this?

---

### Post by fourchannel on 2006-08-06
Ok, first off...
I've had a powerbook G4 for about 2 years now, and the battery life is great on OSX. However I never got around to installing ubuntu on mine. I think the battery doesn't last quite as long but it is still good running time.

Second... Now that Apple has switched to Intel chips, I believe that you will need to get the installl cd for the x86 system and use it. [http://ubuntu.cs.utah.edu/releases/6.06/ubuntu-6.06-desktop-i386.iso](http://ubuntu.cs.utah.edu/releases/6.06/ubuntu-6.06-desktop-i386.iso) And from what I've read from these threads you just double click on the install icon and when it asks you how to carve up the partition, tell it "erase entire disk".

Do keep in mind that OSX will work better at somethings, *or did at one point in time*, including the fan speed control, wireless, WEP encryption. but for most everything else Ubuntu has it matched or beaten. That was with Ubuntu Breezy back in the day, I dunno know about Dapper.

These are the threads I looked at. Hope this is useful.

[http://ubuntuforums.org/showthread.php?t=218130](http://ubuntuforums.org/showthread.php?t=218130)
[http://www.ubuntuforums.org/showpost.php?p=1060679&postcount=22](http://www.ubuntuforums.org/showpost.php?p=1060679&postcount=22)
[http://bin-false.org/?p=17](http://bin-false.org/?p=17)
[http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453)

---

### Post by James_M on 2006-08-06
dapper works great for almost everything but I'd keep an OS X partition sitting there just in case.  You will need an x86 install CD (the regular one, I don't think the 64 bit is needed).  Hope that helps

---

### Post by chasisaac on 2006-08-07
> **Breepee said:**
> I might be tempted into buying a MacBook, but my main concern is how I can run Ubuntu on it. I've read verious tutorials, but they all mention the use of Bootcamp, software that I would like to avoid if possible (it being timebombed and all, and I want a pure Linux option ;)). Now I heard Fedora can run directly on it, through Lilo and it's support for Intel EFI. Can this be done with Ubuntu too?



I do not think the Bootcamp time bomb will affect anything. I do not know for sure. 

You would use LILO for booting. I think all that bootcamp does is make life easy to partion the hard drive. That way you do not have to reformat the drive. 

IF you want a full time 100% ubuntu that is easy to do and will work well.

---

### Post by Ebabylon on 2006-09-13
Try with Parallels Desktop, [http://www.parallels.com/en/products/workstation/mac/](http://www.parallels.com/en/products/workstation/mac/)
Work just fine for me. I have a Mac Book Pro, a brilliant and excellent piece of equipment, with Linux Ubuntu 6.06 and Windows xP Professional installed.

---

### Post by stmiller on 2006-09-13
In Linux you can specify how fast/slow you want your CPU to run, to the exact CPU clock speed. So you can make your battery last a LONG time. 

I have my iBook G4 (1Ghz) clock down to 533Mhz when on a battery or idle, and it lasts for quite a while. I'm not sure how long; I haven't tested it to see.

(OS X defaults this computer down to 800Mhz.)

---


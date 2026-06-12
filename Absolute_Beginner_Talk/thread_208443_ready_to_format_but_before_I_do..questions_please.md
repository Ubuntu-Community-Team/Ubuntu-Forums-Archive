---
title: "ready to format but before I do..questions please"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by leebrendalee on 2006-07-03
In my quest to find the perfect linux distro for me...I am pretty sure I'm screwed something up because for the life of me...I cannot get Ubuntu to recognize my ipaq pocket pc.  When I plug in my usb memory stick...no problem..works right away...but I need to be able to transfer stuff to and from my pocket pc...I haven't tried my printer or anything else until I get this working.....I'm sure its because I've messed something up during the install process...Has anyone gotten their ipaq pocket pc to work when the just plug it in??  If so..than I'll go and format and start from scratch..no biggie..will take an hour if that...better than the week or so I've spent trying to get this thing working....................

---

### Post by richbarna on 2006-07-03
[QUOTE=leebrendalee]In my quest to find the perfect linux distro for me...I am pretty sure I'm screwed something up because for the life of me...I cannot get Ubuntu to recognize my ipaq pocket pc.  When I plug in my usb memory stick...no problem..works right away...but I need to be able to transfer stuff to and from my pocket pc...I haven't tried my printer or anything else until I get this working.....I'm sure its because I've messed something up during the install process...Has anyone gotten their ipaq pocket pc to work when the just plug it in??  If so..than I'll go and format and start from scratch..no biggie..will take an hour if that...better than the week or so I've spent trying to get this thing working....................[/QUOTE]

Here's your answer :)
[http://www.ubuntuforums.org/showthread.php?t=30936]("http://www.ubuntuforums.org/showthread.php?t=30936")

---

### Post by leebrendalee on 2006-07-03
I forgot to say that Iv'e read everything.  Nothing ever says what if my hardware isnt' found.......nobody has ever asked this question.  I can't get by the first step because when I type dmesg it says:
it found new full speed device..that's it..after that..everything else in the thread makes no sense if my hardware isn't mounted...it's simply not loading the ipaq kernal as it says in this thread: mine doesn't say anything but the first line.,,.

 usb 4-2: new full speed USB device using uhci_hcd and address 3
ipaq 4-2:1.0: PocketPC PDA converter detected
usb 4-2: PocketPC PDA converter now attached to ttyUSB0

---

### Post by leebrendalee on 2006-07-03
yes I've found out it's simply not loading the ipaq driver...........does anyone know how to load the darn driver? gotta be something simple?

---

### Post by leebrendalee on 2006-07-03
As usual, I come up with brick walls like this:  It says what's wrong but doesn't suggest what to do about it?  does this mean I can't use ubuntu because my ipaq doesn't work with it?

Class, subclass and protocol

Does your USB device presents itself like this? Compare the parts marked with red color.

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  9 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ef(unk. ) Sub=01 Prot=01 MxPS=16 #Cfgs=  1
P:  Vendor=0bb4 ProdID=0b01 Rev= 0.00
S:  Manufacturer=MSFT
S:  Product=PocketPC USB Sync
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=ef(unk. ) Sub=01 Prot=01 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=1ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=03(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

If your device matches the above it does not work with SynCE or the ipaq kernel driver and will most likely crash your kernel when you run ''synce-serial-start''. See bug report 1332550. You are very welcome to amend your experiences to the bug report!

---


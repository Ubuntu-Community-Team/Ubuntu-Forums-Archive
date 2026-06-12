---
title: "cant co nnect to the net"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by bash the bishop on 2006-05-04
i have just install dapper and now i'm having trouble connecting to the net. i am using tiscali for my isp. i have a usb modem which in xp works fine, but i cant seem to get anywhere with ubuntu. where can i put in my logon details? where can i check that ubuntu can see my modem? 
here's hoping

---

### Post by cgjones on 2006-05-04
If you have a cable modem connected to your computer, you might want to see if you can use an ethernet cable in place of the usb cable. My cable modem, a Motorola Surfboard, can use either. I'm not saying it won't work in Ubuntu using the usb cable, but switching to an ethernet cable might make things easier.

---

### Post by swampy81 on 2006-05-04
I second the motion to go with a network cable (ethernet), whatever you want to call it, in place of the USB, if thats an option.  That will at least remove a large question mark in terms of troubleshooting.  From there, make sure you are set to use DHCP.

Go to system > administration >networking > ethernet connection> configuration

If you have to go with USB then I dont think I can help you at the moment, as I usaully rely on USB in linux to automagically work :)

---

### Post by steve.horsley on 2006-05-04
IUf you can find the exact model of the modem, search the forums for that model name/number. You are bound to find other threads discussing it. 

I always recommend an external router+ethernet switch for ADSL, but look for threads on your modem model first.

---

### Post by ZiLOG_Z80 on 2006-05-04
I had the same problem in Breezy but have not tried Dapper. If you are using the Sagem Fast800 modem supplied by Tiscali the solution may be the same and you would need the driver from

[http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230](http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230)

It needs to be compiled from source and in Breezy required a few packages not installed by default and a couple downloaded from the packages pages and then manually installed in Ubuntu from the comand line using *dpkg -i*.

Unfortunately I cant remember the exact steps, I think the packages needed from synaptic were, build essential and the headers for the kernel. From the packages pages you needed gcc3.4, gcc3.4-base and cpp3.4 as thats what was used to compile the kernel.

Sorry I couldnt give exact instructions, if you give it a go and have problems just ask and I'll try to help.

---

### Post by richbarna on 2006-05-04
Get a router, USB modems suck big style.
Routers areb easy peasy to configure from their web interface.

---

### Post by bash the bishop on 2006-05-07
All seems a bit of an effort. I shouldn't have to get a new router when the USB modem works fine, and I'm a bit concerned about applying firmware updates incase it knackers it for XP. I know I'm only new to Ubuntu, but having to manually download and install stuff in terminal and mess about with all this seems a little complicated. 
Is there not a more simple driver DB to download??
:confused:

---

### Post by Blondie on 2006-05-07
Hi,

Check to see if your modem is on this list as supported,
[http://eciadsl.flashtux.org/modems.php](http://eciadsl.flashtux.org/modems.php)

If it is listed as supported there then check out my reply to this guy and see if it works for you,
[http://www.ubuntuforums.org/showthread.php?t=171202](http://www.ubuntuforums.org/showthread.php?t=171202)

Good luck!

---

### Post by n3tfury on 2006-05-07
[QUOTE=richbarna]Get a router, USB modems suck big style.
Routers areb easy peasy to configure from their web interface.[/QUOTE]

i totally agree.  they're so cheap, it's almost a no-brainer to get one. GO. NOW.

---

### Post by bash the bishop on 2006-05-07
I didnt see the need to get one when it was free with the net connection. It has served me well so what am I missing? I have looked at the link provided, and the Sagem F@st 800 isn't listed anywhere, but the F@st 1000 is not support. Guess mine goes the same way then?

---

### Post by Blondie on 2006-05-07
Yes I would think it's not supported by eciadsl. Check out this thread,

[http://www.ubuntuforums.org/showthread.php?t=44459](http://www.ubuntuforums.org/showthread.php?t=44459)

You might want to ask the guys there if you have trouble.

---

### Post by ZiLOG_Z80 on 2006-05-07
The Sagem F@st800 works fine in Breezy and thoug a little complicated to get set up is a good learing experience as you may need to compile some things eventually, and theres no way you're going to get by never using the comand line

---


---
title: "MacBook Internet Connection Via Airport"
date: 2008-03-26
forum: Apple Intel Users
---

### Post by AussieHolden on 2008-03-26
Hi,

I just installed Ubuntu V8.04 lastnight but I can not connect to the internet via the AirPort on my MacBook which is a 2008 2.1GHz Intel Core Duo 1G mem and the AirPort card is Broadcom BCM43xx 1.0

What do I need to do to get it connected to the internet etc.

Please be very clear in your insturctions as I am new to all this.

---

### Post by cyberdork33 on 2008-03-26
You have to use ndiswrapper and the appropriate windows driver.

There is currently a bug with ndiswrapper in Hardy so you will continue to have issues anyway.

[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b)
[http://ubuntuforums.org/showthread.php?t=735846](http://ubuntuforums.org/showthread.php?t=735846)

---

### Post by AussieHolden on 2008-03-26
> **cyberdork33 said:**
> You have to use ndiswrapper and the appropriate windows driver.

There is currently a bug with ndiswrapper in Hardy so you will continue to have issues anyway.

[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b)
[http://ubuntuforums.org/showthread.php?t=735846](http://ubuntuforums.org/showthread.php?t=735846)

This refers to a MacBook Santa Rosa never heard of it I just know it as a MacBook 2008 model.

Why hasn't anyone just made an install program to set this all up I'm not a programer and I still don't understand those instructions there too advanced for a newbie.

If I can not get this to work then Ubuntu is useless to me as it won't be mobile.  Funny how it never has a problem with ethernet ?

---

### Post by cyberdork33 on 2008-03-26
> **AussieHolden said:**
> This refers to a MacBook Santa Rosa never heard of it I just know it as a MacBook 2008 model.Santa Rosa refers to the chipset in the newer Macbooks / Macbook Pros.

> **AussieHolden said:**
> Why hasn't anyone just made an install program to set this all up I'm not a programer and I still don't understand those instructions there too advanced for a newbie.New users use these same instructions all the time. Those instructions are pretty much step by step what you have to do in at a commandline. You can copy and paste. It cannot be much more simple than that until an open driver can be made. You can complain to Apple / Broadcom since they create proprietary hardware and software.

This is only made even more difficult because you have installed Beta software and there are bugs. Since there is a bug that is not yet fixed, you have to edit the script to load and unload modules in the correct order as shown in the second link I posted.

> **AussieHolden said:**
>  If I can not get this to work then Ubuntu is useless to me as it won't be mobile.  Funny how it never has a problem with ethernet ?
Ethernet is not WiFi, completely different beast.

---

### Post by simplebeep on 2008-06-06
> **cyberdork33 said:**
> New users use these same instructions all the time.

It may be easy for you, but not for some.
I sure will complain about proprietary hardware!  :mad:  But I also think that if these instructions are easy enough for a *moderate* noob, then they should be included in the standard Ubuntu install.  Why has no one come up with a GUI all-automatic installer for this stuff yet, indeed?!

Ubuntu may be Linux, but for it to gain traction, it must work for *every* user without the use of the terminal!

Oh, well.  Maybe in 8.10...

---

### Post by cyberdork33 on 2008-06-08
> **simplebeep said:**
> It may be easy for you, but not for some.
I sure will complain about proprietary hardware!  :mad:  But I also think that if these instructions are easy enough for a *moderate* noob, then they should be included in the standard Ubuntu install.  Why has no one come up with a GUI all-automatic installer for this stuff yet, indeed?!

Ubuntu may be Linux, but for it to gain traction, it must work for *every* user without the use of the terminal!

Oh, well.  Maybe in 8.10...
doubtful. There is way to many other things going on. If you would like to create this miracle app then you are welcome to do so.

---


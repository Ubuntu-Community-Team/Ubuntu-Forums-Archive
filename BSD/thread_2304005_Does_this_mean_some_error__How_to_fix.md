---
title: "Does this mean some error ? How to fix ??"
date: 2015-11-23
forum: BSD
---

### Post by soamz on 2015-11-23
See attached. 
[ATTACH=CONFIG]265739[/ATTACH]

---

### Post by Habitual on 2015-11-23
It's not an error in FreeBSD.
It means you have to enter the username followed by the correct username password, for the FreeBSD system.
Did you install FreeBSD?

How to fix is subjective. From a FreeBSD perspective there doesn't seem to be any fixing necessary.
What would you like "fixed"?

---

### Post by soamz on 2015-11-23
Did, but the script owner says, this means some error in hardware.

He said, 
"Thats is the problem with the system have issue and was reported error in your MFI0 will not able to use the software
Normally is issue with your hardware or maybe can be hardware incompatibility. Check, 
https://www.freebsd.org/releases/10.1R/hardware.html"

How do I know my server Dell 2950 is compatible or incompatible for FreeBSD ??

I cant believe this.

> **Habitual said:**
> It's not an error in FreeBSD.
It means you have to enter the username followed by the correct username password, for the FreeBSD system.
Did you install FreeBSD?

How to fix is subjective. From a FreeBSD perspective there doesn't seem to be any fixing necessary.
What would you like "fixed"?


I think I need the upgrade the drivers or something, as thats what I read from google. 

How to upgrade the firmware or drivers doe the RAID or DRAC ?

Also, I think need to upgrade BIOS. 
So, how do I upgrade those things now ??

I have bought 2 Dell 2950 refurbished servers and need to install FreeBSD to it. 

But its showing some mce0 error or something. 
I think I need to upgrade BIOS and DRAC both. 

How to do it and whats the download link ?

---

### Post by tgalati4 on 2015-11-23
You can generally upgrade the BIOS and RAID BIOS for PowerEdge servers by downloading a CD image from Dell, burning it correctly, and booting from it. Then follow the instructions carefully.  PowerEdge servers are generally compatible with Linux, but BSD is Unix, not Linux, a different operating system.  Why are you posting in an Ubuntu Linux forum?

A quick web search shows that there is some problem with Dell PERC raid cards and the *mfi* driver that is used:  [http://engineering.wayfair.com/2012/03/freebsd-9-0-on-dell-poweredge-12g-servers/](http://engineering.wayfair.com/2012/03/freebsd-9-0-on-dell-poweredge-12g-servers/)

Since your error shows mfi0, I presume that the error is coming from this driver.  Don't know how to fix, other than building a new driver from the latest source.  Look on the freebsd forums.

---

### Post by Habitual on 2015-11-23
Wow. I so missed that one. :)

---

### Post by tgalati4 on 2015-11-23
[http://www.dell.com/support/home/us/en/19/product-support/product/poweredge-2950/drivers](http://www.dell.com/support/home/us/en/19/product-support/product/poweredge-2950/drivers)

Download the files, burn a CD, boot from it, follow the instructions.

---

### Post by matt_symes on 2015-11-23
I've merged your two threads and moved them to the BSD subforum.

---

### Post by soamz on 2015-11-23
> **tgalati4 said:**
> You can generally upgrade the BIOS and RAID BIOS for PowerEdge servers by downloading a CD image from Dell, burning it correctly, and booting from it. Then follow the instructions carefully.  PowerEdge servers are generally compatible with Linux, but BSD is Unix, not Linux, a different operating system.  Why are you posting in an Ubuntu Linux forum?

A quick web search shows that there is some problem with Dell PERC raid cards and the *mfi* driver that is used:  [http://engineering.wayfair.com/2012/03/freebsd-9-0-on-dell-poweredge-12g-servers/](http://engineering.wayfair.com/2012/03/freebsd-9-0-on-dell-poweredge-12g-servers/)

Since your error shows mfi0, I presume that the error is coming from this driver.  Don't know how to fix, other than building a new driver from the latest source.  Look on the freebsd forums.

Is there a FreeBSD sub forum here ?
So, basically Im not alone :(

> **tgalati4 said:**
> You can generally upgrade the BIOS and RAID BIOS for PowerEdge servers by downloading a CD image from Dell, burning it correctly, and booting from it. Then follow the instructions carefully.  PowerEdge servers are generally compatible with Linux, but BSD is Unix, not Linux, a different operating system.  Why are you posting in an Ubuntu Linux forum?

A quick web search shows that there is some problem with Dell PERC raid cards and the *mfi* driver that is used:  [http://engineering.wayfair.com/2012/03/freebsd-9-0-on-dell-poweredge-12g-servers/](http://engineering.wayfair.com/2012/03/freebsd-9-0-on-dell-poweredge-12g-servers/)

Since your error shows mfi0, I presume that the error is coming from this driver.  Don't know how to fix, other than building a new driver from the latest source.  Look on the freebsd forums.

Is there a FreeBSD sub forum here ?
So, basically Im not alone :(

> **tgalati4 said:**
> [http://www.dell.com/support/home/us/en/19/product-support/product/poweredge-2950/drivers](http://www.dell.com/support/home/us/en/19/product-support/product/poweredge-2950/drivers)

Download the files, burn a CD, boot from it, follow the instructions.


I see one exe file for BIOS. 
Apart from that, what else to download ?

And download those exe files and make a bootable drive ?
But how does that help ?

The multiple files bootable, Im confused.

---


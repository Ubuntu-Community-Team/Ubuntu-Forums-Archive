---
title: "Strange error in virtual consoles."
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by roach of discord on 2005-06-27
For whatever reason, whenever in a virtual console, I am flooded with the error:

hub 5-0:1.0: over-current change on port 2

It makes it hard to type anything...as this error keeps coming up.  Any idea as to what this means, and how to fix it? 

Thanks!

---

### Post by skoal on 2005-06-27
Is it a USB keyboard? If so, you might be having issues with it and the kernel driver.  Try to use a different port (a lower speed one if available) and see if it continues.  If you don't know which ports are 1.1 or 2.0, just keep trying different ones and see if it goes away.

\\//_

---

### Post by roach of discord on 2005-06-27
Hi, thanks for your response.  I actually removed all of my usb connected items..and still get this error, even after a reboot.

---

### Post by roach of discord on 2005-06-27
**update**

I was told to unload the usb module..by: rmmod ehci-hcd

This fixed the issue!  However, does this mean USB devices will no longer work?  It seems my external harddrive still works..which is USB.

Do I need to do anything else to fix this permanantly?

Thanks!

-RoaCh

---

### Post by mirko_3 on 2008-04-29
Three years later and now suddenly I get the same problem. Could it be a hardware issue? Any answer to the above question?

---


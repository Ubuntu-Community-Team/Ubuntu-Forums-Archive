---
title: "Shared printer disconnect (CUPS problem?)"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by mattorama on 2007-09-28
I have a printer connected to my ubuntu box.

I used the instructions here:

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP]("https://help.ubuntu.com/community/NetworkPrintingFromWinXP")

 to share the printer with windows XP.

This works great, except after some time the printer is no longer available from within XP. Attempting to access the printer (in XP) reports that the printer is unavailable.

I was thinking that this was an XP issue until I noticed that restarting cups...

sudo /etc/init.d/cupsys restart

 causes the printer to come back "online" from within XP.

How can I prevent the printer from disconnecting?

Any help is appreciated!

---

### Post by ryanVickers on 2007-09-28
if there is any way to hook it into your router instead, this would be the first step - it's so much better! :)

if there isn't a way for you to do this, then perhaps just have a script that runs in the backgound and restarts cups every hour or so (however long it takes)

just do
```

#!/bin/bash
while [ "5" -eq "5" ]; do
gksudo /etc/init.d/cupsys restart
sleep 3600
done

```of course, you'll get a password window popping up ever hour :p

---

### Post by mattorama on 2007-09-29
While I applaud your ingenuity, having a password window pop up every hour or so is not very workable. It seems to me that there ought to be a fix for this or at least an explanation of what is going on.

Regards,

Matt

---

### Post by ryanVickers on 2007-09-29
Well, if it was me, I might just restart it before printing, but I don't really know why it would keep randomly disconnecting.  You should time exactly how long it is, and see if it's more or less random, or if it's like every hour or 2.  If it's on a set time, maybe it's doing it as a sleep mode or something :confused:

---

### Post by djchandler on 2007-09-29
> **ryanVickers said:**
> Well, if it was me, I might just restart it before printing, but I don't really know why it would keep randomly disconnecting.  You should time exactly how long it is, and see if it's more or less random, or if it's like every hour or 2.  If it's on a set time, maybe it's doing it as a sleep mode or something :confused:

What Ryan says makes sense to me. The printer is unavailable to Linux as well  if you are having to restart cups. I wonder if connecting the printer to the XP box causes the problem in reverse. BTW, you didn't say what model and make of printer you are using.

I have an old LaserJet 4 Plus with a JetDirect card in it. It's available to all 4 computers here even though it goes into a power saving mode after a while. Some newer printers are dependent on drivers, especially Windows drivers, to fully implement all functions. The "awaken" function is not being supported by your printer under Linux. ](*,)

DJ

---

### Post by mattorama on 2007-09-29
The printer is a Brother HL-5040 Laser. I'll check into the "awaken" function.

Thanks,

Matt

---

### Post by mattorama on 2007-10-01
I don't think the printer is the issue.

If you look at:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-5040](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-5040)

You can see that the printer is fully supported.

---


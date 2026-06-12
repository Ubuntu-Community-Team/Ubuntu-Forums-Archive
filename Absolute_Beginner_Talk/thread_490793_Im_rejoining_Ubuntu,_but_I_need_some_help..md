---
title: "Im rejoining Ubuntu, but I need some help."
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by firebirdworks on 2007-07-02
The last time I tried to use Ubuntu, the latest release was Edgy Eft, and it didn't work well with my HP laptop.  For example, my wireless internet built in card did not work.  It was the only reason that I didn't stick with Ubuntu.  Now that windows has made me so angry that I want to kick Bill Gates, im ready to go back to a dual boot.

I really don't want to go thru a major code in terminal.  Last time I tried that it took me 4 days, and it still didn't work.  I even had a friend that tried to fix it and couldn't and he helped make pidgin.

Can anyone tell me if there was a major update in the drivers?  Thanks.

Amen.  Ubuntu.

---

### Post by Pathfinder_ on 2007-07-02
well, ubuntu 7.04 uses a newer version of the kernel than 6.10 so I guess your wireless issues might have been resolved. Try the live CD and see for yourself.

---

### Post by IYY on 2007-07-02
It's probably a Broadcom chip. They don't work with Ubuntu by default, but work just fine with ndiswrapper.

---

### Post by firebirdworks on 2007-07-02
Ah yes.  Ndiswrapper.  Good, err... bad times.

---

### Post by ramjet_1953 on 2007-07-02
Certainly, with Feisty, it does recognise hardware better and installing codecs is a breeze.

For codec install, you can follow the tutorial, which is in the sticky section of this forum, or if you just try to run a media file, it will ask you automatically, if you want to download the relevant codec.

Getting back to your wireless networking, if you post the info on your particular wireless card, I'm sure that it can be coaxed into operation, with the help of this forum.

Regards,
Roger :cool:

---

### Post by evny on 2007-07-02
I have an HP Pavilion DV5003 laptop.  Using Edgy, after following the how-to for Broadcom cards in the networking forum, I was disappointed to see that the card still didn't work.  It was something about the kernel needing to be updated or recompiled -- something that I didn't know how to do.  However, after updating to Feisty, the card immediately started working.  So, it will probably work for you, too. (But I think you still have to use ndiswrapper and the Windows drivers.)

---

### Post by nwbearcat84 on 2007-07-02
For years I have had the same problems as you have had with HP laptops and Linux (especially the network drivers).  To get mine to work in my laptop, I downloaded the absolute latest version of ndiswrapper from their site and the executable driver file from HP.  Extract the driver from the .exe file using the cabextract utility (you may have to install it).  The rest of the instructions are in the ndiswrapper package.  I have tried lots of install methods from the Ubuntu forums, and none seem to work, but I tried this method and it worked first time, no problem.

---


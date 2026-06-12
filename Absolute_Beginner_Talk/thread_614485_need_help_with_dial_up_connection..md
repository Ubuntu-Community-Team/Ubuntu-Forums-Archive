---
title: "need help with dial up connection."
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by jess7901 on 2007-11-16
ok, Ive been trying to figure this out on my own and all Ive accomplished is getting a migraine.
 
I just got my computer set up as a dual boot with Windows XP and Linux.  Now Im trying to set up my internet connection with the modem that came in my computer.  

I just cant seem to do it on my own.  Help please!!

---

### Post by jess7901 on 2007-11-16
ok, so I guess the first question I should be asking is... "how do I figure out if my modem is compatible with Ubuntu?"

---

### Post by brianC on 2007-11-16
You need to know if your modem is compatible with Linux. The page that had a list of modems seems to be missing?  Try this this page  [http://www.linmodems.org/](http://www.linmodems.org/) for a list.
   [www.linuxant.com](www.linuxant.com) ( they have the drivers for  compatible modens )

---

### Post by Bartender on 2007-11-16
Chances are that it's not.  What can you find out about the modem?  Can you read anything off the card?

---

### Post by jess7901 on 2007-11-16
it's an Agere Systems PCI soft modem. what else do you need to know?

---

### Post by jess7901 on 2007-11-16
ok, so I ran the ScanModem, and it did not find it...does that make any sense?? to anyone?
:confused:

---

### Post by NotTheMessiah on 2007-11-16
You need to find out the chipset type/brand and find the appropriate driver:
[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745)
That is a free driver for conexant chipsets which you can install.
If you chip is not supported then buy yourself an external serial modem - easy :)

---


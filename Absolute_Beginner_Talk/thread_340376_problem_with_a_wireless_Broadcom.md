---
title: "problem with a wireless Broadcom"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by nekofelin on 2007-01-17
hi i'm very new to linux systems and am having a hard time with wireless.  well i followed a tutorial (currently using Ubuntu 6.06 dapper) and it was the one for the broadcom bcm43xx-fwcutter or something like that and well it works now but the problem is the wireless likes to turn it's self on and off whenever it feels like which is not good.  is there a solution to fix it? i'm very confused

---

### Post by scrooge_74 on 2007-01-22
Have you notice when this happens? Any particular application, maybe it is losing the signal from the router?

---

### Post by NICU28 on 2007-01-22
I had a similar problem with the first time I used the fwcutter utility.  I went back to the manufacturer's website (Linksys in my case) downloaded the latest drivers and followed the instructions at [http://www.ubuntuforums.org/showthread.php?t=185174&page=2](http://www.ubuntuforums.org/showthread.php?t=185174&page=2).  The second post gives a good example for using the utility:
```
sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-23-386 /path/to/bcmwl5.sys
```
This worked in my case, hope this helps.  If not what brand/model of card are you using?

---


---
title: "Broadcom 43xG Wireless"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by apostoj on 2007-02-20
Is it possible to get this thing to work?  I am totally new to linux I am on my second day of dealing with this and all of those old commands are coming back to my fingers from the old days...

Sorry,  I am just stoked to be playing with a real OS again.  I don't want to lose my enthusiaim with this, like I said I am stoked.

But i am a little frustrated now with the nic.  

can someone answer the question on weather I can get this to work.

Can one of the linux guys point me to the a step by step process.
Like how would I get the drivers..and what is this FWCUTTER command?

I know in a day or two once I get the nic to work that I will be less frustated.  I want to be a microsoft - less house..I am so sick of there bloat and power..

---

### Post by NewOldTimer on 2007-02-20
n00b here but this might help
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by kelbizzle on 2007-02-20
Which card do you have? If you have the BCM4318. I have gotten this to work every time I reinstall edgy.   [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) this is the thread I use every time. I just  saved the thread and the driver.


```
 lspci |grep broadcom
``` 

lspci will list the pci devices  "|grep broadcom" will look for broadcom anywhere in the list.

---

### Post by apostoj on 2007-02-20
I don't see it in the networking tools view....

---


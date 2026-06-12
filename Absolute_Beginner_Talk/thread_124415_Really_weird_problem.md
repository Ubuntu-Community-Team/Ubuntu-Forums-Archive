---
title: "Really weird problem"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2006-02-01
Hello People,
I am in a dual boot with Win XP and Ubuntu. Here is the thing...everytime I log onto either of the OS's I need to reset my clock. Both the Ubuntu and XP reset the hardware clock differently. 
For example,
Its currenly 23.12 at my place. I just set my ubuntu clock and its showing 23.12. But now I went to XP and the clock over there showed some 10.34. When I reset that and came back to ubuntu..its showing 5.00.

Any suggestions to correct this?
Linuxnovice.

---

### Post by editrix on 2006-02-02
I found this on the Ubuntu FAQ page

[http://www.ubuntu.com/support/faq?action=show&redirect=FAQ](http://www.ubuntu.com/support/faq?action=show&redirect=FAQ)


> Everytime I dual boot to my Windows partition, my computer clock become X hours ahead/behind my local time. How do I solve that problem with Ubuntu? 

Edit the file /etc/default/rcS. in there is a setting for time ("UTC="). 

Set it to no ("UTC=no")

Hope this helps.

---

### Post by raublekick on 2006-02-02
what's really weird is that on my last dual-boot setup with Breezy, this was happening, but after I re-installed both XP and Breezy the problem has not occured since!

---


---
title: "Create custom live CD?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by rodtempleton on 2007-06-26
Is there a way to take my current install and essentially turn it into a live CD that I can use to reinstall my system in case of a serious crash, or just in case I completely hose it?  Once I get the the system customized, I'd really prefer to not have to spend a few hours getting everything reinstalled and configured the way that I like it.

Cheers,
Rod

---

### Post by bodhi.zazen on 2007-06-26
Check these links :

Customize the Live CD:
	[https://help.ubuntu.com/community/LiveCDCustomization/6%2e06](https://help.ubuntu.com/community/LiveCDCustomization/6%2e06)
	[http://www.livecdlist.com/wiki/index.php/LiveCD_Creation_Resources](http://www.livecdlist.com/wiki/index.php/LiveCD_Creation_Resources)
	[http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1](http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1)

---

### Post by mlentink on 2007-06-26
Maybe I totally misunderstand, but isn't this what backups are for?

---

### Post by rodtempleton on 2007-06-26
Yes, this is why you do backups, and I certainly do backup my data.  However, I was looking for a bit more of a convenient solution.  Thanks to both of you for the feedback, though.

---

### Post by Seisen on 2007-06-26
> **mlentink said:**
> Maybe I totally misunderstand, but isn't this what backups are for?

I think he is looking at in the point of view of if my computer crashes and I need this information right now I have it available to use.

---

### Post by dingo on 2007-07-15
Try using partimage. It creates a file containing an exact duplicate of a partition that can be restored easily in case of disk failure (or operator error). The partition must be unmounted at the time the image is created, so I find it easiest to boot to a live CD, and run partimage from there. I use System Rescue CD (which boots fast and contains partimage), but I think you could also do it with the Ubuntu live CD.

---


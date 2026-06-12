---
title: "Seriously considering moving back to Windows....."
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by speedway on 2007-07-08
... and turning my Ubuntu install into a Virtual Machine. However, I don't know if it is at all possible to do that. If I do go back, can I take my whole installation, as-is, and create a VM based machine out of it? If so, any pointers to information on how?

In case you are wondering, I am returning to the world of Windows programming and the development tool I use is Windows only, as are the source code control, databases and everything else associated with it, including the Microsoft .NET framework. I have tried all of the combinations under VMWare but performance is dismal so I need to do all this under "real" Windows. I want to keep Ubuntu around as I intend to use it for everything else....

Any help appreciated....

Oh, and I am not in a position to buy a whole new machine for development, not yet anyway...

Cheers
Bruce

---

### Post by drascus on 2007-07-08
Why not running as a duel boot. I have run Ubuntu as a duel boot program many times and I found it easy and a nice way to have both worlds. Just install windows first then install ubuntu and tell it to partition the disk as a duel boot. 
Good luck
~Mike~

---

### Post by vexorian on 2007-07-08
From my experience virtualization is faster for a windows guest in Ubuntu host than Ubuntu guest in windows host, odd stuff?

---

### Post by plinydogg on 2007-07-08
But if you're using Vista don't let Ubuntu mess with your partitions. Instead, use Vista's built in partition tool otherwise problems can occur.

---

### Post by starcraft.man on 2007-07-08
Well, I was going to recommend the [VMware converter]("http://www.vmware.com/products/converter/") to make a vmdk file for your linux install, I don't think it will work though. It states it only converts physical installs of Windows to VM images, as well as converting third party VM images. So no, you can't just clone the install into a VM to my knowledge.

I'd just stick to a dual boot, if you already have that no problem eh? You can install a VM into Windows to play with Ubuntu in it, but I don't see much point. If all you do is development in Windows, then just boot Ubuntu when your not doing development.

Oh and just a thought, but maybe try [VBox?]("http://www.virtualbox.org/") I have heard quite a few people say they got better performance out of it.

---

### Post by speedway on 2007-07-09
Thanks all

It looks like I'll wait until I can get a specific machine to run Windows on. My whole reason behind running Ubuntu in parallel was to use email, web etc at the same time as my development efforts. Dual booting won't allow that. I'll check to see if this machine can take more than 1Gb  of memory so Windows under VMWare will perform a little better....

Cheers
Bruce

---

### Post by deadlikeoscar on 2007-07-09
Not to knock VMWare but I think that Virtualbox is faster. Could just be me though.

---

### Post by Church.Cameron on 2007-07-09
> **deadlikeoscar said:**
> Not to knock VMWare but I think that Virtualbox is faster. Could just be me though.

no your right it has shown to be faster

---


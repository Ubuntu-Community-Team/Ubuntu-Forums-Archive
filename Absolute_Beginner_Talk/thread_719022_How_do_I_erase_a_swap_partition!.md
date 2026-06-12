---
title: "How do I erase a swap partition?!"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by fredscripts on 2008-03-08
Hi!

I'm on a macbook and I have a swap partition a part from mac OS that I want to erase. From mac OS I cannot do it and from Ubuntu 7.10 live cd neither. Anyone knows how can I do it?

---

### Post by JoshuaRL on 2008-03-08
I would suggest [Parted Magic.](http://partedmagic.com/wiki/PartedMagic.php)  It's also a Live CD, and will allow you to edit partitions.  You can delete, add, merge partitions from it.

Sorry to hear you're getting rid of Ubuntu/Linux.

---

### Post by fredscripts on 2008-03-08
Thanks for answering! 

I don't want to get rid of Ubuntu, I just want to triple boot on my macbook and I want to clean the system before start the process!!

Rigth now I'm having problems to burn CD's, anyone knows another way (some software, or from the ubuntu live CD) to delete that swap partition?

---

### Post by JoshuaRL on 2008-03-08
Yeah, the Ubuntu Live CD should have GPartEd on it somewhere.  That stands for Gnome Partition Editor.  That should let you fix what you want.

And I'm sorry to jump to that conclusion, I just saw that screenshot and assumed I knew what was happening.

---

### Post by fredscripts on 2008-03-08
Thanks! No problem!

I cannot delete swap parition with Ubuntu 7.10 Live CD. Seems the live CD uses that partition so I cannot delete it with gparted.

Any other idea?

---

### Post by logos34 on 2008-03-08
> **fredscripts said:**
> Thanks! No problem!

I cannot delete swap parition with Ubuntu 7.10 Live CD. Seems the live CD uses that partition so I cannot delete it with gparted.

Any other idea?

Post a screenshot of Gparted from the live cd.

Or run this in a terminal and post the output:
[B]
sudo fdisk -l[/B]

---


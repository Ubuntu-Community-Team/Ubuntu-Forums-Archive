---
title: "So...I can keep folders of my choice when installing from CD?"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by cam2009 on 2007-10-17
I've been using Feisty for 6 months or so, and can't wait to upgrade to Gutsy. I've accumulated more and more little problems from my first couple months of tinkering, so I figure it's probably good to start fresh. I backed up my files and videos, but I'm having a tough time figuring where I can put my music folder (iPod doesn't hold it all, other hard drives are full). I could've sworn there was an option when I select to erase my entire hard drive and install Ubuntu to keep whichever folders I want. Is that right? Is there any significant risk involved in this? For example, if something goes wrong during the installation, have there been cases of losing these files, or does it make sure those folders are copied over first? Or am I making this feature up?

---

### Post by LowSky on 2007-10-17
What you can do is make your /home file its own partition, this way when you install ubuntu it doesn't erase whats there.

so you will have 3 partitions

/ (root)
/home
swap

---

### Post by qpieus on 2007-10-17
You can't keep folders during the installation except if the folders you want to keep are on a separate partition. That is, you can tell the installer to not touch a particular partition and whatever is on that partition will be retained. I hope that answers your question. As far as risk involved when doing this - sure there's always a chance something could go haywire, but I've installed a few times and told it not to touch certain partitions and everything was fine.

---

### Post by cam2009 on 2007-10-17
Thanks, glad I asked or that would've been a headache. I think if I split my music collection in two, half will fit on the hard drive and half on the iPod, that way I don't have to worry about another partition.

---


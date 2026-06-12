---
title: "HP pavilion zv5000 and Ubuntu"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by MST3Kakalina on 2006-03-26
I have been running Debian on my HP pavilion zv5000 notebook for about a year and a half now.  I have hit some issues that I can't seem to fix, so I am considering wiping that installation and using Ubuntu instead.  

(I'm posting this here because this will be my first solo Linux install, when I switched to Debian I had a friend sitting there with me to move things along. Even though I've been using Linux for a while, I still need things explained to me step-by-step, so I don't want to test the patience of those in the installation forums.)

My major concern is hardware compatibility.  Searching this site and on google, things seem to be rosy except for the wifi card (which I don't use much, anyway). It'd be nice to see if this is really the case and what issues other people had, if any.  Also, I'm wondering what to do with Debian.  As it stands now, I only have one partition, no swap or anything.  Is there a way to create new partitions (for /home and swap, I suppose) without having to wipe the disk and start again?

I can already get the installation disc from a friend (a comp sci professor here hands them out to all of his students), though I don't know how old it is or what version he has.

**So in general**:

1. Any experiences you have had with hp pavilion zv5000s (or comparable HP models) and Ubuntu in general; advice, warnings, etc.
2. Tips and advice on partitions and working with previous installs.

Thanks!

---

### Post by debernardis on 2006-03-26
Might help you:
[http://ubuntuforums.org/showthread.php?t=100924](http://ubuntuforums.org/showthread.php?t=100924)
[http://ubuntuforums.org/showthread.php?t=100643](http://ubuntuforums.org/showthread.php?t=100643)
(mine is a zv6278ea)

---

### Post by MST3Kakalina on 2006-03-27
Thanks!  I was also able to come across a copy of the Live CD (5.10), so that should take care of my compatibility questions.

---

### Post by xoros on 2006-06-07
This may help you with it's obscure nforce modem:

[http://www.ubuntuforums.org/showthread.php?t=43433](http://www.ubuntuforums.org/showthread.php?t=43433)

---

### Post by Nicks Spleen on 2006-06-11
I own a hp pavilion zv5200 and have been using ubuntu on it since warty and dapper is by far the best thing to happen to my laptop. Everything is working now except for the card reader becuase the lack of linux drivers. I am also not sure about the modem becuase I don't have anything to test it with. I used ndiswrapper to get the broadcom card wifi card to work. I fiddled around with the new drivers for dapper but since they are capped at 11mb/s I desided just keep the faster windows one. The nvidia drivers from the repos work well, although I haven't been able to get xgl/compiz working under gnome. I have heard that there are no problems with xgl/compiz in KDE and I haven't tried the new versions yet. In order to get flash working, I installed opera using the new beta2 deb and used the 32bit flash plugin. Since I perfer opera to firefox, it worked out well. The only thing you'd be missing would be wma/wmv support. Overall I find its one of the easier laptops to get ubuntu running on.

I used tseliot's guide for the nvidia drivers becuase you have to add a couple lines to your xorg.conf:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---


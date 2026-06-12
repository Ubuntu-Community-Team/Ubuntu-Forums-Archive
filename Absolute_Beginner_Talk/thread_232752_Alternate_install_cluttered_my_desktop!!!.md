---
title: "Alternate install cluttered my desktop!!!"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by spiral777 on 2006-08-09
I guess the alternate install CD noticed my wife's XP partition and automatically mounted it when I booted up for the first time. Is there a way to remove the icon from my desktop?

---

### Post by Klaidas on 2006-08-09
Isn't autodetecting and automounting partitions a good thing? :)
If you want to remove it, clicking "Unmount partition" might help

---

### Post by spiral777 on 2006-08-09
I love that it did it, I'd just much rather it stayed up in Places where it belongs! :p

---

### Post by Klaidas on 2006-08-09
Well, at least I browse my XP partition pretty often, so it's easier to do it if it's on the destop.
It is added in Places too.

---

### Post by catlett on 2006-08-09
There are 2 things you can do. Change the mount point. Partitions mounted in media get a desktop icon. Chanmge the mount poiunt to /mnt/wondows (or whereever you want) in /etc/fstab

If you don't want any icons for partitions, go to Configuration Editor under Applications (you may have to enable config ed. through alacarte menu editor) 
When it opens, go to Apps<Nautilus<Desktop and uncheck "volumes visible"
That will keep the volumes' icons from appearing

---


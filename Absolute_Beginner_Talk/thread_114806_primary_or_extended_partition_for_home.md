---
title: "primary or extended partition for /home"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by vinthund on 2006-01-09
hello,

what partition do you use for /home in a dual boot machine, primary or extended? And why?

vin

---

### Post by Arktis on 2006-01-09
I use an extended partition for /home.  It's just better suited to my way of thinking/doing I suppose.  Having home in it's own parition can be very beneficial if you broke something in root and you're looking to reinstall and you want to easily save user settings for yourself and other users.

---

### Post by Thirsteh on 2006-01-09
Primary volumes are the "classic" partitions. The problem with these are that there can be a max of four partitions on one drive, and thus extended partitions were invented. They're simply "additional partitions", in case you've already used up the four primary partitions. If you're not going to have more than four partitions, do primary.

---

### Post by Arktis on 2006-01-09
Oh, I thought he was talking about simply having /home on the same primary partition as the root filesystem or having it in it's own separate extended partition.  My bad.

---

### Post by Thirsteh on 2006-01-09
Hehe, I noticed :) That **is** a good idea, though. I'd even say it's a must for any Linux user, to have /home on a seperate partition, that is.

---


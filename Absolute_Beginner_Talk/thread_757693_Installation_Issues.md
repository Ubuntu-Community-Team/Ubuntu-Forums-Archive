---
title: "Installation Issues"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by tweygandt20 on 2008-04-17
When installing Ubuntu 7.1 I had it format my Win XP OS (this was intentional). What is happening now is that all the system files are on a 839 Mb partition and I have no room for the updates, how can I remedy this?  Also, I dan not start the computer without the Ubuntu boot disk, it tells me to removethe disk, hit enter and then it just hangs.

---

### Post by northern lights on 2008-04-17
Can you post the output of ```
sudo fdisk -l
``` Thank you.

---

### Post by bumanie on 2008-04-17
Yes > sudo fdisk -l would be useful, but if what you are saying is right re the 839mb, there is no way a ubuntu file system can install into that space - it needs something like 3.5 gb, before updates. I think you will have to reformat and do a fresh install. If you do that partition so that you have a separate /home. Have 7-8g for / 1-2g for swap and the rest for /home.

---

### Post by tweygandt20 on 2008-04-17
Ok, all is better now... I just simply re-installed ubuntu, I'm thinking I might have not done it correctly the first time but now it is running just fine.

Thank you for your help.
Tony

---


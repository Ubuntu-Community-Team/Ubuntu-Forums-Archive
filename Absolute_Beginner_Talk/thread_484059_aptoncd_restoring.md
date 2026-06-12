---
title: "aptoncd restoring"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by stonerrob420 on 2007-06-25
I had to reinstall ubuntu dapper after a massive mess up on my part. I was tinkering with things I shouldn't have.    
 I installed aptoncd and backed up all my packages on the system. Now that I've reinstalled and got all the drivers and things I need. I used aptoncd to restore the packages to the /var/cache/apt/archives file. How to I get it to reinstall all the pacakges without downloading everything with sysnaptic. Didn't the  /var/cache/apt/archives  include all the updates ? Any help on this subject would be greatly appreciated. :p

---

### Post by cam_tram on 2007-06-25
You can try using Synaptic's "Install Downloaded Packages" option, it should get the dependencies if they're all in the same folder.

---


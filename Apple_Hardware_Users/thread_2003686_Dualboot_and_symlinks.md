---
title: "Dualboot and symlinks"
date: 2012-06-14
forum: Apple Hardware Users
---

### Post by bogren on 2012-06-14
Hi, I am currently dualbooting os x Lion and Ubuntu 12.04 LTS. Im sharing home folders like in this guide: 
[http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems](http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems)

basically I just disabled journaling on my hfs+ volume and changed uid to 501 to match the uid in os x. And then created symlinks in the home folder of my linux partition. All worked for a couple of reboots but now I keep loosing writing rights. I don't now if it is because ubuntu can't write to hfs+ partition anymore or because I lost permission to the os x home folder. But I guess it's the later. 

And also the links in the symlinks appear to be broken. Even if the path is correct (media/Macintosh HD/...). So I deleted them and created a new one wich appear to be working. But it has a lock on the folder-icon with the purpose of telling me I cant write to it?

How can I fix this?

---

### Post by bogren on 2012-06-16
Just bumping thread because I edited the post to be more specific

---

### Post by bogren on 2012-06-16
Looks like I fixed it by repairing permissions in OS X disc utility...

---


---
title: "Upgrade or clean install"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by alamba on 2006-03-12
Hi all,

Just wondering what people generally tend to do - upgrade to a new version of ubuntu or do a clean install? Since I run a ubuntu only laptop (no dual boot) I decided to go down the upgrade path from 5.04 to 5.10. However, contrary to popular belief, the apt-get upgrade bit doesn't really do as intensive a job as a clean install (well it didn't in my case). 

I later realized while troubleshooting some driver issues with help on the forums that the upgrade didn't change any drivers for me that were inbuilt into 5.10. Hence, now I'm considering doing a clean install for 6.04 rather than the upgrade path.

Akshay

---

### Post by encompass on 2006-03-12
I agree... I would do a clean install and keep your /home/ dir in a dif partition... that way you stuff will be just the way you left it.  Most time that works.  And you won't loose any data.

---

### Post by alamba on 2006-03-12
Yep I think that makes a lot of sence. However, I didn't take this account during my initial installation of ubuntu and hence only have a singe / partition (other than swap ofcourse). Probably not a good way of doing things.

Can I now change this to a seperate /home partition by doing the following:
1. Use gparted from a liveCD to change the size of /.
2. Create a seperate /home partition using ext3 filesystem.
3. Add this in /etc/fstab
4. Copy current /home to new /home --- something doesn't feel correct in this step since wouldn't the current /home now point to the new partition?

A

---

### Post by encompass on 2006-03-12
You would want o copy the data first before putting the information in Fstab.  Just incase something bad happens, like a power outage or cat in open case.  that kind of stuff.  and what you do that I would make usre that youhave the proper permissions set up.  You can do that with chown.  Or even more shnazzy is to use rsync to copy everything from one partition to the other without any loss of permisission.  I would look for howtos on that one.  if they don't have one.  you could make a howto on that.  Good thinking man.  I wish I knew about shrinking partitions.. but never had to.  Another option is to attach another driver and copy the data there temporarialy then install... and copy that data back.  I did that once.  A LOOONG time ago.

---

### Post by alamba on 2006-03-12
Backup is my mantra buddy! I do a daily backup anyway! Thanks for the rsync tip...will read up on that.

A

---

### Post by chris_andrew on 2006-03-29
This may help.

[http://www.gentoo.org/doc/en/articles/partitioning-p1.xml](http://www.gentoo.org/doc/en/articles/partitioning-p1.xml)

Chris.

---

### Post by alamba on 2006-03-29
Thanks chris. That is indeed very helpful.

A

---


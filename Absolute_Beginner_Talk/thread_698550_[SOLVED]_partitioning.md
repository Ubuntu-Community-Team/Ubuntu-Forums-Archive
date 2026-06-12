---
title: "[SOLVED] partitioning"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by chris200x9 on 2008-02-16
Hi, I want to set my parents up with ubuntu, they have a windows machine and they have important stuff on it. I was wondering how to set up a dual boot without erasing windows? Can I non-destructavly re-partition the windows disk?

---

### Post by drs305 on 2008-02-16
Check out this site. It can answer a lot of your questions:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

To answer your question, yes, you can. Do the routine stuff on the windows partition before you start (empty trash, defrag, back up important data, etc).

Edit: You can, but there are some precautions you have to take such as defragging to get the windows stuff to the front of the disk if you are going to reduce the size of it's partition.

---

### Post by sandysandy on 2008-02-16
> **chris200x9 said:**
> Hi, I want to set my parents up with ubuntu, they have a windows machine and they have important stuff on it. I was wondering how to set up a dual boot without erasing windows? Can I non-destructavly re-partition the windows disk?

dual booting is very much possible. in fact i have six linux distros co-existing with my win XP. when installing ubuntu (or any other linux distro) u will have options 
 - on which partition to install ( assuming you have more than one partition) or 
- to resize your existing win XP NTFS partition ( in this case u must defrag the drive prior to utilising this option)

basically Ubuntu will need one partition for root [COLOR="Blue"]/[/COLOR] and one for swap (twice ur RAM size generally).

during ubuntu installation it will also install GRUB boot loader which will give u option of booting ur win XP and Ubuntu.

But remember BACK UP important data as safety.

regards

---

### Post by kwacka on 2008-02-16
I would also recommend another partition,  /home, for storage of user data.

If you re-install or upgrade you can choose not to partition this and retain all your data & settings.

---


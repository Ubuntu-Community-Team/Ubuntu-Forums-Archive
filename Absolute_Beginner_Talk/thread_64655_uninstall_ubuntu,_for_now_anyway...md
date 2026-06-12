---
title: "uninstall ubuntu, for now anyway.."
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by kenific on 2005-09-11
All,

I created a dual boot of Windows XP and Ubuntu and it worked great til my IT guy found out. opppps--SO now he wants me to get it off of the laptop, but I have no clue how to do that. Ideally I would like to reallocate that partition and "give it back to XP" I will put ubuntu on my desktop at home and then just ftp into it I guess...so, any clue as to how I can get ubuntu off of my laptop keeping in mind that I am only an admin on the ubuntu partition. I have no admin rights at all to the XP portion... yeah I know I F'ed up....hahaha thanks for any help-

---

### Post by manicka on 2005-09-11
make a boot floppy to boot into Ubuntu.

Restore the windows mbr or get your IT guy to do it, then boot into Ubuntu with your floppy when he's not looking ;)

---

### Post by Lux Perpetua on 2005-09-11
Do you have a Knoppix CD? If so, boot into it and fire up QtParted. It should let you delete your Ubuntu partitions completely and then resize your Windows XP NTFS partition to reclaim the space. 

If you don't have Knoppix, check [here](http://www.knoppix.net/get.php). If you don't want to buy the CD, you'll need a CD burner and good internet access.

---


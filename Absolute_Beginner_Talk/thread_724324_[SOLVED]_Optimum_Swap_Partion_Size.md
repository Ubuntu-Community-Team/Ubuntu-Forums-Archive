---
title: "[SOLVED] Optimum Swap Partion Size"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by AlistairH on 2008-03-14
When I installed Gutsy a few weeks ago, I had 512MB RAM and a swap partition of 1.4GB was automatically created. I've since upgraded to 2GB RAM and was wondering what my swap size should be. I'd normally set it to twice the RAM.

Is there any issues I should know about when I resize the partition using the partition editor? Does it have to be done using the Live CD?

Also, while I'm on the subject, I'd like to move my home folders to a separate partition. Yes, ideally I should've done that at the start, but we live and learn. Would it be easier to backup all my data and simply re-install from scratch?

---

### Post by Oldsoldier2003 on 2008-03-14
> **AlistairH said:**
> When I installed Gutsy a few weeks ago, I had 512MB RAM and a swap partition of 1.4GB was automatically created. I've since upgraded to 2GB RAM and was wondering what my swap size should be. I'd normally set it to twice the RAM.

Is there any issues I should know about when I resize the partition using the partition editor? Does it have to be done using the Live CD?

Also, while I'm on the subject, I'd like to move my home folders to a separate partition. Yes, ideally I should've done that at the start, but we live and learn. Would it be easier to backup all my data and simply re-install from scratch?

2-3 GB is plenty of swap for almost any situation. if you want to  hibernate/suspend you need to be sure you have Swap > Ram

Iif you decide to resize your swap  it needs to be done with a live CD.

If you want to move your /home try this tutorial: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by sandysandy on 2008-03-14
> **AlistairH said:**
> 

Is there any issues I should know about when I resize the partition using the partition editor? Does it have to be done using the Live CD?



u could also consider GParted live CD.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

take backup of important data before resizing.

regards

---

### Post by AlistairH on 2008-03-15
As I thought. Thanks folks.

---


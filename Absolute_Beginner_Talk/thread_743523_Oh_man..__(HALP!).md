---
title: "Oh man..  (HALP!)"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Rowdy73 on 2008-04-02
Love Ubuntu 7.10, been using it for a while, moved into new house, computer got jostled around in the move, need help NAO.
Had to reinstall Ubuntu 7.10 from disk, step 3 is blank, here is my error message:

You need to specify a partition for the root file system (mount point "/") with a minimum size of 2 GB, and a swap partition of at least 256 MB. You may also set up other partitions if you wish.

Thanks in advance for any suggestions, just want to be Ubuntu'ing again!

---

### Post by Rocket2DMn on 2008-04-02
If you are doing manual partitioning, you have to give it at least 2 partitions:
1) a root partition, ext3 formatted at mount point "/".
2) a swap partition, formatted as "swap" with mount point "none"
So if you are doing a completely fresh install over the whole disk, delete the existing partitions so you have nothing but free space, then start from there and setup the 2 necessary partitions.

---

### Post by Rowdy73 on 2008-04-03
> **Rocket2DMn said:**
> If you are doing manual partitioning, you have to give it at least 2 partitions:
1) a root partition, ext3 formatted at mount point "/".
2) a swap partition, formatted as "swap" with mount point "none"
So if you are doing a completely fresh install over the whole disk, delete the existing partitions so you have nothing but free space, then start from there and setup the 2 necessary partitions.

Ok, how do i go about doing this?
(I can follow walk-throughs).

---

### Post by Rowdy73 on 2008-04-03
This is what i have right now.

[img]http://img221.imageshack.us/img221/7407/screenshotinstallra6.png[/img]

---

### Post by Rocket2DMn on 2008-04-03
Is your hard drive not detected?  Run
```
sudo fdisk -l
``` from a terminal (may not need sudo from the LiveCD).  What was on the previous screen?

---

### Post by canthus13 on 2008-04-03
Hmm... It's not detecting the drive quite right... I'd crack open the case and make sure that everything is connected properly.  Disconnect/reconnect the drives, including CD/DVD drives, then close it up and try again.

---

### Post by Rowdy73 on 2008-04-03
> **canthus13 said:**
> Hmm... It's not detecting the drive quite right... I'd crack open the case and make sure that everything is connected properly.  Disconnect/reconnect the drives, including CD/DVD drives, then close it up and try again.

Gonna do that now, be right back.

---

### Post by Rowdy73 on 2008-04-03
Very strange, my hard drives had to be reconnected, did that, and i'm reinstalling windows xp now.
Once that's finished, i can reinstall ubuntu and get my dual boot system back.

Using my laptop to type this.

Computing is never boring..

---

### Post by Rowdy73 on 2008-04-03
> **canthus13 said:**
> Hmm... It's not detecting the drive quite right... I'd crack open the case and make sure that everything is connected properly.  Disconnect/reconnect the drives, including CD/DVD drives, then close it up and try again.

Seems like that was the case, thank you for the advice on this.
I'll update on my progress later once i get a handle on it.

---

### Post by canthus13 on 2008-04-03
> **Rowdy73 said:**
> Seems like that was the case, thank you for the advice on this.
I'll update on my progress later once i get a handle on it.

No problem.. Glad I could help.

--Me

---


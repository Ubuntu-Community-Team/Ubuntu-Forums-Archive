---
title: "dual boot windows/linux"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by everest on 2007-12-08
Hi,
I have a 40 GB IDE hard disk. Created two partitions, C&D and installed Windows XP on C partition and I use D to store data.

Now I tried installing Ubuntu (Fiesty) on the remaining 14 GB free space that was available. I chose manual partition and created a ext3 partition of 12 GB and a swap partition of 500 MB. Installation went smooth and after completion, I could boot into Ubuntu and it works fine. 

But when I boot into Windows, it doest boot, it show that its starting up and doesn't go further. What could be wrong? Please suggest...Thanks

---

### Post by mikewhatever on 2007-12-08
Can you post the output of the following command > sudo fdisk -l

---

### Post by sandysandy on 2007-12-08
> **everest said:**
> Hi,
I have a 40 GB IDE hard disk. Created two partitions, C&D and installed Windows XP on C partition and I use D to store data.

Now I tried installing Ubuntu (Fiesty) on the remaining 14 GB free space that was available. I chose manual partition and created a ext3 partition of 12 GB and a swap partition of 500 MB. Installation went smooth and after completion, I could boot into Ubuntu and it works fine. 

But when I boot into Windows, it doest boot, it show that its starting up and doesn't go further. What could be wrong? Please suggest...Thanks

kindly post output of 
[COLOR="Blue"]
sudo fdisk -lu[/COLOR]

regards

---

### Post by awthomp on 2007-12-08
Edit: same as above.

---

### Post by everest on 2007-12-08
sorry, i will post it later, as i cant connect to internet with the linux...i use a dialup connection and the modem is not getting detected.
Thanks *I will post the output of fdisk -l latest by Monday

---

### Post by everest on 2007-12-09
> **mikewhatever said:**
> Can you post the output of the following command

Here is the simplified output of fdisk -l...thanks

Device boot                                   System
/dev/sda1                                    HPFS/NTFS
/dev/sda2                                    W95/Ext'd (LBA)
/dev/sda5                                    NTFS
/dev/sda6                                    Linux
/dev/sda7                                    Swap

---


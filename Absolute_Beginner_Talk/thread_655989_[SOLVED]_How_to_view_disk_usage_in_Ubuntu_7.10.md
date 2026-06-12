---
title: "[SOLVED] How to view disk usage in Ubuntu 7.10?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by onlytanmoy on 2008-01-02
Do i have any option to see my disk usage for all the partitions in my machine in Ubuntu 7.10 ? 
ike back in windows vista, if u open the explorer, it shows all the partitions with disk usage like 101 mb of 40 GB(say for C drive) , 1.2 GB of 50 GB(say for D drive) etc, ...do i have a similar option in Ubuntu also?

---

### Post by chewearn on 2008-01-02
One method:
System Monitor > File Systems tab.

---

### Post by HermanAB on 2008-01-02
Simple: df and du

---

### Post by user1397 on 2008-01-02
Applications > Accessories > Disk Usage Analyzer (for your current partition)

If you want to see all partitions, install gparted ```
sudo apt-get install gparted
``` for a nice graphical view of your partitions.

---

### Post by onlytanmoy on 2008-01-02
@ubuntuman001 >> thanks for replying bro... i wish to see all my hard disc partitions..
ubuntu is not installed in my machine..i am live booting with it..can i still use gparted to see all my partitions? plz reply..thanks.

---

### Post by user1397 on 2008-01-02
> **onlytanmoy said:**
> @ubuntuman001 >> thanks for replying bro... i wish to see all my hard disc partitions..
ubuntu is not installed in my machine..i am live booting with it..can i still use gparted to see all my partitions? plz reply..thanks.yep, in the live cd, gparted is actually installed by default.  just go to system > administration > Gparted Partition Editor or something similar.  it'll show you your partitions right away, but be careful not to erase any that you wouldn't want to erase...

---

### Post by ~LoKe on 2008-01-02
df will show this information assuming you mounted the drives.  An example of my output:
> [02:18:21 loke]$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2              9574584   4271312   4816908  47% /
varrun                 1031240        76   1031164   1% /var/run
varlock                1031240         0   1031240   0% /var/lock
udev                   1031240       112   1031128   1% /dev
devshm                 1031240         0   1031240   0% /dev/shm
lrm                    1031240     13320   1017920   2% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1            230283700 198614948  19971024  91% /home

---

### Post by kpkeerthi on 2008-01-02
Use **df -h** to see the output in **h**uman readable format :)

---

### Post by onlytanmoy on 2008-01-02
> yep, in the live cd, gparted is actually installed by default. just go to system > administration > Gparted Partition Editor or something similar. it'll show you your partitions right away, but be careful not to erase any that you wouldn't want to erase...

thanks again...i will try this out n mark this thread as Solved...will take some time though as the machine is at my home n i am at my frends place :)

---

### Post by onlytanmoy on 2008-01-03
thanks ubuntuman001...gparted is wat i was looking for, it worked like a charm :)

thank u all for replying..wish u all a very happy new year 2008..marking the thread as solved.

---


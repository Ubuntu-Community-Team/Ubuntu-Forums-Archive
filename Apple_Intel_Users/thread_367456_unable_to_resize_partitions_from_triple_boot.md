---
title: "unable to resize partitions from triple boot"
date: 2007-02-22
forum: Apple Intel Users
---

### Post by sammycitrus on 2007-02-22
So I'm completely new to the Linux scene, and I'm a pretty computer savvy person. However with no knowledge in Linux and a decent knowledge of terminal commands in OS X, I'm stuck trying to resize the three partitions i created trying to triple boot my macbook pro.

the story so far,
i figured i'd install Xp and ubuntu on my macbook pro in addition to OS X. So i followed the instructions from [https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro) . and right after creating the three partitions, as is my habit, i decided to read up more on the diskutil command. In the process i saw i had partitioned the three volumes with wrong sizes. So now i need to resize the 3 partitions.

Can someone help me with how/where i can find help in terminal level resizing? I have three partitions and rEFIt installed. rEFIT works fine, and i didnt go ahead with the XP installation or the ubuntu installation coz i wanted to size my partitions up correctly before i go ahead. Also additional help on restoring the mac HDD to a single partition without reformating the disk (and perhaps without using Carbon copy cloner) would be really appreciated.

thanks in advance...

---

### Post by tylerdurden on 2007-02-22
i tried doing the same thing when i got my macbook not to long ago (3 weeks) and i decided to scrap it... i was left with one large HFS+ (read: Mac) partition and i wanted to restore it... if you look at gparted support... u can only shrink a mac partition not grow it... i was on a mac IRC channel everyday trying to see if i could resize it without formating... they all told me it wasnt possible... i bit the bullet and reinstalled... thankfully!... i discovered Parallels and man does it work well... i have xp and ubuntu installed using parallels and fast switching is great.... plus xp and ubuntu run faster under parallels than they do as native installs on my desktop... long story short... look into parallels and reformat... i dont think u can grow HFS+ partitions...

---


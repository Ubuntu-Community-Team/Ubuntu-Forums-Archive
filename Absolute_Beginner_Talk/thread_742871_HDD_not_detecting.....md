---
title: "HDD not detecting...."
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by rajputrajat on 2008-04-02
Guys, help me out....plzzzzzzz....

I was running feisty on my home computer.....(AMD one + nvidia graphics).
then my bro installed XP on it......

But now after 3 months, i again tried to installed gutsy, i'm unable to see harddisk partition it it...
so. installation can't be done...

I tried gutsy, pclinxOS, sabayon.....same problem...:(

b/w, bindose is working fine...

what can be the reason? :confused:

---

### Post by sayakb on 2008-04-02
Did you properly shut down the Windows you had? Windows locks the HDD partitions as it uses it and unlocks it when it is properly unmounted. Try the LiveCD. Goto the terminal and type:
```
fdisk -l
```. Check the /dev/sdax (say, you have it as /dev/sda5) path from there and mount it using:
```
sudo mount -t ntfs-3g /dev/sda5 -o force
```  EDIT: This code is valid for NTFS partitions only.

---

### Post by housam on 2008-04-02
post a screen shot of your partitions using Gparted tool ( on the live cd - system >> admins. >> partition editor . )

---


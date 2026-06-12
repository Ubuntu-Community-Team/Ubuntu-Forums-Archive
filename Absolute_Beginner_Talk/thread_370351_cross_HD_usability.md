---
title: "cross HD usability"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by hendoc on 2007-02-25
I have edgy on a 40 Gb Maxtor slave. I formatted XP away on a 160 Gb WDC that is the master. Edgy sees the master HD, but won't let me access it. There must be a better way than just reinstalling to the WDC.

---

### Post by george29 on 2007-02-25
Not sure what you mean...?

you have 2 drives on a IDE channel the Wester digital is the master drive (in linux ususally hda) and the maxtor is a slave on the IDE channel (hdb).

with ubuntu installed on the maxtor that will have an Ext3 filesystem. 

what filesystem did you reformat the western digital drive to? i presume you deleted windows completed because you didn't want to keep it?

if this is the case you should type

 ```
sudo fdisk -l 
```

into a terminal this will tell you what partitions you have. 

use gparted (enable repositories and install using synaptic - refer to ubuntu guide if necessary, which can be found via a google search) to reformat to Ext3 or whichever file system you wish to use and then read the how to below which has all the information you require to mount those partitions

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by hendoc on 2007-02-25
I made hda fat 32. I will follow the link you provided and I thank you for your help.

---


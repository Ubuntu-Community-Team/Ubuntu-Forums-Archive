---
title: "Resize problemo!"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Metroid48 on 2006-11-05
Hey, I'm going to resize the Windows NTFS partition to install Ubuntu. However, there's a problemo:). Here's a picture from Diskeeper defragmentation program:

[IMG]http://img49.imageshack.us/img49/337/defragpn1.png[/IMG]

I need the entire bottom bar free to resize (think of it as having all the bars connected, like Windows defrag) but I can't move the one blue chunk. The green one's my hibernation file, I'm going to delete that. Any ideas on how I can move the files?:confused: 


-Metroid48

---

### Post by annda on 2006-11-05
oops, that seems to be a windows program! i hope somebody knows the answer, but don't expect any pros versed in numerous windows programs in this forum. i don't mean to be rude or anything, but maybe try to delete anything you don't need, defrag and use the partitioner on your ubuntu install cd.

what i mean is you will **certainly** get help on ubuntu software, and only **maybe** on win software.

good luck anyway!

---

### Post by Metroid48 on 2006-11-05
No, I ment if there's a way I can find what file(s) are located them and move them. I can use linux programs if neccessary.

---

### Post by smoker on 2006-11-05
hi, this block may be your pagefile, or system restore points, which i dont think get moved or altered during a normal defrag. you could turn off system restore to get rid of all restore points, and turn off your pagefile, then defrag in safe mode. remember to turn system restore back on again once you have defragged. and also your pagefile.

hope this helps

---

### Post by Metroid48 on 2006-11-05
No, I already disabled the pagefile (well, set it to another drive) and system files are green anyway.

---

### Post by smoker on 2006-11-05
you could let ubuntu resize your ntfs partition then, or if you want it done before doing the ubuntu install, download 'gparted' (available from sourceforge.net, i believe, create the gparted boot disk and resize your partition with it. remember to back up all your windows data before resizing.

hope this helps

---

### Post by Metroid48 on 2006-11-05
Cool, will it backup whatever files are in the location it overwrites? If so, then i'm ready to resize!

---

### Post by smoker on 2006-11-05
hi,

gparted will move the data in your windows partition to fit in the resized space. eg, if you have 5gb of used space on a 10gb partition, and you reduce this to 7gb, gparted will move data so that the 7gb partition holds the 5gb of used space. there is always a risk resizing a partition with a lot of data on it, this is why it is important to make a back up, just in case...:mad: 

i have used gparted many times though, and luckily have never had any mishaps with it:D 

hope that answers your question

---


---
title: "ForExperts:Possible to make a automatic e2fsck reparing when I boot up my Linux PC?"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-01-15
```
e2fsck and put option : 
automatic repair & force the checking even if clean 
```
  
I have a script running at my startup ... 
When /etc/rc2.d/SxxE2FSCKautoRepair
  
What value of xx should I put ??
  Which level should be used in order to fix automatically my /dev/hda ??
  
Thank you very much

greetz

pat

---

### Post by Kyral on 2006-01-15
It shouldn't be needed. Ext2/3 FS's are automatically checked every (I think 36 is the default) mounts. You can of course change this with tune2fs :D

---

### Post by patrick295767 on 2006-01-15
I would like to do a :
```
e2fsck -p -f /dev/hda2
```
  each time I reboot my server
  
Which number zz should I use ?
(in /etc/rc2.d/SzzCheckit.sh)
  
U've any idea cos if it's 99, it's too late cos everthg is mounted & used by linux like crazy
... 
too much risks ... 
  
I'll try tune2fs...
  
thank you

---


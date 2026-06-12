---
title: "How to Add Leopard in Grub"
date: 2008-06-14
forum: Apple Hardware Users
---

### Post by ankitguptag18 on 2008-06-14
hi,

I had Leopard installed on my Laptop for past 3 months, 
suddenly my Leopard partion (hd0,4) is missing from the grub 
can any ony say me what to do

I tried 

title		Leopard
root		(hd0,4)
savedefault
makeactive
chainloader	+1
quiet

but it didnot work.

I am Using UBUNTU 7.10

---

### Post by PmDematagoda on 2008-06-14
Post the output of:-
```
sudo fdisk -l
```

---

### Post by meierfra. on 2008-06-14
I don't know  anything about booting "Leopard". But I know that "makeactive" applied to a logical partition causes Grub Error 12. So I suggest to remove the "makeactice".

Make sure that your Leopard item is below the line

### END DEBIAN AUTOMAGIC KERNELS LIST

otherwise it will disappear after the next kernel update.



Also, you should not start more than one thread on the same subject.

---

### Post by Sef on 2008-06-14
Locked: [Duplicate Post]("http://ubuntuforums.org/showthread.php?p=5184447#post5184447").

---


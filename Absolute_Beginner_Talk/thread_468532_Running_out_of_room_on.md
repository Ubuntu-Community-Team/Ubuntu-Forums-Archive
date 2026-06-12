---
title: "Running out of room on /"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by ubu_n00b69 on 2007-06-08
I have a 110GB HD. I used 10.91 for \ and 94 for media.
I am 95% full on \ and I cant seem to figure out how to make some more space available on \.

Any help would be appreciated.

---

### Post by tahuya_rat on 2007-06-08
Ok, if you don't already have it installed,  then type into a terminal:

```
sudo apt-get install gparted
```

Once it's installed, then just type:

```
gparted
```

and then, just do what you wish with the HD.



HTH.

-tahuyarat

---

### Post by ubu_n00b69 on 2007-06-09
GPARTED wont let me resize any of the partitions

---

### Post by yurimxpxman on 2007-06-09
> **ubu_n00b69 said:**
> GPARTED wont let me resize any of the partitions
That's because you have them mounted. Use your Ubuntu LiveCD to do it.

However, I'm 95% certain you cannot resize a bootable ext3 partition.

---

### Post by ubu_n00b69 on 2007-06-09
Lets give it a shot...Thanks

---

### Post by 444 on 2007-06-09
You'll be able to expand your bootable partition fine. It's the shrinking the the second one that's the problem. With ext3 you can stretch or shrink the ending of a partition however you want but you can't move the start, unless you copy the whole thing at once.

---

### Post by tahuya_rat on 2007-06-09
> **yurimxpxman said:**
> That's because you have them mounted. Use your Ubuntu LiveCD to do it.

However, I'm 95% certain you cannot resize a bootable ext3 partition.

Yeesh!  Never tried it, part of me hopes you're wrong, and part of me hopes you're right, I might need to do this someday...:p

---


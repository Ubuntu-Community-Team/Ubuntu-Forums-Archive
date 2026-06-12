---
title: "too much swap"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by snake444 on 2007-08-13
i have 700 mb of swap how can i remove from it 500 mb and add them to the ubuntu?

---

### Post by por100pre1 on 2007-08-13
Before answering...  Is the Ubuntu partition(s) next to the swap partition?  How many primary partitions do you have?

---

### Post by ramjet_1953 on 2007-08-13
Also, how much RAM do you have?

Up to 1GB it's a good idea to have twice your RAM, if you want to hibernate.

Regards,
Roger :cool:

---

### Post by snake444 on 2007-08-13
i have only two partitions
1 partition that is the ubuntu and its 39~ gb
and another one partition that is the swap that is 700 mb

---

### Post by por100pre1 on 2007-08-13
I think you can delete your swap partition and increase your ubuntu partition, then you can create a new swap partition on the remaining space, I think.:-k But it's a good idea to keep that swap size intact, you could need it someday. :) Sorry for my delay, I was very busy.

---

### Post by snake444 on 2007-08-13
and how to remove the partiotion??
and i dont want to keep .. 700mb is too much

---

### Post by skymera on 2007-08-13
```
 sudo apt-get install gparted 
```

delete wiothj that

---

### Post by bodhi.zazen on 2007-08-13
Better to manage your partitions with a live CD.

You can unmount the swap partition and delete tit if you are running from your hard drive, but you will not be able to add the space back to Ubuntu if it is mounted (thus the reason to do it from a live CD)

You can do this with the ubuntu desktop CD as it already has gparted.

You will need to unomount swap (both commands in a terminal) :

```
sudo swapoff  </dev/hdxy>
```

and run gparted as root :

```
gksudo gparted
```

---

### Post by yorkie on 2007-08-13
please note that if you remove swap partition it could end up making your PC/LAPTOP run slower best to keep some swap patition

---


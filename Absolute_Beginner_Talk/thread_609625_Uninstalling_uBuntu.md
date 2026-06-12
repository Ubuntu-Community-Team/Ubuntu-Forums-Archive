---
title: "Uninstalling uBuntu"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Code1026 on 2007-11-11
Hello guys,

I have installed uBuntu a month ago on the same partition that has Windows XP installed on (stupid I know). Anyway, I want to uninstall uBuntu, create a new partition and have it installed again so I finally start experimenting and learning it.

Help, tutorials are all welcomed!

Thank you in advance,

Code1026

---

### Post by skymera on 2007-11-11
so you over wrote XP?

---

### Post by bulldog on 2007-11-11
Or did you use Wubi?

---

### Post by TadH on 2007-11-11
i think he is saying he has ubuntu and windows on the same partition.

---

### Post by bulldog on 2007-11-11
> **TadH said:**
> i think he is saying he has ubuntu and windows on the same partition.

Yes I know,your problem is solved btw,look for the answer in your topic :)

I had a simular question last week and he had installed with Wubi,which obviously created a folder within windows,so I'm told.

---

### Post by Code1026 on 2007-11-13
Yes this is the problem I am facing (As Tad mentioned)

Can anyone link me to the topic where this problem was solved?

Thank you :mrgreen:

---

### Post by bulldog on 2007-11-13
It wasn't your problen what was solved,but from TaDh.:)
Can you give me the output of ```
sudo fdisk -l
```from a terminal?

You should know windows uses NTFS or FAT filesystem and ubuntu ext3,so I have my doubts that they are on the same partition.

---


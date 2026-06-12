---
title: "delete unallocated space"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by tbluhp on 2006-11-04
Hi I have a unallocated 8GB that I created by resizing my hd in ubuntu from 38GB down to 30GB and it created that unallocated space how do I get rid of the unallocated space and gain back my 8GB?

---

### Post by Portable_Jim on 2006-11-04
A few questions:

1. Is the parition you are trying to resize your main partition.?
2. When and how did you resize it in the first place (from 38GB to 30GB)?
3. What version are you using (Breezy, Dapper, or Edgy)?

If you could answer these questions it would greatly assist in solving your problem.

---

### Post by tbluhp on 2006-11-04
> **Portable_Jim said:**
> A few questions:

1. Is the parition you are trying to resize your main partition.?
2. When and how did you resize it in the first place (from 38GB to 30GB)?
3. What version are you using (Breezy, Dapper, or Edgy)?

If you could answer these questions it would greatly assist in solving your problem.
1. Is the parition you are trying to resize your main partition.?
Yes from my internal hd
2. When and how did you resize it in the first place (from 38GB to 30GB)?
From ubuntu's live cd partion tool it was couple hours ago.
3. What version are you using (Breezy, Dapper, or Edgy)?
Edgy 6.10

---

### Post by Sef on 2006-11-04
What are you thinking of doing with the unallocated space?

As for partitioners, I would use [GParted]("http://gparted.sourceforge.net/").

---

### Post by tbluhp on 2006-11-04
> **Sef said:**
> What are you thinking of doing with the unallocated space?

As for partitioners, I would use [GParted]("http://gparted.sourceforge.net/").

I want to get rid of it have only one partion and that is for my OS not ubuntu. I can only use the live cd version of ubuntu so I need to erase/undo the unallocated space that I created.

Gparted is on the linux live cd that is what I used.

---

### Post by Portable_Jim on 2006-11-04
You will need to boot using the live CD then resize the partition (like you did when you enlarged the partition.)

Shrinking a Linux partition can result in a loss of data. You can find more info by searching the forums.

[ Please forgive me  (and my quick answer) because I have to leave the forums for a while. I will be back to help you sometime later.]

---

### Post by tbluhp on 2006-11-04
> **Portable_Jim said:**
> You will need to boot using the live CD then resize the partition (like you did when you enlarged the partition.)

Shrinking a Linux partition can result in a loss of data. You can find more info by searching the forums.

[ Please forgive me  (and my quick answer) because I have to leave the forums for a while. I will be back to help you sometime later.]
I tryed that and it will not let me go from 30GB to my orignal state wich is 38GB? It will not let past 30GB?

---

### Post by tbluhp on 2006-11-04
> **Portable_Jim said:**
> You will need to boot using the live CD then resize the partition (like you did when you enlarged the partition.)

Shrinking a Linux partition can result in a loss of data. You can find more info by searching the forums.

[ Please forgive me  (and my quick answer) because I have to leave the forums for a while. I will be back to help you sometime later.]

All I need to know is how to get rid of the 8GB space and have my one and only partion back to 38GB

---

### Post by Portable_Jim on 2006-11-05
Sorry, I was confused at the time of writing. I now understand.

Can you resize the partition at all? (from the Live CD)

---


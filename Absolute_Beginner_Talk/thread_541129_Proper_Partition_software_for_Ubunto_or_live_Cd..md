---
title: "Proper Partition software for Ubunto or live Cd."
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by dr_kaufman on 2007-09-02
Hi people of this great forum, I'm an absolute begginer in this linux thing so I screwed up a bit, I hope you comprehend and help me!

So, the problem is about the partitions (Windows & Ubuntu) more likely the windows partiton, that I limited with a 600 MB free space witch isn't acceptable of course and the ubuntu partition has about 80 GB witch is a lot since I'm only experiencing it. 

While I was googling I've found the Gparted software, I read the functions I I though "Hey, this is what I am looking for" but...

I burnt the cd, boot it and limited the linux partition to 25 GB creating an empty one with 60 GB, the problem starts here, I have an empty partition but, with this software, I can't resize/enlarge the windows one using the empty parttn. 

**So, if you know a ubuntu software that manages to enlarge a partition using other, I'll be very happy to know!** (I said linux soft and not win soft because windows is unaccessible) a bootable, live cd program is also a choice.

Here what it should like if you didn't get the point of the text:

Right now:

1 NTFS (Windows) 52 GB
2 Linux-Swap
3 NTFS (Data) 80 GB
4 Ext3 (Linux) 25 GB
5 NTFS (empty) 60 GB

Then it should look like this!

1 NTFS (Windows) 110 GB
2 Linux-Swap
3 NTFS (Data) 80 GB
4 Ext3 (Linux) 25 GB


I hope you understand my problem & thank you.

Stay cool!

---

### Post by Wynne G Oldman on 2007-09-02
You could use "Boot It NG" to resize your partitions. I can't remember where I downloaded it from, but I'm sure that you could find it with Google.

---

### Post by mikewhatever on 2007-09-02
> Right now:

1 NTFS (Windows) 52 GB
2 Linux-Swap
3 NTFS (Data) 80 GB
4 Ext3 (Linux) 25 GB
5 NTFS (vazia) 60 GB
There seems to be no empty partition next to the Windows one. Which one is the empty one, 3 or 5? 
> ...and the ubuntu partition has about 80 GB witch is a lot...
Also, where is the Ubuntu partition the size of 80 GB?

---

### Post by dr_kaufman on 2007-09-02
> **mikewhatever said:**
> There seems to be no empty partition next to the Windows one. Which one is the empty one, 3 or 5? Also, where is the Ubuntu partition the size of 80 GB?

It is the 5th one.

I had the Ubuntu partition with the size of 80 GB and resized, using GParted, to about 25 GB creating the 60 GB empty one.

The problem is that I canot enlarge the windows partition with that software so I need another.

Thank you once again.

Sorry about my english.

---

### Post by mikewhatever on 2007-09-02
Is this all on a single HDD, or is '3 NTFS (Data) 80 GB' a separate one?

---

### Post by dr_kaufman on 2007-09-02
> **mikewhatever said:**
> Is this all on a single HDD, or is '3 NTFS (Data) 80 GB' a separate one?

Yes, only one HDD.

---

### Post by meierfra on 2007-09-02
you can do  it with gparted. The trick is that you can only use unallocated space next to a partition to increase a partition. So this is what you need to do:

Delete partition 5 (NFTS, empty 60 GB)

Increase partition 4 by 60 GB.

Decrease partition 4 by 60 GB leaving the unallocated  space before partition 4.

Increase partition 3 by 60 GB.

Delete swap. 

Decrease partition 3 by 60 GB leaving the unallocated  space before partition 3

Increase partition 1 by 60 GB.

Format swap from the remaining unallocated space.

---

### Post by meierfra on 2007-09-02
I fixed a typo in my post. Also I'm not sure whether this is a good way to do it, since it does lots of resizing.  Maybe where are other programs which can do it easier, but I don't know.

---

### Post by dr_kaufman on 2007-09-02
ok, I'll wait for some more answers before I try that one!

---

### Post by mikewhatever on 2007-09-02
Had the empty partition been next to the Windows one, deleting it and incorporating the unallocated space to Windows would have been an easy task. The problem is, there are three other partitions between the one with Windows and the empty one. I have no idea how you ended up with such a set up, nor how to alter it to the one you want without deleting all but Windows partition. That said, I am no expert, perhaps there is a way. Here is a link to GParted documentation [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---


---
title: "Install of V6.06.1 fails"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by rfrisbee on 2006-09-02
:-\" So.....

Under winXP I partition a secondary drive into 3 partions all ntfs.  The two for Ubuntu are ~70GB (for /) and ~5GB (for swap).  Check files on the burned CD, all ok.  Boot Ubuntu from CD, run install:
1) specify 70GB part as / and 5 GB as root
2) Indicates "ready to install"
3) "installing system"
4) "starting partitioner"
5) Install program terminates with no info?

I think it is failing during the format.  When I reboot winXP, it wants to run scandisk.

Any suggestions?

---

### Post by nrwilk on 2006-09-02
> **rfrisbee said:**
> :-\" So.....

Under winXP I partition a secondary drive into 3 partions all ntfs. The two for Ubuntu are ~70GB (for /) and ~5GB (for swap). Check files on the burned CD, all ok. Boot Ubuntu from CD, run install:
1) specify 70GB part as / and 5 GB as root
2) Indicates "ready to install"
3) "installing system"
4) "starting partitioner"
5) Install program terminates with no info?

I think it is failing during the format.  When I reboot winXP, it wants to run scandisk.

Any suggestions?

ubuntu cannot run on an ntfs partition. in fact, Linux support for writing to NTFS is very new and buggy. There are several programs which attempt it, but i don't think any are perfect yet.
 
 ubuntu by default uses ext3, but you could use fat32 or reiserfs too.
 
 Also, 5GB is WAY too much space for swap.  I recommend not using more than 1GB at the very most.


> **rfrisbee said:**
>  1) specify 70GB part as / and 5 GB as root

/ *is* root.  I assume this is a typo?  Did you mean swap instead of root?

---

### Post by rfrisbee on 2006-09-02
As part of the install, I specify reformat with a check beside the partition.  I think it is failing at that point.

---

### Post by nrwilk on 2006-09-02
EDIT: deleted double post.  Sorry! #-o

---

### Post by rfrisbee on 2006-09-02
sorry,  should be / (root) and swap

---

### Post by nrwilk on 2006-09-02
> **rfrisbee said:**
> sorry,  should be / (root) and swap


Did you see the rest of my post?  The part about ubuntu not being able to use ntfs.

---

### Post by rfrisbee on 2006-09-02
Yes, but during the install, i selected the checkmark beside each partion (root and swap) to format before proceeding.  I assume ther e is no problem formatting over ntfs.

---

### Post by nrwilk on 2006-09-02
> **rfrisbee said:**
> Yes, but during the install, i selected the checkmark beside each partion (root and swap) to format before proceeding.  I assume ther e is no problem formatting over ntfs.
I'm sorry, I thought you were saying that you'd formatted them AS ntfs.  What filesystem did you specify to format them as, then?

---

### Post by rfrisbee on 2006-09-02
in the Ubuntu install program there is no option to specify the format when you check format beside the partition.  I assume it uses ext3.

---

### Post by nrwilk on 2006-09-02
> **rfrisbee said:**
> in the Ubuntu install program there is no option to specify the format when you check format beside the partition.  I assume it uses ext3.


Right, but you said that you partitioned it "under WinXP."

Did you do a checksum of the iso you downloaded before you burnt it?

---


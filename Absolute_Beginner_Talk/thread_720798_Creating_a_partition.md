---
title: "Creating a partition"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by conrad1975 on 2008-03-10
I installed Ubuntu 7.10. I have 70 gig hard drive ,but i only create a 35 gig partition when i done the installation. I would like to create another 
35 gig partition with the rest of the hard disk. How would you do this and will i loose the all the information on the existing partition. I am still new to ubuntu.

---

### Post by p_quarles on 2008-03-10
Moved to Beginner Talk.

I think you are misunderstanding what a partition is. If the remaining 35 GBs actually haa data on it, then it is already a partition. And, yes, creating a new partition on that space would format the partition, eliminating any data that was there.

---

### Post by melopsittacus on 2008-03-10
Hi, use gparted (you can get it with Applications-->Add/Remove)
You can perform the partitioning of free space without losing any data on the other partition.

[edit]
This applies if I understood the situation correctly, that is:
one 35GB partition with Linux system installed on it
35GB of free space

if there is no free spce, but another 35GB partition instead, you will lose any data on it by formatting it, as p_quarles  has said

---

### Post by ruy_lopez on 2008-03-10
Install "gparted":

```

sudo apt-get install gparted

```

Once installed, Navigate: System->Administration->Gnome Parition Manager. The free space will appear as a grey block. Select the unallocated space. Choose "partition"->"new" from the menubar.

Make the partition the size you want, choose ext3 as the type. Then apply your changes. Take note of the device "/dev/hdaX" or "/dev/sdaX" (X is a number).

Once you have created the partition.

Create a mountpoint: (replace "newpartition" with the name you want to give the partition).
```

sudo mkdir /media/newpartition

```

Mount the partition: (replace /dev/hdaX with device gparted used).
```

sudo mount -t ext3 /media/newpartition /dev/hdaX

```

Change the mountpoint ownership (replace yourname with your username):
```

sudo chown yourname:yourname /media/newpartition

```

Add a line to /etc/fstab, to automatically mount on boot:
```

/dev/hdaX       /media/newpartition       ext3        defaults        0       0

```

Good luck

---

### Post by gecko113 on 2008-03-10
Also if u are new to Ubuntu still use Gparted but run it off the live cd its much easier to use like if u wanted to u can wipe ur whole computer out and partion it that way so that u kno wat is what and also it very simple to use. If u ran it from linux u wouldn't be able to touch the Ubuntu partion on ur harddrive (which i'm pretty sure of) but if so then ur good if not run of a live cd of gparted its the best way to go :) good luck to u

---

### Post by ruy_lopez on 2008-03-10
> **gecko113 said:**
> Also if u are new to Ubuntu still use Gparted but run it off the live cd its much easier to use like if u wanted to u can wipe ur whole computer out and partion it that way so that u kno wat is what and also it very simple to use. If u ran it from linux u wouldn't be able to touch the Ubuntu partion on ur harddrive (which i'm pretty sure of) but if so then ur good if not run of a live cd of gparted its the best way to go :) good luck to u

The OP doesn't want to touch his Ubuntu partition. He wants to use the free space. Using Gparted from Ubuntu will allow him to create a new partition **if** the space is unallocated. It will also prevent him from ruining his Ubuntu partition.

In this case, using the LiveCD (something I usually suggest), won't prevent him from ruining his Ubuntu installation.

---


---
title: "Help with partition"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Dannybzr on 2007-02-20
Hello all,

I would love to get some help on this one, I have hit a wall as far as my ubuntu install is going.

I partitioned my harddrive using PartitionMagic last night, I created an Ext2 partition that is 6gig in size and created a swap file that is 500mb in size.

When I open PartitionMagic it shows me 3 partitions, 1 with windows on it that is active, 2 then are the swap file for ubuntu and the 6gig Ext2 partition they are being displayed in not being active.

What I would like help with is how I go about installing ubuntu from here?? What steps that I need to look out for etc. 

Taking into account that this is my very first experience with partitioning and also installing a new OS, which is linux based. I am not familier with deleting or merging of partitions either, and I am not aware of the pitfalls to look out for.

Thanks in advance for all the help, it is much appreciated. Any other required information can be givin

Regards

Danny

---

### Post by Bachstelze on 2007-02-20
Download an Ubuntu install CD, boot from it and follow the instructions :)

---

### Post by Dannybzr on 2007-02-20
> **HymnToLife said:**
> Download an Ubuntu install CD, boot from it and follow the instructions :)

But I am afraid that it will try and overwrite my windows Xp partition which is what I dont want.. I want to be able to dual boot my system from startup.

---

### Post by indytim on 2007-02-20
If you want to pre-configure the partitions prior to installing, you should be using ext3 and not ext2.

With respect to your concern about blowing away your Windows install, just pay close attention during the install.  When it comes to the part re. where to install your new U-Kbuntu, make sure you DO NOT SELECT the option to install across the entire h/d.  If you have pre-configured your partitions, select the option to select where the ops system will be installed.  My apologies for lack of exact wording as I'm at work and not accessible to the Live CD.

Hope this helps.

IndyTim

---

### Post by Dannybzr on 2007-02-20
> **indytim said:**
> If you want to pre-configure the partitions prior to installing, you should be using ext3 and not ext2.

With respect to your concern about blowing away your Windows install, just pay close attention during the install.  When it comes to the part re. where to install your new U-Kbuntu, make sure you DO NOT SELECT the option to install across the entire h/d.  If you have pre-configured your partitions, select the option to select where the ops system will be installed.  My apologies for lack of exact wording as I'm at work and not accessible to the Live CD.

Hope this helps.

IndyTim


So if I boot from the live cd, and once that loads hit the install icon on the desktop on the cd and as long as I install it to the partition that I have created, it should re configure the partition for me and leave my windows partition as is, with altering it.??

---

### Post by Dannybzr on 2007-02-22
Bump anyone care to answer my last question

---

### Post by mikewhatever on 2007-02-22
Yes that should be the case. I assume you meant 'without altering it'.

---

### Post by Dannybzr on 2007-02-22
> **mikewhatever said:**
> Yes that should be the case. I assume you meant 'without altering it'.


Sounds goods, thanks very much.................:guitar:

---

### Post by bodhi.zazen on 2007-02-22
You may have a problem with your partitions in that partition magic does not always work well with Linux.

If this is the case, delete all but windows partition, boot the ubuntu CD, and partition from Ubuntu rather then partition magic :p

You will be able to install without damage to your windows install most of the time. With that said, however, you should back up you data first just in case.

Here is a nice install guide : [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

HTH 8)

---


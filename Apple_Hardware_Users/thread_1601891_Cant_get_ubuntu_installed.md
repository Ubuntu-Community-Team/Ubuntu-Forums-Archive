---
title: "Cant get ubuntu installed"
date: 2010-10-20
forum: Apple Hardware Users
---

### Post by camiloorozco on 2010-10-20
Ive been trying to install ubuntu on my macbook pro for days but it wont work, im trying using rEFIT and its great until its copying files and then it says errorno5 because there was a problem copying the files. My hardrive is also getting tons of partitions that i cant delete using diskutil and its starting to bug me.

any help would be appreciated

---

### Post by pc_michael on 2010-10-21
Hi!

[Use this guide](https://help.ubuntu.com/community/MacBookPro), it will walk you through installing Ubuntu on your Macbook Pro.

First, you should probably delete all the extra partitions that are being made(?).  Disk Utility in Mac OS X is unable to manipulate Linux partitions, so you can boot into your Live CD and use Gparted (under System > Administration) to remove those partitions you say are being created.

I am unclear about these partitions though--is it rEFIt creating these partitions?  Or the Ubuntu installer?

---

### Post by camiloorozco on 2010-10-29
the ubuntu installer is creating the partitions, ive tried opening gparted from the live cd  but it always crashes, i tried the link to my computer on that guide but it just opened a page to help users that had already installed it.

---


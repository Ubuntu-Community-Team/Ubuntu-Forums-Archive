---
title: "help creating new partition with GParted"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by rahul_bhise on 2007-07-14
i had a 80gb hdd. in windows xp i partitioned it to 4 equal parts of 20 gb C, D, E & F.
before moving to ubuntu i moved all my data from e to f.
then i made a partition of 10 gb in e (using a live cd of ubuntu) 
now i want to make another partition in e (what is remain of it) for storing my work done in ubuntu.
what i am going to do is (see the screen shot of my GParted) whit help of gparted.
1> shrink the /dev/sda6 (remaining of e) from right side
2> move /dev/sda8 (my ubuntu partition)to left of newly created unallocated partition
3> formate the newly created partition to ext3

so my question is that is this the right way of doing for what i have in my mind.
and i am going to do this when i am logged in my first user name i created while installing ubuntu from live cd

---

### Post by earobinson on 2007-07-14
I would use the live cd to shrink sda6 (since that is your working partition as I understand it and you wont be able to shrink it when your using it) but other than that yup that sounds correct

Let us know how it goes!

---

### Post by rahul_bhise on 2007-07-14
> I would use the live cd to shrink sda6 (since that is your working partition as I understand it and you wont be able to shrink it when your using it)
no this is remaining E:/ after partition for ubuntu

---

### Post by macogw on 2007-07-14
Ubuntu doesn't use C:\ E:\ and whatever.  Those are Windows's names for them.  /dev/sda refers to the first SATA or SCSI drive.  /dev/hda refers to the first IDE drive. /dev/sdb would be second SATA, /dev/hdb would be second IDE.  The first partition on a the first SATA drive is /dev/sda1.  What earobinson is referring to is the 6th partition on your hard drive: /dev/sda6

---

### Post by earobinson on 2007-07-14
oops nevermind then
/blush

---

### Post by rahul_bhise on 2007-07-15
> **earobinson said:**
> oops nevermind then
/blush

does that means i can proceed the way i have firstly decided.
as are you for** sure**, that nothing will go wrong with me.

---

### Post by earobinson on 2007-07-17
> **rahul_bhise said:**
> does that means i can proceed the way i have firstly decided.
as are you for** sure**, that nothing will go wrong with me.
Well things should work yes, we can never be sure, make sure to back up any important data on the partition you will be resizing but things should work so yes.

Let us know how it goes.

(the way I suggested would have worked it would have just taken longer)

---

### Post by rahul_bhise on 2007-07-18
> **earobinson said:**
> (the way I suggested would have worked it would have just taken longer)
this made me change my mind and i used gparted in live cd
making the partition was easy, though it gave me lots of error after i click **APPLY **and then **ACCEPT**. i still kept on continuing my further steps.
Then i restarted (without live cd) and logged in to see all was all right.(so it was)
then i copied my home folder to the new partition (thanks to [http://www.psychocats.net/](http://www.psychocats.net/) )
and everything worked well (*tho my default setting, sessions, firefox addons and extension are all gown. and dont know what happened to all my downloaded and installed software* ) but thats not a serious problem.
**thanks earobinson for sharing your expertise**

---


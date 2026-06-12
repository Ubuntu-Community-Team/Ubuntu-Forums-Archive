---
title: "Can I repartition my filesystem drive into two drives?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Galactic Jack on 2007-02-06
I want to repartition my filesystem into two partitions, one being a storage partition and the other being for applications and things like that. it's an 80GB HD [works out to like 72 after the overhear and filesystem] My goal is to have the filesystem partition being like 8-10 GB and the rest being the other partition.

I currently have gparted installed so I can used the GUI on that program fairly effectively, I'm just afraid it'll wipe out anything currently on my desktop.

So I'm more wondering if this is in anyway possible [as I know Linux is capable of extending boundaries and uses of certain applications foar more than Windows can]

GJ

---

### Post by xpod on 2007-02-06
If your talking about splitting your current partition then you`ll need to use gparted on your Ubuntu live cd or go download and burn the gparted live cd to do any partitioning.

You cant change a partition your actually using without first unmounting it so you need to use one of the above options i believe.

Sorry if iv`e picked you up wrong but thats what it sounds like you want to do.

---

### Post by bodhi.zazen on 2007-02-06
Sure can do, very easy

However, you will need to re-partition from a live cD as you can not resize a mounted partition (in this case you Ubunt root)

Either use the desktop CD or download gparted :

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Now resize your Ubuntu root partition. I would go 10-15 Gb but you can likely go as small as 5 Gb if you wish ...

make the rest into a data partition ...

You will then need to edit /etc/fstab on your ubuntu root partition

```
gksudo gedit /etc/fstab
```

Add something like this:```
/dev/hda2 /media/data auto defaults 0 2
```

Then, in a terminal:```
sudo mkdir /media/data
sudo mount /media/data
sudo chmod root:user /media/data
sudo chmod 770 /media/data
```

Call the mount point what you will :)

Also see here:

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

---

### Post by Mba7eth on 2007-02-06
check [ this]("http://www.ubuntuforums.org/showthread.php?t=335544")  \\:D/

---

### Post by meng on 2007-02-06
and:
[www.psychocats.net/ubuntu/separatehome](www.psychocats.net/ubuntu/separatehome)

good luck!

---

### Post by Mba7eth on 2007-02-06
Wooow I just wrote this and submet .. And 2 other already did :) 

[COLOR="Red"]I LOVE UBUNTU[/COLOR]

---

### Post by kbudurka on 2007-02-06
I am more curious as to why you want to partition.
If you want to be able to wipe out dapper (or whatever) in the future and be able to reload with no issues, then create a partition for /home. Other then that, only the swap partition needs to be different.

If you running a big system with multiple users, you might want separate partitions for /var and  /home, but I'm not sure what you need or want to accomplish.

---

### Post by ingo on 2007-02-19
and just to plug my own howto - have a look at the first link of my signature :)

---


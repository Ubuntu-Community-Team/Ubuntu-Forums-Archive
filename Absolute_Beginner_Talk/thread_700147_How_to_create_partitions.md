---
title: "How to create partitions??"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by v.cube on 2008-02-18
How to create extra partitions after install? I want my work to be saved even when i format the partition on which Ubuntu is installed?

---

### Post by viciouslime on 2008-02-18
You can install gparted from synaptic to graphically manage partitions. It sounds like you want to make a separate home partition.

---

### Post by jan quark on 2008-02-18
before thinking about partitioning make a backup of your important data now :)


you can use the gprated live cd to created new partitions

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by nilarimogard on 2008-02-18
And if you want to make changes to your root partition, you have to use the gparded iso, burn it on a CD and boot from it (just google for gparted iso).

---

### Post by geo909 on 2008-02-18
> **jan quark said:**
> before thinking about partitioning make a backup of your important data now :)

+1 to this, do not skip!!

---

### Post by housam on 2008-02-18
After using Gparted tool to create a new partition, read [[COLOR="black"][COLOR="black"][COLOR="Red"]this guide [/COLOR][/COLOR][/COLOR]]("http://www.psychocats.net/ubuntu/separatehome"). it'll help creating /home partition

---

### Post by candtalan on 2008-02-18
I do not go quite as far as making a separate  home partition, I use a large size partion for my 'data', and then use it when I want.

---

### Post by oedha on 2008-02-18
> **candtalan said:**
> I do not go quite as far as making a separate  home partition, I use a large size partion for my 'data', and then use it when I want.

you're right......
but different people different styly...and have different opinion....
i think......separated home.....if you use linux only
yours.....depend on your style
mine......just like yours....but ntfs.......:)

---

### Post by v.cube on 2008-02-18
thx everybody. but how to access gparted?? i can't see it in the applications area?

---

### Post by stchman on 2008-02-18
> **v.cube said:**
> How to create extra partitions after install? I want my work to be saved even when i format the partition on which Ubuntu is installed?

Yes, I do the same thing.  I have a partition called storage.  I mount it in the /media folder as their will be an icon on my desktop.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

You will need to install Gnome Partition Editor (gparted) and then you can graphically create partitions.  If you have one big partition you will need to use the LiveCD.

---

### Post by housam on 2008-02-19
> **v.cube said:**
> thx everybody. but how to access gparted?? i can't see it in the applications area?

boot from ubuntu  live cd , then system >> administration >> Gparted

---


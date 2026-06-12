---
title: "How to move /home to a directroy on a seperate partition"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by skroops on 2007-12-30
I have a software raid on /dev/md0.

I would like to make my /home folder on this partition, but I do not want to mount the entire raid as /home.  I have the raid automounted in fstab as /raid

What I tried was:

rsync -aS /home /raid/home
mv /home /home.back
ln -s /raid/home /home

That worked, however it caused some unfortunate side effects, such as my terminal windows now being titled "leroy@localhost" instead of "leroy@cecil".  I just reinstalled because it seemed to cause some problems with mythtv-backend as well.

What is the best way to accomplish what I am describing here?  I want /home to be on the raid, and I want my mythtv recoridings on the raid (like at /raid/myth) but I don't want all my mythtv recordings and other things to be in the /home folder

---

### Post by Vixis on 2007-12-30
read this:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by skroops on 2007-12-30
Thanks, but as I said, I don't want to mount the raid as /home

To further clarify, I want /home to be a _directory_ on the raid, probably at /raid/home.  I want this to be transparent to the user.

---

### Post by blueridgedog on 2007-12-30
Logic:

home has to be a volume mounted as /home or on a volume mounted at a parent location.

There is only one parent location of /home, that is /.  

Your raid array then needs to be mounted as / to implement what you want, but since it is a software array, it can not be.  

We are then back to it can be mounted as /home.

---

### Post by skroops on 2007-12-30
That stinks, I guess I'll have to do it differently then.
Thanks for the explanation.

---

### Post by oc3an on 2008-01-30
Have you tried mount --bind?

---

### Post by MoToR on 2008-01-30
I'm thinking about the same problem right now.

I dual-boot Vista and ubuntu. It's basic to have at least two separate partitions for Windows to be able to reinstall easily. So had four primary partitions - two NTFS for Windows, one for ubuntu and one for ubuntu swap.

Now it seems to me like a good idea to have /home at a separate location, to make ubuntu reinstallation easier as well and I'm thinking - is there a way to stay with four partitions only and have /home on an NTFS partition in a folder or something or I do I have to make one partition Extended and add a logical drive for /home?

---


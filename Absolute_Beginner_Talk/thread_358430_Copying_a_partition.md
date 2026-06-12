---
title: "Copying a partition"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by blueoyster on 2007-02-10
I have recently recieved a new hard drive and I would like to move the contents of my /home ext3 patition onto a new patition on the new hard drive. 

is there a way i could do this?

---

### Post by ardchoille42 on 2007-02-10
You can use Part Image to copy a partition to an image and then use Part Image to restore it to the new drive. Part Image is in the repos, but I keep a copy of [http://www.sysresccd.org](http://www.sysresccd.org) around for various tasks since it has a lot of admin tools on it.

I recently used Part Image to image my root partition, which was 2.5Gb, and PI shrank it down to 849Mb. I then burned that image to a DVD and resotred it to a new drive using Part Image, the whole process took about 12 minutes. PI only copies the used bits of a partition instead of the entire partition like dd does.

---

### Post by blueoyster on 2007-02-10
thanks, i will try that.

just to make sure, i does not involve burning the image to a cd and then from the cd restoring to the new partition, though you can if you want to, correct?

---

### Post by blueoyster on 2007-02-10
how do i unmount my /home partition.
when i try to sudo umount it i get an error that that device is in use.

---

### Post by ardchoille42 on 2007-02-11
> **blueoyster said:**
> how do i unmount my /home partition.
when i try to sudo umount it i get an error that that device is in use.

You can't unmount /home while you are logged in. You'll either need to use recovery mode, or use that LiveCD

What partimage does is take a partition of your choice, tar up the used bits into a tarball and save that tarball to your choice of location. Then you can do with that tarball what you want. I usually burn the tarball image to a cd or dvd and take that cd/dvd to a new machine and use partimage to restore that partition on the new machine. It's quick and does a good job without messing with the unused portion of the partition. In other words, if you have a 300Gb patition, but you're only using 2.8 Gb, partimage will tar the 2.8Gb up and leave yo with a tarball of about 900Mb.

I have /dev/hda (my ubuntu installation) and /dev/hdb, my storage drive. I have partimage tar up /dev/hda and save it to /dev/hdb. You can also do that with two different partitions on the same drive. The rule is, though, that you can't mount the partition that you are copying, but you must mount the partition where you are saving the image.

---

### Post by aysiu on 2007-02-11
I second the motion for PartImage.

If you don't have the SystemRescue CD, you can use the Ubuntu CD:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by ardchoille42 on 2007-02-11
> **aysiu said:**
> I second the motion for PartImage.

If you don't have the SystemRescue CD, you can use the Ubuntu CD:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Nice write up. I continue to enjoy [http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu) for its great value :)

---


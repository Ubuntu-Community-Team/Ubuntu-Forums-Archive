---
title: "Adding a second hard disk ?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by drifting on 2007-04-12
Hi.

I have followed this guide : -
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

And for the life of me I cannot get it to mount !

I created  /media/data and attempted to follow the instruction on mounting "data"

However after hunting through the forums I managed to get this far :-

sudo mount -t ext3 /dev/hdb1 /media/data

And it mounted ! So now what do I put in the fstab? As mine looks nothing like the example?

Perhaps this cold has got more of a grip on this bemused brain than I though? or the howto is out of date...

Paul.

---

### Post by dstew on 2007-04-12
Put this line in fstab:

/dev/hdb1 /media/data ext3 defaults 0 0

Then reboot. It should mount automatically after that.
Here is a site about fstab: [http://doc.gwos.org/index.php/Understanding_fstab](http://doc.gwos.org/index.php/Understanding_fstab)

---

### Post by terdon on 2007-04-12
Your fstab should simply have the following line:

```

/dev/hdb1    /media/data   ext3   defaults 0 2
```

Which is pretty much what the howto you mentioned suggests. Does this not work for you?

---

### Post by drifting on 2007-04-12
Thank you both, it confused me with the dfferent looking fstab.

Regards paul.

---


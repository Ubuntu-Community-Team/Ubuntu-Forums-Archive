---
title: "Accessing files on old ubuntu hard drive."
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by redhue on 2008-04-08
How do I go about accessing my files on my other hard drive? I have it installed as my primary slave. It is from my old machine and I would like to go to it quickly and easily. BTW I was running Ubuntu on it as well.

---

### Post by mikeyphi on 2008-04-08
> **redhue said:**
> How do I go about accessing my files on my other hard drive? I have it installed as my primary slave. It is from my old machine and I would like to go to it quickly and easily. BTW I was running Ubuntu on it as well.

Should be able to find it under "Places-Computer"
If needed, right click - select mount then open

---

### Post by redhue on 2008-04-08
OK I tried that and I was informed that I do not have privlidge to mount that volume. Whats next?

---

### Post by bodhi.zazen on 2008-04-08
You will need to add an entry in fstab or, if it is temporary, mount and access it as root.

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)
[Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)


OR

```
sudo mount sdb1 /mnt
gksu nautilus /mnt
```

change "sdb1" to the partition you want to access. List your partitions with :

```
sudo fdisk -l
```

---

### Post by redhue on 2008-04-08
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14405   115708131   83  Linux
/dev/hda2           14406       14593     1510110    5  Extended
/dev/hda5           14406       14593     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 4303 MB, 4303272960 bytes
255 heads, 63 sectors/track, 523 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         497     3992121   83  Linux
/dev/hdb2             498         523      208845    5  Extended
/dev/hdb5             498         523      208813+  82  Linux swap / Solaris
OK so take a look how do I go about making this drive easily and regularly accessable with out going into root everytime?

---

### Post by bodhi.zazen on 2008-04-08
```
sudo mkdir /media/sdb1
gksu gedit /etc/fstab
```

Add :

> /dev/sdb1 /media/sdb1 auto defaults 0 2

Save your changes and exit gedit.

Then:

```
sudo mount -a
sudo chown root.users /media/sdb1
chmod 770 /media/sdb1
```

done.

Read the links I gave you for a more detailed explanation.

---


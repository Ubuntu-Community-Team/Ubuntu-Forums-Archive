---
title: "really stoopid newbie question i know"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by metrodon on 2007-05-03
Hi

I've just installed 7.04 on vmware and i want to install the vmware tools. I have the instructions from vmware and the first stage is to mount the CD.

I've su - 'd to root and run the suggested vmware command that is

mount /dev/cdrom /mnt/cdrom

and also tried a number of different combinations that include /media/cdrom0 etc but none of these mount points seem to exist.

can anyone help a noob please?

---

### Post by finer recliner on 2007-05-03
1) not a stupid question

2) make sure you the place you're mounting to exists before trying to mount it there. in this case youre trying to mount to /mnt/cdrom. most linux distros use /mnt to keep all their mount points, ubuntu uses /media. this is just a naming convention, nothing to worry about. so all you need to do is:

```

$mkdir /media/cdrom
$sudo mount /dev/cdrom /media/cdrom

```

you're telling ubuntu, i want to access the content of device "cdrom" at the directory "/media/cdrom"

---

### Post by GrueTamer on 2007-05-03
Try /dev/hdc, that's what mine is.  If it doesn't work, it might be sdc, I don't know if libata would affect this or not.

---

### Post by BaffledMollusc on 2007-05-03
> **finer recliner said:**
> 1) not a stupid question

2) make sure you the place you're mounting to exists before trying to mount it there. in this case youre trying to mount to /mnt/cdrom. most linux distros use /mnt to keep all their mount points, ubuntu uses /media. this is just a naming convention, nothing to worry about. so all you need to do is:

```

$mkdir /media/cdrom
$sudo mount /dev/cdrom /media/cdrom

```

you're telling ubuntu, i want to access the content of device "cdrom" at the directory "/media/cdrom"

You'll probably need to do "sudo mkdir /media/cdrom" since that directory is not in your home directory.

---

### Post by regomodo on 2007-05-03
i used to have the same issue when i first moved to Ubuntu

I was used to accessing drives through /dev/ or /mnt instead of /media. Just a quirk of Ubuntu

---

### Post by metrodon on 2007-05-03
thanks guys, i actually got around it by copying the vmware tools file from the supposedly unmounted cd drive to the tmp directory.

---


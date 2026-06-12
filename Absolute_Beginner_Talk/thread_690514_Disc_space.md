---
title: "Disc space"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by bossa on 2008-02-07
Hi All 
I only re installed Ubuntu the other day and I ony have 26 gb left on a 80 gb disc ,is this normal ? Ihave not downloaded loads of movies or anything . lib seems to have 24 gb is that normal . I'm afraid I will run out of space before long. I installed Vmware is this a possible cause of space being used. I allocated the standard 8 gb for two OS.

---

### Post by jken146 on 2008-02-07
Please post the output of ```
df -h
```

---

### Post by dca on 2008-02-07
Once your VM is set-up and you set the partition size a file is created (or multiple) that equal that partition size...  Oooops, I'm stuck in a loop, now...  In other words when installing the VM guest, it asks what size partition.  You answer 2GB, 3, 4, 10, etc.  Once you answer and get the creating disk multiple files are created equaling that size...  By default, though, if it's VMWare it installs in /var/lib/vmware/virtual\ machines...

---

### Post by bossa on 2008-02-07
steve@steve-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              71G      33G   35G  48% /
varrun               1014M      236K 1014M   1% /var/run
varlock              1014M       0 1014M   0% /var/lock
udev                 1014M       84K 1014M   1% /dev
devshm               1014M       0 1014M   0% /dev/shm
lrm                  1014M           34M  980M   4% /lib/modules/2.6.22-14-generic/volatile


Here you go..what do you think?

---

### Post by jken146 on 2008-02-07
Well, it says you have 35 GB free.

---

### Post by bossa on 2008-02-07
> **jken146 said:**
> Well, it says you have 35 GB free.

Hi jken
Yeah  I deleted one of the OS in VMWare so I guess that freed up 8 gb. Right now I just have XP . What would be the minimum space to allocate for a OS in VMWare ie XP ..I would like to have a Linux distro too ?

---

### Post by forrestcupp on 2008-02-07
If it's not your vmware, it's because you partitioned you hard drive for Ubuntu, and you're only looking at the available space on one of the partitions.

---

### Post by jken146 on 2008-02-07
> **forrestcupp said:**
> If it's not your vmware, it's because you partitioned you hard drive for Ubuntu, and you're only looking at the available space on one of the partitions.

He said he had an 80 gig disk.  df shows a total size of 71 gigs for that partition, which sounds about right to me.

---

### Post by bossa on 2008-02-07
Thanks guys 
I used the disc usage analyzer and found a bunch of stuff that needed to go and things are looking better

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              71G   16G   52G  24% /
varrun               1014M  236K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   80K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile

Could I ask again what would be minimum space allocated for XP and minimum for a distro in VMWare?

---

### Post by jken146 on 2008-02-07
For XP, that depends what you want to do with it.  I think it takes up about 4 gigs just for the install (but I may be a bit off there) and then there are all the programs running on top of it, which will require different amounts of space depending on what they are.  A modern game, for example, can be huge.

For a Linux distro, that really depends on which one you're talking about.  Linux distros range from less than 50 MB in size (e.g. Damn Small Linux, Puppy) to something like Sabayon, whose installer complains if you give it less than 15 GB.  I would give a *buntu distro a *minimum* of 5 GB.

---


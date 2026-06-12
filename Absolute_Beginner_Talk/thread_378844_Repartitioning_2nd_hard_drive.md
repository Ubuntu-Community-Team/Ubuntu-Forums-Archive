---
title: "Repartitioning 2nd hard drive"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by BurgesS on 2007-03-07
Do I need to download a partitioning program to repartition my 2nd hard drive?  It is currently NTFS and I want to repartition it so that I have a linux partition as well.

---

### Post by Kateikyoushi on 2007-03-07
You can not repartition amounted hard drive, for partitioning I recommend gparted which as a nice gui and most likely you used it during installation.
Right now I am upgrading so can't check whether it is installed by default but you can always add it via synaptic.

---

### Post by Atreus12 on 2007-03-07
I'm not sure about 6.10, but 6.06 does not have gparted installed by default

To install gparted:

```

sudo aptitude install gparted

```

It should show up under: system -> administration -> Gnome Partition Editor

---


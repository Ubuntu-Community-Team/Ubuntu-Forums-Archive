---
title: "Partioning Problems"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by -Stevey-Wonder-1990- on 2007-10-06
Ok here's my dilema, i want to dual boot windows with linux... i have a reasonable old computer and would like to run Windows 98, Xubuntu and perhaps Puppy/DSL.  I have a 30GB hard drive, how would you go about partioning this harddrive?  How much space would need allocated to each OS?  I have 192MB RAM although i dont think this is important?!

Thanks

---

### Post by -Stevey-Wonder-1990- on 2007-10-06
[bump]

any help out there?

---

### Post by tenmillionmilesaway on 2007-10-06
Windows will require a single partition (fat32?? i never did w98 ).  The minimum for a Linux distro would be a root partition and a swap partition, however i think that both Linux distros could use the same swap partition.  Afaik the swap should be about the same size as your ram but don't quote me on that.  Xubuntu should be fine with a few gig, don't know about the others.
You could make a data partition in fat32 which is quite large, say 20gig and then you will be able to share files between all the os installed. and have a smaller partition for each os (and a swap).
Is this a blank hdd with no os on it at all or do you already have windows on it?

Richard

---

### Post by -Stevey-Wonder-1990- on 2007-10-06
i already have windows on it, but i have read quite a few dual booting articles and am quite confident about resizing partitions and dual booting.  However what order would be best for installing the distros.  Do all linux distros use GRUB as the boot manager?

---

### Post by tenmillionmilesaway on 2007-10-06
If you already have windows on there then just pop the xubuntu cd in and let it boot, then there is an install icon on the desktop.  follow through the options and when it comes to partition resizing you can let it handle it.  You should see a slider which allows you to choose how much of the current windows partition you want to use choose an percent and then it will then create the swap and root partitions by itself.  You can go through the partitioning manually if you want tho.
Not all Linux distros use grub by default, however they should all work with grub.  Having no experience with Puppy or DSL I cant tell if they use grub.

In regards to the ordering so long as windows in on first you should be ok with the Linux installs.

---


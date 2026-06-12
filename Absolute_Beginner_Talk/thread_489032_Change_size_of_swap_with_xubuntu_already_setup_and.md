---
title: "Change size of swap with xubuntu already setup and running"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Xoldie on 2007-06-30
How do I change the size of the swap partition once xbuntu is already setup and running?

---

### Post by PCFascist on 2007-06-30
Boot the install CD that you used. You should beable to install Gparted and resize your swap.

This might mess up you fstab if you use UUIDs... but I really have no idea on this.

---

### Post by pyros on 2007-06-30
Yeah assuming you get internet connectivity from your live cd, just install gparted. first you will have to shrink your main partition, but then you should be able to increase the size of your swap partition.

---

### Post by Xoldie on 2007-07-01
Tks to all. I'll try gparted and after that I'ii be back with the results. As I'm a Xubuntu user with less than 24 hour flown on Linux you may be sure I'll be back soon. Bye bye and tks again.;)

---

### Post by bodhi.zazen on 2007-07-01
> **pyros said:**
> Yeah assuming you get internet connectivity from your live cd, just install gparted. first you will have to shrink your main partition, but then you should be able to increase the size of your swap partition.

FYI : 

1. I like your signature :)

2. gparted is already on the live (desktop) CD. It is not installed to HD, so with a hd install you need  to install gparted, but then again, IMO gparted is bst run from a live CD with all HD partitions unmounted ...

---

### Post by MrSilva on 2007-07-01
Hi folks... new to forum... Ubuntu user for two weeks. I too had a Belkin card that was giving me fits. I tried all sorts of things and finally got a new card. I bought a basic "Ativa" wireless card from Office Depot for about $30 and it works perfectly. It works on my Belkin router at home and so far has worked at several hotspots around Chicago.

---

### Post by larytet on 2008-06-02
see [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

To clean the swap file
```

# swapoff -a
# swapon -a

```

To change "swappiness"
```

echo 10 > /proc/sys/vm/swappiness

```


add line 
```

vm.swappiness=10

```
to the file /etc/sysctl.conf


I have 2G+ of memory and typical usage 1G even when I run virtual Win XP
The change above immediately boosts the system performance. The improvement is very (like VERY) significant. Probably two or three times when switching between windows of heavy applications, like Qemu/OpenOffice/Firefox/Evolution. I think that You are going to say WOW

---


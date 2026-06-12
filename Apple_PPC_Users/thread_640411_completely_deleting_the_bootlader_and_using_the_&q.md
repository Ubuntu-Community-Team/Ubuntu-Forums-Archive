---
title: "completely deleting the bootlader and using the &quot;option&quot; key to select OS?"
date: 2007-12-14
forum: Apple PPC Users
---

### Post by DrivinWest on 2007-12-14
I used used to have Fedora Core 8 installed on my PowerBook G4 and have since replaced it with Kubuntu.  For whatever reason, the Fedora bootstrap/bootloader (whatever it's called!) still exists; I turn on the machine and it asks me whether I want to boot to Fedora, OS X, or CD.

What I really want to do is delete the Linux bootstrap entirely and just use the "option" key on boot up.  I've tried it, and it works, I just don't want to be asked via the bootloader 1st.

Any help is much appreciated!

---

### Post by frog_pilot on 2007-12-14
You have to open the system prefrences panel in OSX and got to startvolume. Here you have to choose your OSX Systemvolume. Now your computer will start OSX without asking if you dont press c-key or option key. After this you can delete the yaboot-partition. But it isnt worth the trouble since its only a 1 MB partition.

---

### Post by DrivinWest on 2007-12-14
Many thanks for the reply!  Selecting the OS X startup disk works.

For future reference, how do I go about editing/deleting the yaboot partition?  In Disk Utility I don't have any additional logical partitions.

Thanks again,
DW

---

### Post by frog_pilot on 2007-12-15
There are no logical partitions on disks with apple partition map. The known limitations for partitioning in dos/windows dont exist in the apple partition scheme. You can access the yaboot-partition only from your linux system. With gparted or qtparted you can delete the yaboot partition and add the new freespace to a partition besides. But keep in mind, as stated its usually less than 1 MB and the whole process of deleting and resizing partitions can create new problems...

---

### Post by driven1 on 2007-12-19
While running linux open** /etc/yaboot.conf **with a text editor in Terminal and add

```
defaultos=macosx
```

if you want to boot OSX without having to do anything. Of course, the bootloader is still there, but on my Powerbook it is faster than using the option key. With this setup you can choose Linux by either method. You can also edit the code

```
Timeout=xxx
```

by increasing or decreasing the numbers represented by the ```
xxx
``` you can speedup or slow down the bootloader.

Oops, nearly forgot to bless with Holy Penguin Pee... anytime you edit the yaboot.conf you need to run ```
sudo ybin -v
``` in order for the changes to be effective.

---


---
title: "Resizing with GParted"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by SpiceWeasel on 2006-10-11
This is probably a stupid question, i know linux cant write to NTFS nomral or even well with the programs you get but is there a program out there that can allow me to make my linux partition smaller then make the NTFS partition bigger. Or maybe use one program such as GParted to make the linux one smaller and a completely different program to add to the NTFS partition. Basically i just want to know if its possible to make my ext3 smaller and take the freed up space for ntfs with out having to reformat the whole damn thing. ](*,)

---

### Post by meng on 2006-10-11
The latest GParted LiveCD apparently has support for resizing and moving all partition types now (last version couldn't move ext3 among other things).

I would recommend using a LiveCD rather than an installed Linux.

---

### Post by SpiceWeasel on 2006-10-11
Have been using, in fact im on it right now. :p I have no problem with making the ext3 smaller but as far as making the NTFS bigger it doesnt let me do it.

---

### Post by Frak on 2006-10-11
QTParted done that when I used it. GParted didn't though, don't know why.

---

### Post by fatsheep on 2006-10-11
You can only expand a partition to the right so if your NTFS partition is up against the right edge of the hard disk (when viewed in a program like GPARTED) then you will need to move it to the left and then expand it.  I found this out when I was trying to expand my ext3 partition...

---

### Post by SpiceWeasel on 2006-10-11
So if from left to right my partitions are NTFS/ext3/fat32/linux-swap and i take the ext3 and cut it in half it only lets me put all of that space following the ext3 and when i click on the unallocated space it doesnt give an option to move it. In other words i am a total noobert at using gparted hehehe so how exactly do i get the unallocated space on the other side so i can resize the NTFS partition.....or i could be talking total nonsense here so feel free to tell me whats what. :confused:

---

### Post by meng on 2006-10-11
Are you getting these problems with the latest version of the GParted LiveCD? The last upgrade had considerably improved support for moving partitions. Just making sure you're not talking about an older version, or about the Ubuntu LiveCD.

---

### Post by SpiceWeasel on 2006-10-11
The current live cd im using is one I just got last week from my professor who ordered them a week or two before for those of us that will be taking the linux class next semester so i would think its more current then the ones I burned last month.

---

### Post by meng on 2006-10-11
> **SpiceWeasel said:**
> The current live cd im using is one I just got last week from my professor who ordered them a week or two before for those of us that will be taking the linux class next semester so i would think its more current then the ones I burned last month.
So it's an Ubuntu LiveCD correct? I suggested using the GPARTED LIVECD (sorry, just felt I had to shout it) because the latest version of GParted, which is on the GPARTED LIVECD (my, my, quite loud, eh?) has much improved support for resizing/moving partitions, whereas the less recent versions were not so good in that regard.

---

### Post by SpiceWeasel on 2006-10-11
Ah so i need a GParted live cd instead of the ubuntu live cd? :-k Thats so crazy it just might work hahaha. ](*,)

*EDIT* Just the thought makes me think of how much fun i could have playing with the partitions on the pcs in the commens area of my college. :twisted:

---


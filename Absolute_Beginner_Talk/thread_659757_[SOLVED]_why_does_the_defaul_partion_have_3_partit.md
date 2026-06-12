---
title: "[SOLVED] why does the defaul partion have 3 partitions?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by iamclueless on 2008-01-06
Hi

ive installed and reinstalled Ubuntu and Xubuntu a few times using automatic and manual partitioning...

why do they  create and extended partition and put the swap partition within it, basically taking up the whole thing?

at a minimum i thought a swap and a root partition was needed

so why put a swap partition within an ext3 partition?

---

### Post by LowSky on 2008-01-06
huh? ubuntu only makes 2 partitions
why not make your own partitions? set everything up your self. you can create primary / then create an extended with you home and swap, that way you can still make more primary partitions

---

### Post by indytim on 2008-01-06
When you hit either the 3rd or 4th partition (can't remember what the exact limit is)on a h/d, you are going to be forced to an extended partition.  However you you got to your harddrive configuration, that is what has happened.  Evidently the /swap forced you over the edge.  An extended partition is like a bucket holding area for additional partitions.

Easy fix : get a copy of GParted Live to a cd.  Boot to it. Resize your swap to ~2x RAM.  Then either leave the rest of the space as unallocated (for growth later), or create a new partition for data or whatever storage.

INdyTim

---

### Post by iamclueless on 2008-01-06
oops late night, i dont think i typed that well

Yes when the default partition runs

i end up with

and ext3 - containing root

and a smaller ext3 partition that has the swap partition within it


I though all that was needed is a swap and a root

so i can manually just make these two partitions then?

---

### Post by llamakc on 2008-01-06
> **iamclueless said:**
> oops late night, i dont think i typed that well

Yes when the default partition runs

i end up with

and ext3 - containing root

and a smaller ext3 partition that has the swap partition within it


I though all that was needed is a swap and a root

so i can manually just make these two partitions then?

The smaller partition is not ext3, its type is swap.

---

### Post by Alx c on 2008-01-06
If yu are using vista with out ubuntu (at least on a dell) it comes with 3 partitions, If you are using vista you might want to get rid of these partitions for space (it dependes on the computer you are using some come with 3 some with 1). Just a sujestion.

---

### Post by iamclueless on 2008-01-06
ok

finally understood it after yet again reinstalling :)

the swap partition cannot be set as a swap unless you first designate the space as extended

you get a cyan coloured partition with a red one inside it

---


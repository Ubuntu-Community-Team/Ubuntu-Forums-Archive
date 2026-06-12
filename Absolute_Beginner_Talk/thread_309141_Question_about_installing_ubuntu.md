---
title: "Question about installing ubuntu"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2006-11-29
My friend haven't install Ubuntu. He has two partition (one HDD,both are NTFS). How to install ubuntu on 1st partition? Because I thought installing on the HDD will reformat the HDD and kill all the partitions. I don't want this to be happen.

---

### Post by Bachstelze on 2006-11-29
You cannot install Ubuntu (or anything else than an NT-based Windows) on NTFS.

---

### Post by renzokuken on 2006-11-29
you can have both OS's on the first partition.

you'll need a few gigs free space on it, defrag the windows partition, boot from the install cd and ubuntu will resize the partition for you, format it and install to it

---

### Post by Bachstelze on 2006-11-29
> **renzokuken said:**
> you can have both OS's on the first partition.

Wrong.

---

### Post by renzokuken on 2006-11-29
no, because, once ubuntu has done its magic its no longer a single partition, it will be two (three including swap)

i just didnt explain it very well

---

### Post by 56phil on 2006-11-29
Welcome to Ubuntu.

You can have two OSs on the same HDD. I've done it. All you need to do, providing there is enough free space on the drive, is click install on the Ubuntu desktop. I hope this helps.

---

### Post by Kieranties on 2006-11-29
> **renzokuken said:**
> no, because, once ubuntu has done its magic its no longer a single partition, it will be two (three including swap)

i just didnt explain it very well

Indeed, the nice thing about gparted, is that it can resize partitions for you.  When resizing just make sure you dont try to make the partition smaller then the current data stored on it.  This is shown with the inner yellow bar.

Then with the reamining space, reformat the majority into ext3 for you ubuntu partition, and the rest into linux-swap for swap space.

Normall reccomendation is about twice you memory for swap.  But if you have say a gig of memory, then a gig of swap is more than enough

Have fun!

---

### Post by Bachstelze on 2006-11-29
> **renzokuken said:**
> no, because, once ubuntu has done its magic its no longer a single partition, it will be two (three including swap)


I guess the OSes won't be on the same partition then...

---

### Post by renzokuken on 2006-11-29
picking nits are we?

---

### Post by Bachstelze on 2006-11-29
Nope, you said something wrong and I corrected it, that's all, no offense :)

---

### Post by renzokuken on 2006-11-29
none taken, i know i really do suck at explaining things.

>_<

---

### Post by oliviacond on 2006-11-29
OK, everyone this is what my friend plan to do.
1. Install Ubuntu over the XP at the 1st partition (XP no longer exist at his pc/no more XP)
2. Set the 2nd partition as /home. (he plan to move the data from 2nd partition to the /home(1st partition) temporaly and format the 2nd partition as ext3 and set /home at the 2nd partition and move the data back to the /home(2nd partition)

---

### Post by Bachstelze on 2006-11-29
That will erase XP !

How big are the partitions ? Anyway, if you want to use the second as a /home partition, you'll have to format it so better clear out the wole drive and repartition it, I think.

---

### Post by oliviacond on 2006-11-29
Nevermine. He is happy that XP no longer exist in his pc.
Erm......he is making the 2nd partition now. I tell him to leave 15GB space to the 1st partition(where the Ubuntu will stay).

---

### Post by renzokuken on 2006-11-29
sounds good

---

### Post by oliviacond on 2006-11-29
So, the question is : Can I select which partition I want to format and install (no Gparted involve yet,just Ubuntu Live CD) ?

---

### Post by Bachstelze on 2006-11-29
There will be GParted involved since it's what the Ubuntu Live CD uses for partitioning ;)

---

### Post by oliviacond on 2006-11-29
How? Please teach me step by step for installing Ubuntu on 1st partition.

---


---
title: "Partitioning, Feisty, Win XP"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2007-04-19
I have a full NTFS partition for WinXP Media Center 2005. I used to have room for Ubuntu, but could never get my wireless working. Now, according to the live CD, it works great!

So, how can I -SAFELY- resize my NTFS partition, without damaging the installl and whatnot, and -just in case- (Eas my mind), be able to bring it back to the full size of my HD, without damaging, slowing down, or anything. Be able to have it exactly like it is right now.

---

### Post by tchoklat on 2007-04-19
The feisty installer will resize your ntfs partition and install itself. Defrag XP first though.

---

### Post by Taigrr on 2007-04-19
That was easy.

Will it be able to revert back, as well? Like, put C: back as the whole HD, should I want it to? (Probably won't. I just don't trust technology)

---

### Post by MikeBgts on 2007-04-19
Best commercial solution: perfectdisk for defragmentation + partition magic to create your partitions.
Best free solution : Windows utility for defragmentation + Ubuntu's automatic partitioning
Best open source solution: GParted live cd + manually define partitions using Ubuntu's partitioner (or in automatic without the use of GParted) + these require before a defrag under windows (I have not tried any open source windows software for defrag)

---

### Post by MikeBgts on 2007-04-19
> **Taigrr said:**
> That was easy.

Will it be able to revert back, as well? Like, put C: back as the whole HD, should I want it to? (Probably won't. I just don't trust technology)

I believe that you can delete the linux partitions and then fix the MBR (for windows) which will delete Grub (this is valid if you want to keep your win installation that already exists). 

For a new win installation there are no wories: delete the linux partitions and the new win installation will delete Grub or install win and then delete the linux partiotions. I suggest you to use atool like partition magic in windows to delete the linux partitions and unify your space back.

---

### Post by Taigrr on 2007-04-19
No no no, I want to keep it(the winXP installation) how it is now. If it were just a matter of installing I wouldn't care, i'd just reformat and call it good.

But I want this(WinXP) partition to stay, just a bit smaller than it is now (Chop 25 gig off the end for Linux), and if Ubuntu doesn't work out, I want to be able to extend this (Windows) partition back to the full 80 gig that my harddrive holds

---

### Post by MikeBgts on 2007-04-19
Then you have to:
- Under windows use a tool like Partion magic to make all the partition changes
- Then try what you like with ubuntu. If you don't like ubuntu and you want to keep your win installation you'll have to:
- Fix your MBR (fixmbr) (so search for this here and also use google). This will delete Grub and you'll boot directly to your windows installation.
- In windows use a tool like partition magic to delete the linux partitions and make all the changes you want with them.

---


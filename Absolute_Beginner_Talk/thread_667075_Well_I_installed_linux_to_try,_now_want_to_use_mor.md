---
title: "Well I installed linux to try, now want to use more of my hard drive"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by joshlemer on 2008-01-14
Been using Linux(Ubuntu Gutsy Gibbon 7.10) for a bit more than a week now. I did it by shrinking some (5 GB) of my hard drive (200 GB) while in Vista. Then I downloaded Linux, made a CD, installed, the whole shebang. Now that I'm comfortable in Linux, I'd like to use more of my hard drive, so how do I do that? Does it have something to do with "partitioning" (don't know what the word even means)? I basically want to make my computer's harddrive 50/50 Ubuntu7.10/Vista, instead of 5/195 or whatever it is. Should I make backups of all my data in Vista? Do I have to wipe my drive?

---

### Post by -grubby on 2008-01-14
MAKE BACKUPS. Basically what I'd tell you to do is boot up your ubuntu-live cd. Then go to System-Administration>partition editor. After that's open you use the built in options to resize the partitions (make vista smaller first, then make ubuntu bigger). BTW, ubuntu will be listed as "ext3" and vista as "ntfs"

---

### Post by Dreamlocked on 2008-01-14
I hear the partitioning tool needs too much time to partition Vista's ntfs filesystem (which is a bit different from XP's). Better to shrink Vista from within Vista.

---

### Post by joshlemer on 2008-01-14
Nathan, why use my live cd instead of already-installed Ubuntu?

Dreamlocked: How would I do that then?

---

### Post by -grubby on 2008-01-14
> **joshlemer said:**
> Nathan, why use my live cd instead of already-installed Ubuntu?

you can't exactly partition your ubuntu drive while you're using it (as in it's mounted)

---

### Post by joshlemer on 2008-01-14
Ok will anything be damaged in vista? Lastly, I don't have patition editor(atleast not on my installed ubuntu), but the live cd does I'm guessing?

---

### Post by Dreamlocked on 2008-01-14
Sorry for the delay.
Here, short guide with screenshots showing how you can [partition Vista from withing Vista]("http://www.tech-recipes.com/rx/1593/vista_shrink_partition").

---


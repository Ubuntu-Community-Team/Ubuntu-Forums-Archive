---
title: "Defragment"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by thepocketdrummer on 2006-02-20
How do you defragment in Linux?

---

### Post by bscbrit on 2006-02-20
You don't - its not necessary.  However, every 24th time a drive is mounted some essential housekeeping is carried out.

---

### Post by psusi on 2006-02-20
You really don't need to because linux doesn't use retarded block allocation algorithms that cause massive fragmentation like certain other operating systems.  If you REALLY want to though, you can install the defrag package which can defragment ext2/3 partitions.  You can't use it on a mounted partition though, so if you want to defrag your root you will need to do this from the livecd.

---

### Post by cronholio on 2006-02-20
> every 24th time a drive is mounted some essential housekeeping is carried out

Only ext2/3. ReiserFS doesn't need "manual" defragmentation. ;)

---

### Post by psusi on 2006-02-20
[QUOTE=cronholio]Only ext2/3. ReiserFS doesn't need "manual" defragmentation. ;)[/QUOTE]

Actually, it needs it just as much as ext2/3, which is to say, not enough to worry about, but not zero either.  

The thing you see every 24th boot has nothing to do with defragmenting, that's just fsck.  It is checking to make sure the filesystem looks like it's not hosed up.  You can disable that with tune2fs, and seeing as how it is a rather pointless waste of time, it is a shame that ubuntu doesn't do that automatically.

---

### Post by steve.horsley on 2006-02-20
What about vfat partitions? I presume they need defragging, even if used exclusively by Linux (I know, if it's exclusively used by Linux, you wouldn't use vfat, but if you did...)?

---

### Post by bscbrit on 2006-02-20
Cronholio, the essential housekeeping is not defragmentation, it is checking for lost inodes and  duplicate inodes I believe - but your point is accepted.

---

### Post by earobinson on 2006-02-20
[QUOTE=steve.horsley]What about vfat partitions? I presume they need defragging, even if used exclusively by Linux (I know, if it's exclusively used by Linux, you wouldn't use vfat, but if you did...)?[/QUOTE]
This is a very good question I would like to know the answer also :)

---

### Post by bscbrit on 2006-02-20
I don't know how you would defrag FAT using Linux but, as you say, you wouldn't ever need to because the _only_ sensible time you would use FAT is to exchange data with Windows, in which case you could defrag from there.

---

### Post by psusi on 2006-02-20
[QUOTE=bscbrit]I don't know how you would defrag FAT using Linux but, as you say, you wouldn't ever need to because the _only_ sensible time you would use FAT is to exchange data with Windows, in which case you could defrag from there.[/QUOTE]

Exactly.  It would be nice to be able to do this from linux, but nobody has bothered to write such a program because you can just use windows to do it, which you probably have if you have a vfat partition.  

It also isn't really needed if you're only accessing it from linux.

---

### Post by earobinson on 2006-02-20
[QUOTE=bscbrit]I don't know how you would defrag FAT using Linux but, as you say, you wouldn't ever need to because the _only_ sensible time you would use FAT is to exchange data with Windows, in which case you could defrag from there.[/QUOTE]
Or for example someone who wants to keep there data on a hd and be able to yank out the hd once in a while and bring it to work (where they use windows) and plug it in.

My workaround for this is to keep a smaller 10 fat partition but It would be nice if i could keep my work hd all fat and defrag using linux.

very few people have this problem but it is still nice to look for a soultion.

---

### Post by bscbrit on 2006-02-20
OK, but you could store the data in any format you wanted on your hard drive, as long as the media used to transfer it to the windows machine is compatible with both OS.  I suppose it depends on the quantity of data to be transferred - if you have to physically move the drive then you might have a point but you could still defrag it on the windows machine.

HOWEVER - I agree that looking for solutions to problems that are still more conceptual than physical is a worthwhile endeavour, and you've got me curious now.  Time to give it some more thought....  :D

---

### Post by earobinson on 2006-02-20
[QUOTE=bscbrit]OK, but you could store the data in any format you wanted on your hard drive, as long as the media used to transfer it to the windows machine is compatible with both OS.  I suppose it depends on the quantity of data to be transferred - if you have to physically move the drive then you might have a point but you could still defrag it on the windows machine.

HOWEVER - I agree that looking for solutions to problems that are still more conceptual than physical is a worthwhile endeavour, and you've got me curious now.  Time to give it some more thought....  :D[/QUOTE]
Just pointing out that I only take the hd out once in a blue moon I just like the option to do it. so it spends 99% of its time on linux :)

> HOWEVER - I agree that looking for solutions to problems that are still more conceptual than physical is a worthwhile endeavour, and you've got me curious now. Time to give it some more thought.... 
Me 2, Ill keep looking for an answer

---


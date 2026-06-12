---
title: "Anyone using JFS filesystem in Arch?"
date: 2008-11-12
forum: Arch and derivatives
---

### Post by kpkeerthi on 2008-11-12
Please post your experiences with JFS. Is it safe to use for / and /home?

---

### Post by chucky chuckaluck on 2008-11-12
i'm using it for everything. i've used xfs and reiser on two previous installations. it might be a little zippier than xfs, but not that much different. reiser was super fast with pacman, but really slow with my music collection.

---

### Post by TenPlus1 on 2008-11-12
I use JFS for both my / and /home directories on a laptop install of Ubuntu 8.04 (no swap partition) and it's pretty fast and so far no problems :)

---

### Post by SkonesMickLoud on 2008-11-12
I used to use it on Arch and it was quick.  However, it being nearly impossible to shrink a JFS partition led me to reformat in Reiserfs.  MurderFS has only added a few seconds to my boot time (due to a slower fsck), but I'm still getting ~35 second boots and I haven't noticed any slowdown once I'm up and running.

---

### Post by chucky chuckaluck on 2008-11-12
> **SkonesMickLoud said:**
> I used to use it on Arch and it was quick.  However, it being nearly impossible to shrink a JFS partition led me to reformat in Reiserfs.  MurderFS has only added a few seconds to my boot time (due to a slower fsck), but I'm still getting ~35 second boots and I haven't noticed any slowdown once I'm up and running.

35 seconds? mine only takes 18. you must be loading up on everything.

---

### Post by medic2000 on 2008-11-12
I will try reiserfs in the next installation. By the way how is your boot time is 18 seconds?

---

### Post by handy on 2008-11-12
I use ext2 on /boot (I think it is a requirement anyway). ext3 on / & jfs on any other partitions.  I also don't have a /swap.

I have a couple of machines running that way, I did get corruption once in my Oblivion save games, which lost me about 20 hours of gaming which I had to do again. (hard work this gaming :-)) 

I doubt that the loss had anything to do with jfs, but I can't really know.  The system didn't complain when it checked the disk?

---

### Post by chucky chuckaluck on 2008-11-12
> **medic2000 said:**
> I will try reiserfs in the next installation. By the way how is your boot time is 18 seconds?

huh! i was wondering why your's took so long (you didn't install sabayon by accident, did you?). right now, i only have three daemons starting and they all have @ in front of them. i use mostly terminal apps, so my home directory isn't filled with giant wads of config directories. uh... my pure thoughts are probably being rewarded, somehow...

---

### Post by SkonesMickLoud on 2008-11-13
> **chucky chuckaluck said:**
> 35 seconds? mine only takes 18. you must be loading up on everything.

Nah, just a POS laptop.  Hell, the fsck for reiser takes 13 seconds...

---

### Post by Xbehave on 2008-11-13
SkonesMickLoud any chanche you could use bootchart to have a look at your bootup. Im using reiserFS on ubuntu and have noticed a 5 second fsck freeze on root and another 5 on home, according to bootchart the fsck program just zombies for 5 seconds. This is on a boot which say it doesnt need to fsck. 

I thought it was a ubuntu bug but, generally people are reluctant to look at anything involving reiserfs because its unsupported so if i knew it was a bug across distros i would atleaset no its not just a config thing.

> Please post your experiences with JFS. Is it safe to use for / and /home? 
I had a bad experience with JFS because i was running an nvidia card and JFS doesn't take well to crashes (neither does XFS apparently)

---

### Post by MisfitI38 on 2008-11-13
I use JFS for everything.
It is the best balance of long-standing stability, maturity and modernity.
It also offers excellent, predictable performance on all different kinds of disk usage; from many small files to few large ones.
It mounts and fscks fast.
Haven't had a filesystem-specific issue with it yet.

---

### Post by Pogeymanz on 2008-11-13
I like JFS. It seems quicker than ext3 and hasn't given me issues.

I've also heard that it uses less CPU power to read/write to JFS partitions. Does anybody know anything about this?

---

### Post by SkonesMickLoud on 2008-11-13
> **MisfitI38 said:**
> I use JFS for everything.
It is the best balance of long-standing stability, maturity and modernity.
It also offers excellent, predictable performance on all different kinds of disk usage; from many small files to few large ones.
It mounts and fscks fast.
Haven't had a filesystem-specific issue with it yet.

Pretty much this.  Only thing I don't like about it is that it's a complete PITA, and sometimes impossible to shrink.  I'm still trying to get used to how long it takes a 10 Gb MurderFS partition to mount.

---

### Post by kpkeerthi on 2008-11-14
> **SkonesMickLoud said:**
> Pretty much this.  Only thing I don't like about it is that it's a complete PITA, and sometimes impossible to shrink.  I'm still trying to get used to how long it takes a 10 Gb [COLOR="Red"]**MurderFS **[/COLOR]partition to mount.

MurderFS! :) I feel sorry for what happened to Hans Reiser.

---

### Post by kpkeerthi on 2008-11-14
Thanks everyone for your valuable comments.

---

### Post by chucky chuckaluck on 2008-11-14
> **kpkeerthi said:**
> MurderFS! :) I feel sorry for what happened to Hans Reiser.

happened to him? interesting way to put it.

---

### Post by mips on 2008-11-14
> **kpkeerthi said:**
> I feel sorry for what happened to Hans Reiser.

Huh? He killed his wife and got caught. Nothing 'happened' to him, he created his own reality.

---

### Post by chucky chuckaluck on 2008-11-14
> **mips said:**
> Huh? He killed his wife and got caught. Nothing 'happened' to him, he created his own reality.

maybe he meant getting caught. that kind of happened to him.

---

### Post by kpkeerthi on 2008-11-14
Hmm... English is not my first language and sometimes what I intend to say does't get conveyed in the right sense :) 

I guess I should have said "I feel sorry what he is going through now". ;)

---

### Post by Vince4Amy on 2008-11-14
I always use JFS in any distro, it's stable, fast and responsive. Not to mention it's actually quieter.

---

### Post by mips on 2008-11-14
> **kpkeerthi said:**
> Hmm... English is not my first language and sometimes what I intend to say does't get conveyed in the right sense :) 

I guess I should have said "I feel sorry what he is going through now". ;)

No problem on English not being your first language, it's better than some native English speakers ;)

What happened was sad but I would not feel sorry for someone that murdered someone else. cause & effect, action & reaction, butterfly effect etc

---

### Post by chucky chuckaluck on 2008-11-14
> **kpkeerthi said:**
> Hmm... English is not my first language and sometimes what I intend to say does't get conveyed in the right sense :) 

I guess I should have said "I feel sorry what he is going through now". ;)

figured it might have been something like that. sorry to have picked on you.

---

### Post by JNelson on 2008-11-14
I use JFS on my partitions too. My system feels more fast with it also. JFS has more features than Ext3.  

JFS has
Extents- These are more efficent than ext3s direct blocks. Ext3 has to make a head seek every 1024 Blocks read to read another pointer. With JFS all it has to do is read the extents and its there sort of like this.

Extent example
Extent 1 is blocks 1-30000000
Extent 2 is blocks 30000005-300000000

Ext3s block mapping is to compicated to explain.

JFS has B+ trees which NTFS,reiserfs,and xfs have.

Ext3 uses an Htree which is a stripped down B-tree.


As for JFS corruptions i only had one and that was with a 10 Year old harddisk. I have had a few corruptions with ext3 on a new harddisk.


Just remember a Journal only protects recent metadata changes not the whole filesystem.

---

### Post by chucky chuckaluck on 2008-11-16
> **JNelson said:**
> I use JFS on my partitions too. My system feels more fast with it also. JFS has more features than Ext3.  

JFS has
Extents- These are more efficent than ext3s direct blocks. Ext3 has to make a head seek every 1024 Blocks read to read another pointer. With JFS all it has to do is read the extents and its there sort of like this.

Extent example
Extent 1 is blocks 1-30000000
Extent 2 is blocks 30000005-300000000

Ext3s block mapping is to compicated to explain.

JFS has B+ trees which NTFS,reiserfs,and xfs have.

Ext3 uses an Htree which is a stripped down B-tree.


As for JFS corruptions i only had one and that was with a 10 Year old harddisk. I have had a few corruptions with ext3 on a new harddisk.


Just remember a Journal only protects recent metadata changes not the whole filesystem.

you wouldn't happen to have the cliff notes for all of that, would you?

---

### Post by medic2000 on 2008-11-17
By the way i just installed system with ReiserFS. I have to say it really rocks! So much faster than ext3!

---


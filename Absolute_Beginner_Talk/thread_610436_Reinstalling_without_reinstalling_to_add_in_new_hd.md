---
title: "Reinstalling without reinstalling to add in new hdd space?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Simimi on 2007-11-12
So when I installed Gutsy as a dual boot with my windows partition like I normally do... Now I want to remove Windows. That part is easy just remove the partition with gParted. But then I want to add the new free space to my existing /home and / partitions respectively (still trying to decide which should get more of the space...). That also really isn't too hard. The issue is; I want to return Ubuntu to a fresh install, as in format / and /home. I do not have a working install cd, and after burning 5 cds and having them all fail, I'm out of cds and ideas... 

Tips or Tricks?

Yours,
 Mimi

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
well down load a new copy of ubuntu in cases thats bad then run the checksum on it to make shur it's good
then burn the cd's really slowly

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
you should look at the man page for mount
cuses you can do some crazy crap with it that
i would make a new part and just mount it in side of /home/yourname/
maybe as extra storage
or use gparted to inlarge the /home part to fil in the windows space

---

### Post by robinl on 2007-11-12
No it cannot be done. Mounting something to a directory means that any existing data on the directory will be removed (or something like that, can't remember exactly what it was). You grow a partition if you have free space after it, but you definitely can't split that free space and link it to two different partitions. If the free space (where Windows was) is in front of all your partitions, you can't grow any of your partitions unless you repartition your whole drive, or make a new partition out of the new space and mount it somewhere.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **robinl said:**
> No it cannot be done. Mounting something to a directory means that any existing data on the directory will be removed (or something like that, can't remember exactly what it was). You grow a partition if you have free space after it, but you definitely can't split that free space and link it to two different partitions. If the free space (where Windows was) is in front of all your partitions, you can't grow any of your partitions unless you repartition your whole drive, or make a new partition out of the new space and mount it somewhere.

shur you can 
just not that way 
i said inside the forller as in make a /home/yourname/extraspace 
and mount it at extraspace
you can even mount part of a file system agin in a differnt spot not shur how its in the
man mount
thing

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
and you can grow foward just not the / part wile your useing it
you can move the hole partion and then grow it backward but this would require the live cd 

lol how ever i did kill my install once screwing with this stuff so you know the standard disclaemer for open source software well insert here "          "

---

### Post by rsambuca on 2007-11-12
If you want a fresh install, then what is the problem?  Just wipe the drive when you install.

---

### Post by robinl on 2007-11-12
> **<<joe>> said:**
> shur you can 
just not that way 
i said inside the forller as in make a /home/yourname/extraspace 
and mount it at extraspace
you can even mount part of a file system agin in a differnt spot not shur how its in the
man mount
thing

That's fundamentally different to what OP is trying to achieve (increasing the size of ~/), FWIW I can even create a symlink from anywhere to ~/something/ and it would still show up in my home folder, but then the content in the symlink can also be anywhere in the file system, being in ~/ merely offers convenience, not actually expanding the size of ~/ .

Also, please learn to spell and use proper punctuations. Ubuntu has built in spell checker for you, you just have to use it.

---

### Post by jaybombalous on 2007-11-12
its never fun to take pop shots when u look just as bad doing it...

> Ubuntu has built in spell checker for you, you just have to use it

it may fix your spelling mistakes, but it will never fix your grammatical errors. :(

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
i am sorry i got a littel bit mad just then and know i will not check my spelling :) kuss you still know what i mean. And your actually the first person to say any thing to me about my spelling on ubuntu forums so i don't know if it was a shot at my inteigence or not i don't care i know how to use all of thoughs fun simbles like ,.:;"''!@#$%%^<>?/ []}{ or what ever else 
i dont know what you do for a liveing and i dont know how smart you are so anyway 
cant spell never could i can desine air planes penn state says i can jsut cant spell :) 
I even know how to use a period. just shut it cuse its easier not to save time and gets who ever i am helping fix there problem faster

edit yes i spelled no know on purpose in case you mised it
ok your right. period i should use more often. I just tried to read through that and man, just one huge run on. lol so spellin, screw it. periods ok every thing else when i feel like it. rember were an open source comunity i dont need to do ****

---

### Post by Simimi on 2007-11-12
Sorry it took me so long to reply. I would just reinstall but I am having trouble getting a working cd iso burnt, as it stands. I'll google how to use md5 checksums properly and I'll try the "download a fresh iso and check the md5sum and burn slowly" idea. Though if my iso produced a good image before, why has it been producing bad images now? Is it just the cds that are bad?

---

### Post by rsambuca on 2007-11-12
What happened to your original disc that you installed Gutsy with?

---


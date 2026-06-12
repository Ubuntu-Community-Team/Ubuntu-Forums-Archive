---
title: "Another one with a partition problem"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by arielb_86 on 2007-06-06
Well ive been playing around with the live cd and i wanted to install ubuntu.

It pops 2 options for the partition. the manual and the one that theoretically would do the whole thing automatically including the dual boot. i picked that one but it jumped direction to what i belive is the migration tool. then i kept going a little bit farther and the last screen with the general information was not telling me anything about any partition. 

My laptop has 120 gigs.....20 for recovery, 60 for data, 40 for XP. i would really like to break into two my 60 gig partition into two. But then again i dont know how the manual works and i dont want to lose anything. Is there something i can do or should i partition the hard drive on windows and then install ubuntu into that new partition?

Thanks!

---

### Post by FleetAdmiral74 on 2007-06-06
If you want to resize xp so you can have xp AND ub, first thing is to defrag the hell out of XP. This puts all the files in front. Just remember, might take a few times. Then you should be able to resize the ntfs partition (make sure to give it some free space depending on how much is actually taken...). Then make a small swap partition and a / partition. 

not quite sure what the migration tool is, but you are right about it auto setting up dual boot, if it works you will be able to choose between the two. 

try that out, and if you get stuck just tell us where you are and we can help.

---

### Post by locke.dragon on 2007-06-06
ok.  here's the first thing you need to do.  go to...

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

and download the gparted live cd.  then burn an iso of it (just burn it exactly like you did with the ubuntu live cd).

now, from within the ubuntu live cd, go up to the top, hit system>>administration>>gparted, take a screenshot, and post it here.  i'll give you some further advice after that.  

setting up a dual-boot isn't a complicated process, and it doesn't take much much effort on your part, just some free time and patience.  :)

p.s.  you can always do the partition editing from the ubuntu cd, but the gparted live cd is more reliable, and yes, you do need to defrag windows first.  but once ought to do it.

---

### Post by ryanVickers on 2007-06-06
Yes, I would download and burn the live CD (or gparted CD; heard it's got more features), then boot and partition from there (remembering this :)):
> ...first thing is to defrag the hell out of XP.

Then you should be able to put windows files in one partition and ubuntu in the other.
The dule boot is actually completely automatic, just install ubuntu, and if it detects xp on the system, when you boot, you can choose ubuntu or xp from the menu.

---

### Post by locke.dragon on 2007-06-07
basically all you do is defrag windows, resize the windows partition so you have some empty space, and then tell the installer to install in the largest contiguous space.  it does the rest.  :)  let us know if you have any partitioning problems.

---

### Post by steve.horsley on 2007-06-07
Don't do a thing until you have made a backup. 
Repartitioning always carries a risk of error, either by the program or the user. 
And partitioning errors can be stressful.

---

### Post by locke.dragon on 2007-06-07
yeah.  it's a good idea to backup data, but you don't have to go all-out and make cd backups of your entire hard drive.  just make copies of the pictures and documents you can't live without.  you can usually re-build whatever else you lose if something screws up.

---

### Post by antoz on 2007-06-07
Here is a good link
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

All the above posts offer good advice, I personally would do the partitions manually you can split your 60 GIG if this is what you want to do. create one partition "/" for your install one for "swap" about 1.5 times your ram and a good idea is to have a separate "home" partition; this is where all your files and settings will reside (a bit like My Documents in Windows). By having a separate home partition it is easier to to reinstall later, all your files and settings stay intact. Hope this helps, good luck,A.

---

### Post by locke.dragon on 2007-06-07
i don't mean to be rude, but you're telling him the hard way to go about doing it.  all he has to do is shrink the windows partition after defraging and backing up and then let the ubuntu installer do its thing in the "largest contiguous space."  it makes the swap and other partitions, and if you really want, 

[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

follow that guide and create the seperate /home partition AFTER installing.  it's much easier.  we don't need to tell someone who's just installing to do it the hard way!  we'll scare him off!  ;)

---

### Post by arielb_86 on 2007-06-07
thanks for the info let me also give some more in depth....

the WHOLE hard drive is NTSF from which i believe its a problem(with solution) for Ubuntu....maybe that is why when i selected the first option it didnt let me resize anything? im at work now so i cant do anything until probably late tonight or tomorrow.

my parts are:
C: Windows XP
D: HP Recovery Disk
G: files NTSF(or NTSF whatever it is:p) 60 gigs

That G: is the one i want to break up into two....one with the files still as an NTFS and the other part with Ubuntu.

will Gparted will still be able to do? i cant just get it from the ubuntu live cd????
what if i just break that G: from windows xp with another program(Acronix) ? i know i can. if so will the dual boot will still be created?

Thanks!

---

### Post by locke.dragon on 2007-06-07
you can resize that partition however you want.  do it in the way that makes you most comfortable.  if you want to do it in xp, fine, go ahead, it'll still get the job done.  :)

---

### Post by locke.dragon on 2007-06-07
once you've busted that partition in two (no matter which way you do it) just hit install in "largest contiguous space" in the ubuntu live cd installer and let it do it's thing!  ;)

---

### Post by parth32 on 2007-06-07
> **arielb_86 said:**
> thanks for the info let me also give some more in depth....

the WHOLE hard drive is NTSF from which i believe its a problem(with solution) for Ubuntu....maybe that is why when i selected the first option it didnt let me resize anything? im at work now so i cant do anything until probably late tonight or tomorrow.

my parts are:
C: Windows XP
D: HP Recovery Disk
G: files NTSF(or NTSF whatever it is:p) 60 gigs

That G: is the one i want to break up into two....one with the files still as an NTFS and the other part with Ubuntu.

will Gparted will still be able to do? i cant just get it from the ubuntu live cd????
what if i just break that G: from windows xp with another program(Acronix) ? i know i can. if so will the dual boot will still be created?

Thanks!

Yes you can create partition but make sure you DO NOT USE** NTFS OR FAT32** System file. Create RAW Partition. And then you will be able to install Linux on it.


In XP right click on My Computer > Manage > Disk Managment and from there you can create partition. 

[[COLOR="Blue"]This Page[/COLOR]]("http://207.46.196.114/windowsserver/en/library/19a9ac4d-d151-4fde-b187-9f8dfa09cb351033.mspx?mfr=true") might Help you.

---

### Post by arielb_86 on 2007-06-07
> **parth32 said:**
>  Create RAW Partition. And then you will be able to install Linux on it.
What do u mean by RAW partition, dont you always need to set up which type(FAT32,NTFS,other) when the partition is done?
Can't i just leave it as FAT32(i understand that i will have a load of problems if i use NTFS) and install linux there???

-------------------------------------------------------------
If i format the new partition X(where i will install Ubuntu), can it be a FAT32 or does it need to be a specific type?
Also, i heard a lot about the linux swap partition having it to be at least twice as the RAM memory. Is it worthy? why do i need it? I will have a partition that is just files(NTFS) will that be good enought?

If i do the partition in WXP first....will the installation still create the dual boot?


Thanks!

---

### Post by steve.horsley on 2007-06-07
locke.dragon is right. If you can shrink the NTFS partition then the easiest install after that is to simply tell the installer to use the free space and let it make the partitions it wants - it knows the sizes and types it needs. This involves leaving really free space - not allocated to any partition.

---

### Post by locke.dragon on 2007-06-07
and the absolute easiest way to do that in my opinion would be to use the gparted cd.  but, if you feel more comfortable using a windows partitioner, go ahead, as long as you do it correctly, it should work anyway.

---

### Post by ryanVickers on 2007-06-07
> (or NTSF whatever it is)
NTFS (New technology filesystem) came out in win NT (the one thing they made that mght have not been complete s-, oh. :))

---

### Post by steve.horsley on 2007-06-08
> **locke.dragon said:**
> and the absolute easiest way to do that in my opinion would be to use the gparted cd.  but, if you feel more comfortable using a windows partitioner, go ahead, as long as you do it correctly, it should work anyway.

I would normally advise people to use a windows baed partition shrinker, just so that the few that go wrong won't get blamed on Linux and Linux based tools. A lot of windows folk are so nervous of non-windows software that they would blame Linux if a metiorite hit their house while they were running a live CD.

---

### Post by locke.dragon on 2007-06-08
LOL!  nice.  that is a good idea.  try the windows partitioner first, and then if that doesn't work, try gparted.

---

### Post by arielb_86 on 2007-06-08
So to make sure, I need the moral support. I wil break apart my 60 gig NTFS partition into 3 smaller ones....3gig for linux swap...15 ext3(for linux) and the rest as NTFS where ill keep the data.

Sounds good?
So when i go to install ubuntu i will choose the first optino and then i will pick the new 15 gig partition to install...will the installation then set up the dual boot?

---

### Post by neo.patrix on 2007-06-08
I don't know how to to say but can you post details of your current partition table to work out a way to allocate enough space for your root partition (/), /home and ofcourse swap.

In windows System Tools --> Administrative Tools --> Computer Management. There is some tree-node called Disk or Fixes Disk whatsoever. There should be require information

What is important to know is if both HP recovery partition and NTFS Data partition both are located on Extented Partition or they are Primary Partitions. The windows utility signifies these partitions by different colors.

---

### Post by arielb_86 on 2007-06-08
I am wondering though what is the main reason to have the Linux Swap partition(the one that is twice as much as my RAM)?

---

### Post by ryanVickers on 2007-06-08
It is in case your ram fills up completely - without swap, if this happened, it would freeze, and then crash if your lucky - if your not, then you'll have to crash it your self :)

It doesn't have to be twice as much as your ram, in fact usually half as much is good, but I would recommend about 512Mb for most people, and maybe 1Gb if your doing lots of memory intensive tasks.  3Gb is way overkill.  I would say, again, that 512Mb to 1Gb is good, 2Gb max!

but you've got everything right!:
> So when i go to install ubuntu i will choose the first option and then i will pick the new 15 gig partition to install...will the installation then set up the dual boot?
yes, if windows is detected on your computer, it will automatically setup the duel boot.

---

### Post by locke.dragon on 2007-06-08
all you have to do is make the empty space where you want ubuntu on your drive, his "install in largest contiguous space" and let ubuntu do its thing.  it'll set up the swap, the main, and the extended partitions you need, with nothing needed on your part.  :)

---

### Post by ryanVickers on 2007-06-08
Perhaps, but if it was me, I just wouldn't trust the automatic mode - I like to know exactly what it's doing and set it up manually, especially since it's SO easy!!! Hooray!

---

### Post by locke.dragon on 2007-06-08
o...k...  have it your way mr. i take the hard road.  :P  i fully trust ubuntu and the automatic install and it's never given me trouble.  i'll let the guy/gal who actually started this thread decide which he want to use.  ;)

---


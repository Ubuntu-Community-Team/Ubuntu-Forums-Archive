---
title: "Yet another partitioning and file system question!"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by shano26 on 2007-02-06
Hey All,

Just quickly like to say that I am glad to be here and hopefully my (gradual) transition to Ubuntu is a good one!

I was just after some paritioning advice if anyone would like to point me in the right direction.

I recently purchased a new Dell Laptop (Inspiron 6400, 2Ghz processor, 2 Gig of RAM, 100 Gig HD, the standard Intel Wireless) and would like to dual boot Windows XP Media Center Edition and Ubuntu. 

I actually already had a crack at this and can boot into both Ubuntu and XP fine (10 Gig Ubuntu partition, 20 Gig windows, 3 gig swap, and the rest as ext3 using the FS-Driver available for XP. This seems to work pretty good but before I really start knuckling down and playing with Linux/Ubuntu i think i'd like to wipe the hard drive and start from scratch as theres still some residual partitions that Dell pre-install on the computer (a media direct player type thing and a restore partition i believe) that i wasn't really game to delete when i tried it but honestly don't really have a need for (and the media player partition is unusable at present anyway because they use some custom MBR stuff that grub doesn't work with or something and potentially the restore partition as well). I have all the Dell restore CD's and Media center cd so i don't feel i really need the restore partition.

A couple of the questions I have are:

[LIST=1]
[*]Is 10 GB enough for **/** (or is it **\** ) i forget, basically the root partition i think
[*]Is it true that I can't really use hibernate/sleep functions (in windows or Ubuntu)  if I use ext3  for my HOME partition (the one that will be shared between windows and linux) - not really fussed by this would just like to know, i would like sleep functionality if possible though.
[*]Should i use ext2 instead of ext3 for the shared partition? (i heard something mentioned about Journaling on ext3 that isn't really necessary for the setup I'm looking at? To be honest i haven't really looked into what Journaling does yet. Am i missing out if i don't have it?)
[*]Is there a performance hit in using the FS-Driver in Windows as it is not a true Windows Filesystem (i couldn't really notice one on mine)
[*]Are there any other concerns i should have with this setup??
[*] Lastly can i delete/set up all the partitions beforehand using the Gparted Live CD and just do all the installs (windows & linux to there respective partitions) or is it better to install Windows using the whole partition as NTFS and do the resizing/repartitioning as part of the Ubuntu install?
[/LIST]

So essentially what I'm going for is something that will look like this:

All dell related partitions gone!

 / - 10 to 20 GB
 WINDOWS - 20 GB
 /SWAP - 3 GB (does the 1.5x rule still work, im sure with 2GB of RAM this will be plenty but please correct me if wrong!)
 SHARED DATA ( /HOME ) - The rest!


I'm a long time windows user, fairly technically minded and have dabbled with Linux at home/work before but never really stuck with it due to various reasons but now with my own machine (which is all mine for no1 else to use/break!) I would really like to seriously start looking into Ubuntu/Linux and with the goal of eventually making the full switch to be my main OS for use at University and home (and hopefully my relatives spyware infested machines as well!).

If anyone could point me in the right direction it would be much appreciated or if anyone has anything they'd like to comment on or things they would do differently it would be much appreciated!!

Thanks!! :)

---

### Post by randomnumber on 2007-02-06
1. I think so
2. I have never heard of this, I dont know. XP will be on fat or ntfs format, I do not think it will matter to windows.
3.  I think a shared fat32 is easiest. 
4. ?
5. I like to make a separate partition for /home in ubuntu, this is not needed but it makes upgrading to next release of ubuntu easier.
6. I recommend installing windows first, Have windows installer format its own partition that is as big as you want. Then install ubuntu on the free space.

You are going to need

windows partition (ntfs or fat)
swap ( fat32 i recommend)
-------linux
swap (linux swap) <- this is vertial memory 500MB is plenty
/ (root a linux format [ext3]
( I recommend a /home partition for you linux data)

---

### Post by Gadren on 2007-04-18
#2: Not sure -- I haven't gotten hibernate to work in Ubuntu yet, but I have ext3 /home and it's fine in windows.

For #3, I set it up as ext3, then used a program called EXT2IFS to access it from Windows.

---

### Post by mikewhatever on 2007-04-18
> A couple of the questions I have are:

   1. Is 10 GB enough for / (or is it \ ) i forget, basically the root partition i think
   2. Is it true that I can't really use hibernate/sleep functions (in windows or Ubuntu) if I use ext3 for my HOME partition (the one that will be shared between windows and linux) - not really fussed by this would just like to know, i would like sleep functionality if possible though.
   3. Should i use ext2 instead of ext3 for the shared partition? (i heard something mentioned about Journaling on ext3 that isn't really necessary for the setup I'm looking at? To be honest i haven't really looked into what Journaling does yet. Am i missing out if i don't have it?)
   4. Is there a performance hit in using the FS-Driver in Windows as it is not a true Windows Filesystem (i couldn't really notice one on mine)
   5. Are there any other concerns i should have with this setup??
   6. Lastly can i delete/set up all the partitions beforehand using the Gparted Live CD and just do all the installs (windows & linux to there respective partitions) or is it better to install Windows using the whole partition as NTFS and do the resizing/repartitioning as part of the Ubuntu install?

10 GB is a good size to start with. You may need more or less, depending on your personal needs.

Never heard of Ubuntu/Windows /home shared partition. What exactly would they share?

No, ext3 is the way to go.

If FS Driver works, you should be able to write to NTFS from Ubuntu, performance unaffected.

No concerns I know of.

Yes, you can pre-partition the space.

---

### Post by antoz on 2007-04-18
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

These two links offer a lot of info

---


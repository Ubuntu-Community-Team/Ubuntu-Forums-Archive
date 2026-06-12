---
title: "dual boot question"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by pennyminstrel on 2006-07-14
I've been playing with an ubuntu live cd and am just about to take the step of formatting my hard drive tocreate an extra partition so I can run unbuntu on a dual boot basis. 

If I do this will I still be able to access files that I created using windows (assuming of course I'm using compatible applications) Or do I need to copy them all and reload them onto ubuntu? Or will that not work either?

---

### Post by AndyCooll on 2006-07-14
Might be worth looking at the dual-booting link in my signature. That will hopefully anser all your questions.

:cool:

---

### Post by Jax Kovak on 2006-07-14
If you format your drive you will lose ALL of the data that is on it now. If you choose to RESIZE your HD partition to allow you to install Ubuntu AND keep your Windows installation you should be able to keep all your files. This is the setup that I have gone with.

Of course it would be a *really* good idea to make a backup of your important data before you try such a thing.

If you want to take the step away from Windows entirely you will need to backup your data before you start formatting your HD.

---

### Post by pennyminstrel on 2006-07-14
Jax - I wanted to reinstall windows anyway so it seemed a good idea to partition it at the same time ready to install linux and yep I have already backed up.

Andy - I checked out your links and maybe I'm being thick but I couldn't find anything that directly answered the question about whether I'll still be able to access files created in windows or not. Heeeeeeeeeeeelp! 

Gotta go now so i'll check in later.

---

### Post by ProjectGod on 2006-07-14
depends on what files you wish to access... binaries of windows architecture? like exes? no. pdfs? documents like word excel? yes. mp3s? avi? yes.

you'll be able to access them from your linux... if they reside on an NTFS partition only read access. if these files that originated in windows reside on FAT32 then you can read and write them from linux...

if you come back or search the forum you'll see many questions answered about mounting windows partitions...

something nifty is that you can access files created on a linux ext2 / ext3 partition from a window 2k / xp. you just have to install a utility and your set!

[www.fs-driver.org](www.fs-driver.org)

hope this helps

---

### Post by pennyminstrel on 2006-07-14
> **ProjectGod said:**
> depends on what files you wish to access... binaries of windows architecture? like exes? no. pdfs? documents like word excel? yes. mp3s? avi? yes.

you'll be able to access them from your linux... if they reside on an NTFS partition only read access. if these files that originated in windows reside on FAT32 then you can read and write them from linux...

if you come back or search the forum you'll see many questions answered about mounting windows partitions...

something nifty is that you can access files created on a linux ext2 / ext3 partition from a window 2k / xp. you just have to install a utility and your set!

[www.fs-driver.org](www.fs-driver.org)

hope this helps


Thanks ProjectGod.
It was mostly just the documents I was bothered about.

Where would I find them once I was in linux? Or will it be obvious? Thanks for the tip about accessing linux files from windows too. Not sure I quite understand it yet but no doubt it'll become clearer once i'm there.

I'm sorry if I sound thick sometimes, but it takes me a while to absorb all the new stuff and although I know there's a lot of stuff on the forums it's very hard to find exactly what you want sometimes and I'm not happy going ahead unless I know exactly what I'm doing! I feel like I want somebody to hold my hand while I do it all the first time.

---

### Post by ProjectGod on 2006-07-14
by default linux will not show you the documents / files located on a windows (NTFS) or FAT partition. you'll have to create a directory and physically mount them using a few simple commands to "reveal" them. after this you will be able to access the stuff on those partitions. 

its easier from a windows point of view because you just install a software and it automatically detects ext2/3 partitions that you can READ and WRITE to ... its like installing a driver for a scanner... simple wizard driven stuff. 

for steps on linux accessing windows partitions... check out.

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

search for NTFS... it'll show you the automount option and the manual mount option ... both very easy. 

say your windows is installed on PRIMARY MASTER and your ubuntu on PRIMARY SLAVE... if your confused with these terms... just think of them as FIRST HD and SECOND HD. anyway. you'll have to mount /dev/hda1 ... assuming windows is occupying the whole HD and is partitioned as one large partition.

lets us know how you go.

:)

---

### Post by theo_man on 2006-07-14
I have a problem: trying to load ubuntu from the disc I received and it goes until power configuration and then goes back to the beginning: what can I do?

Theo_man

---

### Post by ProjectGod on 2006-07-14
hiya theo_man. since this thread has been answered... and because of its typical title..."dual boot question" highly likely that your post will not be checked by anyone... they tend to usually read the first post.

i suggest you start a NEW thread and be as descriptive as possible. like the PC your using, the CD whether it was shipped or downloaded... at what speed you burnt the ISO image file etc... 

i'm not saying no one will answer it here... but if you start a new thread you have a better chance to get a response and perhaps a solution. here it will just fade into oblivion.

---


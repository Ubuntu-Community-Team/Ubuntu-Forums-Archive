---
title: "Hard Drive Space suggestions"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by Sq322 on 2006-06-09
Ok here it is, 
I am working off of a brand new 120gb HD.
My WinXP is installed in the first slot taking up appx 45 gb. It is currently formatted NTFS.
I am looking to install Dapper now using some of my remaining space.
I would install a [/] partition as well as a [/home] partition and a 1gb [swap]  partition [based on my 512mb of ram].
Should i also format a FAT32 partition for file sharing ?

what sizes should i be making these partitions ?

Thx in advance

[my intention is not to upgrade EVERY time a new version comes out, but to stay somewhat current]

---

### Post by nanotube on 2006-06-09
[QUOTE=Sq322]Ok here it is, 
I am working off of a brand new 120gb HD.
My WinXP is installed in the first slot taking up appx 45 gb. It is currently formatted NTFS.
I am looking to install Dapper now using some of my remaining space.
I would install a [/] partition as well as a [/home] partition and a 1gb [swap]  partition [based on my 512mb of ram].
Should i also format a FAT32 partition for file sharing ?

what sizes should i be making these partitions ?

Thx in advance

[my intention is not to upgrade EVERY time a new version comes out, but to stay somewhat current][/QUOTE]

so basically, you have 75g free, eh. (i still remember some arithmetic)
well, make the / partition of about 7-10 g, your 1g swap (sounds reasonable) and leave the rest for /home

for sharing files between winxp and linux, just install fs-driver ([http://www.fs-driver.org/](http://www.fs-driver.org/)) on windows, it will allow you to access the ext3 linux filesystem.

if you prefer to go the fat32 route, then snip off about 15-20 g from home and make it into a separate fat32 partition.

---

### Post by Sq322 on 2006-06-09
[QUOTE=nanotube]so basically, you have 75g free, eh. (i still remember some arithmetic)
well, make the / partition of about 7-10 g, your 1g swap (sounds reasonable) and leave the rest for /home

for sharing files between winxp and linux, just install fs-driver ([http://www.fs-driver.org/](http://www.fs-driver.org/)) on windows, it will allow you to access the ext3 linux filesystem.

if you prefer to go the fat32 route, then snip off about 15-20 g from home and make it into a separate fat32 partition.[/QUOTE]

Thx for the quick response.
Can you tell me the pro's and con's of partitioning some space with FAT32.
I am preferring to make Ubuntu my main daily OS and just VMware into XP when i need to run some work related apps..

---

### Post by nanotube on 2006-06-09
[QUOTE=Sq322]Thx for the quick response.
Can you tell me the pro's and con's of partitioning some space with FAT32.
I am preferring to make Ubuntu my main daily OS and just VMware into XP when i need to run some work related apps..[/QUOTE]
well, the only real cons of making fat32 partition is that you have to take the trouble to make that partition, and that fat32 does not support unix-style file permissions, so all files on that partition will have one set of permissions. also, there is the 4gb filesize limit on fat32. 

the con of using the fs-driver, is that you have to install yet another piece of software on your windows :), and that you have the opportunity of screwing up your linux install, if you mess around with the system partition.

---

### Post by aysiu on 2006-06-09
My thoughts:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by brentoboy on 2006-06-09
[QUOTE=nanotube]there is the 4gb filesize limit on fat32. 
[/QUOTE]

there the 4GB limit was fat16
I have a 16GB fat32, and it works great.

I trust linux to take better care of my fat32 drive than I trust windows to play fair with my ext3 drive, but that's just me.

---

### Post by nanotube on 2006-06-09
[QUOTE=brentoboy]there the 4GB limit was fat16
I have a 16GB fat32, and it works great.

I trust linux to take better care of my fat32 drive than I trust windows to play fair with my ext3 drive, but that's just me.[/QUOTE]
please re-read what i said. :) i did not say that the 4gb limit was on the size of the fat32 partition. it is on the maximum size of the files that you can store in it. 
refer to [http://en.wikipedia.org/wiki/File_Allocation_Table](http://en.wikipedia.org/wiki/File_Allocation_Table) for details, if you wish.

but yes, i am with you on not letting windows touch anything on my linux partitions with a 10foot pole. but that's just me (and you). :) but i have heard favorable reports about that fs-drive thing.

---

### Post by Sq322 on 2006-06-11
[QUOTE=brentoboy]there the 4GB limit was fat16
I have a 16GB fat32, and it works great.

I trust linux to take better care of my fat32 drive than I trust windows to play fair with my ext3 drive, but that's just me.[/QUOTE]
I concur with being more comfortable with linux taking care of fat32 than windows with ext3 files

---

### Post by treris on 2006-06-12
I'm running a total of 5 hdd's and something like 8 partitions while dualbooting between winxp and kubuntu. I rarely use winxp anymore, but occasionally I still boot it to play some games or help someone out with a winxp related problem (unfortunately I haven't been able to convert all of my friends and family into linux users yet).
I've got most of my partitions set up with FAT32 because it allows me to easily work on all of my drives, so far I haven't had a problem yet with FAT access. Only downside to FAT from my point of view is that every once in a while I still have to go into windows and defragment those partitions and supposedly there is a speed difference when copying large files from ReiserFS (my kubuntu partition) to FAT but i'm not sure about that and I can't really say I'm noticing it

I'd say if you have to dualboot then create a FAT32 partition, because appearantly I'm not alone in not wanting windows to have anything to do with linux partitions and linux has FAT32 support build in anyway

---

### Post by Sq322 on 2006-06-12
[QUOTE=treris]

I'd say if you have to dualboot then create a FAT32 partition, because appearantly I'm not alone in not wanting windows to have anything to do with linux partitions and linux has FAT32 support build in anyway[/QUOTE]

Since my laptop is a Dell, there is already a FAT32 partition in there. Should i just resize that one larger, or create a new one?

---

### Post by anaconda on 2006-06-12
> 
I trust linux to take better care of my fat32 drive than I trust windows to play fair with my ext3 drive, but that's just me.

Well the good part about the ext3-driver for windows is that windows doesnt do anything to those ext3-drives (no autocleaning, autoconfiguring, auto-defrag or auto-anything) so it is just for reading/writing from/to ext3 partitions.

I dont make FAT32-partitions anymore.. (exept that my USB-HDD has ~30GB fat32-partition, because I sometimes have to use it in other windows machines.. )

---

### Post by Sq322 on 2006-06-12
[QUOTE=anaconda]Well the good part about the ext3-driver for windows is that windows doesnt do anything to those ext3-drives (no autocleaning, autoconfiguring, auto-defrag or auto-anything) so it is just for reading/writing from/to ext3 partitions.

I dont make FAT32-partitions anymore.. (exept that my USB-HDD has ~30GB fat32-partition, because I sometimes have to use it in other windows machines.. )[/QUOTE]
You are referring to the FS-Driver correct?

---

### Post by anaconda on 2006-06-12
correct..

---


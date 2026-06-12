---
title: "How should i dual boot?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-21
I will be installing  dual boot on a Dell Inspiron laptop:
Pentium 4 - 2.2Ghz
512Mb RAM
30Gb HD

I need some explanation on how much space i should allot my windows partition as well as my Ubuntu partition.  I will probably be splitting my usage 50/50 (xp/linux) as i am still a beginner and learning about ubuntu and its limitations.  The only thing i will need to store on my local HD is the OS, software, and some minor documents(pictures, word documents, spreadsheets) I will not be storing an extensive amount of music/video on my local drive, as i have another 30Gb HD externally for this use.

With the information given, can someone help me decide how much space i should allot to my /, /home, and SWAP partitions??  And how much space to leave windows.  

P.S. this will be a complete wipe of the machine prior to installing any of the OS'

Thanks

---

### Post by BHelts on 2007-06-21
start windows install, partition through windows installer 15GB to windows and install on that partition.
start ubuntu install, choose manual partition.
create a new partition ext2 size 5-7 GB with mount point /
create a new partition SWAP and make it 2x the amount of ram you have.
create a new partition ext2 size rest of drive with mount point of /home

that's how i'd do it.

---

### Post by alienexplorers on 2007-06-21
Follow what BHelts said.  Just make sure you run manual partition so you don't overwrite windows.

---

### Post by ITdrummer on 2007-06-21
I have been through many windows xp format/re-install processes and i dont ever recall it asking me about partition sizes.... doesnt it automatically choose?

---

### Post by aeiah on 2007-06-21
i cant remember where you'd need to go to create a small partition for windows within the windows installer, but worry not. you could install windows to a partition that takes up the entire 300gb.

when you boot to the ubuntu livecd, before installing ubuntu, use the partition manager to resize your windows partition to the size you want. what was suggested sounds good, although you should take into account how much space your existing windows install takes up. you may have a load of games, for example.

---

### Post by ITdrummer on 2007-06-21
> **aeiah said:**
> i cant remember where you'd need to go to create a small partition for windows within the windows installer, but worry not. you could install windows to a partition that takes up the entire 300gb.


only 30 GB.

So let me get this straight. I can install windows on my freshly formatted machine with the default settings (using entire hard drive i am assuming). Then whenever it is finished, i will reboot with my ubuntu 7.04 alternate desktop cd to install ubuntu.  At the partitioning screen, i will choose manual partitioning(to make sure i dont erase windows) then i > **BHelts said:**
> 
create a new partition ext2 size 5-7 GB with mount point /
create a new partition SWAP and make it 2x the amount of ram you have.
create a new partition ext2 size rest of drive with mount point of /home



Is this pretty much the gist of it?

---

### Post by ITdrummer on 2007-06-21
and one more question.  When i am done, my windows partition will be 15 gb and my ubuntu partitions will be 15 gb.  Does this mean, when running windows i will only have 15 gb available, and when running ubuntu i will also have 15 gb available.  And by available i mean, will i only have 15 gb of space to save programs, photos, docs?

---

### Post by Eldar11 on 2007-06-21
yes you will only have the size amount alloted to each partition

---

### Post by buuntuu! on 2007-06-21
hi there.
in theory you will only have 15gigs for each install, as xp does not recognize linux filesystems and linux can read from but not write to ntfs.
you could however format your windows-partition as fat32 and ubuntu will read/write to it, 
or install ntfs-3g in ubuntu which provides it with read/write access to ntfs also (but it's a new driver and there is still some discussion about whether it is stable yet)
or you could install fs-driver which gives you access to ext3, a common linux filesystem from windows (stable)
...
there are many options, each has its downs and ups. read [here]("http://www.psychocats.net/ubuntu/partitioning") for detailed info!

---

### Post by ITdrummer on 2007-06-21
So, lets say i go through with the whole dual-boot route and 6 months from now i make a decision on which OS I want to stick with. To completely shift to either windows or Ubuntu, will i have to format the entire drive and start from scratch? For the sake of argument, lets say i decide to choose Ubuntu as my full-time OS in 6 months.  Will i be able to format my windows partition  and add that space to my Ubuntu Install so it will have all 30Gigs available, of will i need to start from scratch and partition the entire drive?

---

### Post by buuntuu! on 2007-06-21
you will not need to reinstall again. if you decide to keep ubuntu it will be easy: wipe xp, eventually change your partition sizes, edit your grub menu, done.
if you decide to keep xp it will be (nearly as) easy: wipe ubuntu, restore your MBR (where xp's bootloader resides), done...
read [here]("http://www.users.bigpond.net.au/hermanzone/p18.htm") on the details.

you will not want to dump ubuntu though, i'm quite sure about that ;)

---

### Post by ITdrummer on 2007-06-26
when im setting up my partitions for ubuntu, it asks if i want my partitions to be logical or primary, which ones are which?

---

### Post by ITdrummer on 2007-06-26
Then it asks if i want it at the beginning or end?  please tell me the answers to these questions for each partition i should create.... i need help please!

---

### Post by ITdrummer on 2007-06-26
and when i try to name to mount point, SWAP, it tells me that i "have entered an invalid filename, filenames must begin with /"

---

### Post by ITdrummer on 2007-06-27
Ok, i have my SWAP partition figured out.  Here are my partitions as it stands:

Partition #1: 15.0GB  Primary   Windows
Partition #4: 8.0 GB   ext3       Primary     /Home
Partition #2: 6.0 GB   ext3       Primary     /
Partition #3: 1.0 GB                 Primary     swap
  Does this look sufficient for a 30 GB hard drive?

---

### Post by drowner on 2007-06-27
it looks fine.

personally I would have given a bit mnore to / and a bit less to /home, because you are probably going to store data on your XP drive for now.

You might want to invest in an external HD to store picture/music/backup. they're quite cheap these days.

---

### Post by drowner on 2007-06-27
Actually, its more commmon to put the swap partition as logical in an extended partition, and you could put /home  in there too, but i dont think it really matters.

---

### Post by ITdrummer on 2007-06-27
> **drowner said:**
> it looks fine.

personally I would have given a bit more to / and a bit less to /home, because you are probably going to store data on your XP drive for now.

You might want to invest in an external HD to store picture/music/backup. they're quite cheap these days.

I have an external 30 GB hard drive I use for music  and file storage.  As I said above, the only thing I will store on my windows partition is documents, some programming software(Visual Basic) and a few games. Is it normal/Ok for all of my partitions to be ext3? Should they be different?

> **drowner said:**
> 
Actually, its more common to put the swap partition as logical in an extended partition, and you could put /home in there too, but i don't think it really matters.


Would you mind explaining this in a bit more detail.    I am still learning about partition management and I don't quite understand what you mean.

Sorry if I am being difficult.

---

### Post by drowner on 2007-06-27
> **ITdrummer said:**
> I have an external 30 GB hard drive I use for music  and file storage.  As I said above, the only thing I will store on my windows partition is documents, some programming software(Visual Basic) and a few games. Is it normal/Ok for all of my partitions to be ext3? Should they be different?



Would you mind explaining this in a bit more detail.    I am still learning about partition management and I don't quite understand what you mean.

Sorry if I am being difficult.

No problems ;)

The Windows XP partition should be formatted 'NTFS'

The Linux partitions, both /home and / should be ext 3. Quite right.
The Swap partitionm is just 'swap'
The external data storage device should be 'Fat32' for ease of use between the two. Keep your documents there.

And then I would make the /  partition maybe 8gig, but it doesnt REALLY matter.

Now,   there are two sorts of partitions, primary and logical. I'm not really heaps smart about this, but i'll explain what i know, if im wrong, someone please jump in. You can only have like 4 primary partitions on a drive,  but you can make as many 'logical' partitions as you like within  an 'extended' partition. 

So make an 'extended' partition at the the end, and put inside that partition 2 'logical partitions, one for /home, and one for swap.

if you like, it doesnt REALY matter, if you only have 4.

(is that right?)

---

### Post by drowner on 2007-06-27
Actually i'm not sure if its 100% right, but i think the point is made ;)

---

### Post by ITdrummer on 2007-06-27
> **drowner said:**
> No problems ;)

 You can only have like 4 primary partitions on a drive,  but you can make as many 'logical' partitions as you like within  an 'extended' partition. 

So make an 'extended' partition at the the end, and put inside that partition 2 'logical partitions, one for /home, and one for swap.


 How do i make an extended partition and how do i put partitions within other partitions?  And when you say "make 2 logical partitions, one for /home and one for swap", does that mean i will have 2 home partitions and 2 swap partitions.  (the ones i created primary and the ones i created logical?)

---

### Post by ITdrummer on 2007-06-27
Im sorry, that was really confusing. I have another question. Is the setup i have currently ok? Or should i change it to the way you mentioned?

---

### Post by drowner on 2007-06-27
it will look something like this:

Partition one: Primary - NTFS (windows)
Partition two: Primary - ext3 (linux '/')
Partition 3: Extended, containing:
----------------------------------------logical - ext3 (/home)
--------------------------------------- logical - swap


If you are installing with the live cd, gparted will make it all very nice and clear for you.

You basically pick the partition you want to edit, resize it, click the blank area, and then make the new one

But like I said, there is no need to make an extended partition if you are going to have only 4 partitions

aysiu, once again, explains it beautifully:

[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

And good guide to installing too ;)

---

### Post by drowner on 2007-06-27
> **ITdrummer said:**
> Im sorry, that was really confusing. I have another question. Is the setup i have currently ok? Or should i change it to the way you mentioned?


Your setup would work just fine.

The only reason people would recommend an extended partition is if you wanted to have a fifth partition, say, a shared partition.

But, go for it

Don't forget: if you mess it up, it can be fixed, particularly if you are starting with a clean windows install.

You can just reinstall ubuntu as many times as you like ;)

---

### Post by dptxp on 2007-06-27
Defragment The Drive, I assume you have one partition of 30 GB.
Backup Data.
Run Live CD, Click Install.
Select Manual Partition.
Resize The partition to 8 GB. Enough for Windows and a lot of Windows Program.
Resize next 22 GB left to 6 GB (Primary). Mount as / and format as EXT3
Resize next to 15 GB (whatever you got minus 1 GB for SWAP). Mount as /DATA (or whatever you want)
You can mount as /home too. Format in EXT3. You will need a small program in Windows for r/w to EXT3.
Set rest as SWAP(1-2 GB).
Make sure that 'FORMAT' for the Windows partition is not ticked.

---

### Post by ITdrummer on 2007-06-27
Another quick question, there are several options when i am setting up the partitions, such as: 

Use as:
Mount Point:
_Mount options_:
_Label_:
_Reserved Blocks_:
_Typical usage_
_Bootable flag_:
Size:

How should i set the underlined options?
Should all the partitions have the same setup?

---


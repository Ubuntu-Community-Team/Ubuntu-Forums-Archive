---
title: "Making windows and linux play nice"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by SoftTaco on 2007-01-05
I want to Dual-Boot Linux and Windows

In my computer I have a 160GB HD and a 250GB HD, I am about to completely reformat and setup from scratch.

What I would like to do is split the smaller drive and load Windows XP and Linux on there and use the 250GB for storage. But I have three concerns

First, when dual booting is it better to let windows handle the boot selection or Linux, I’ve seen a bunch of tutorials that let windows boot but none the other way.

Second, what is a good partition size for Ubuntu? I intend to use the large drive entirely for storage so I only need room for the distro and all the apps I’d like to pickup. I’m looking at trying to do a lot of video editing and animation under Linux with apps like Blender. But I also want to still have enough room left for the windows partition to install the games I like to play often, Half-Life 2, Company of Heroes, Oblivion, and a bunch of other graphically demanding (big) games. I know this is a complex question that tends to vary from person to person, but I rough idea of the space the distro tends to take up, or your own personal experience would be greatly helpful.

Last, I would like to set up the second drive as a storage partition that both Operating Systems could see and share. In other words I want to be able to make a file in Linux and open it in windows or vice-versa

---

### Post by krajni on 2007-01-05
as far as the boot loader goes partion your 160 gb with any good tool (dont forget a third small partition--1gb-- for linux swap area like i did first  time)  install windows first then linux and when it prompts allow it to install GRUB boot loader.....i found doing it the other way around is too much for ntloader to handle and the last time i tried linux first  xp didnt even recognize that there was another operating system present....

the drive sharing....do NOT go ntfs i am having major problems reading my ntfs partition in ubuntu

---

### Post by jvc26 on 2007-01-05
Ok well first my advice would be you could go for a nice 50-50 split:
NTFS partition for your Windows - 80GB?
ext3 partition for your Ubuntu - 80GB?

Then your storage disk either FAT32 so that both can access the drive easily (from the box as it were), or alternatively NTFS and use the Ubuntu NTFS read-write drivers to run the NTFS system from Ubuntu. (Note these are beta, but have been informed earlier that they seem to work with no probs) Here: [http://ubuntuforums.org/showthread.php?&t=217009](http://ubuntuforums.org/showthread.php?&t=217009)

However, as you are going for a 250GB accessible storage for the both of them, You wont need anything like 80BG for Ubuntu - I'd say you could probs get by with even as little as 20GB - I have only used 20Gigs on mine and thats including almost all of my most used files (I boot 100% Ubuntu now with no XP) but go for a conservative 50 and I'm sure you'll be fine :)

So maybe go for a:
Small 160GB Drive
Windows: 110GB (NTFS)
Ubuntu: 50GB (ext3)
250GB drive
Storage: 250GB (NTFS/FAT32)

Finally, install XP first, then Ubuntu. Use GRUB as your bootloader as its better than trying to get the windows bootloader to play properly running Ubuntu - It caused me a lot of problems when I dual booted so instead I just went with using the GRUB Bootloader (The ubuntu one)

Ubuntu has been in my experience very light on storage (what takes the space is your files not the OS and the apps - I have seen a post somewhere on here which mentioned most of the repos would take up only about 5GB!)

Anyway, good luck and enjoy!
Il

---

### Post by forgetso on 2007-01-05
This is exactly what I am going to do as well except I have 2 160Gb drives, one for storage.

> **krajni said:**
> the drive sharing....do NOT go ntfs i am having major problems reading my ntfs partition in ubuntu

My storage drive is already formatted as NTFS and there is no way I am burning 160gb to disc.  What problems are you facing?

---

### Post by jvc26 on 2007-01-05
> **krajni said:**
> 
the drive sharing....do NOT go ntfs i am having major problems reading my ntfs partition in ubuntu

Just a brief note: Are you trying to read/write with NTFS? - You cant out of the box with ubuntu - NTFS is a proprietary filesystem of MS creation. See my above post for the link, but to read/write you have to get the drivers, otherwise it will not work. Easiest probs to go FAT32 but have been told that fragments pretty quick but of the details of this I'm not sure.

Il

---

### Post by meng on 2007-01-05
I second that comment. I have NO troubles reading NTFS from Linux, but I don't need to write to NTFS (which isn't supported by default).

Install Windows FIRST, then install Ubuntu. The Ubuntu bootloader (grub) will overwrite the Windows bootloader, but will actually permit dual-booting (which the Windows one won't).

---

### Post by krajni on 2007-01-05
> **forgetso said:**
> This is exactly what I am going to do as well except I have 2 160Gb drives, one for storage.



My storage drive is already formatted as NTFS and there is no way I am burning 160gb to disc.  What problems are you facing?


That was how i got in this mess...my  partition for *.mp3 storage was already in ntfs b4 i started with ubuntu....tryin only to get read access not r/w i cant seem to get users other than root user access to my ntfs partition  --see thread "help accessing ntfs partion plz"  for all details

---

### Post by pseudonym on 2007-01-05
With your drive setup (almost identical to mine) I would opt for one OS per disk. If you put both on one disk one OS ends up being on the slower half of the disk. In my experience it's always best to have the 'system' part of any OS at the beginning of the disk, because that's the fastest part of it.

For dual-booting you should always install windows first, on the primary disk controller (SATA or IDE) and with your second disk not plugged in. It tends to like that anyway. this way you will always have the windows bootloader undisturbed in its own master boot record (MBR). It's easily fixed with the windows install disc if it does get overwritten by accident, but this way things are more clearly separated.

On my system I devote the whole 120GB of my disk to windows, with no other partitions. But I just use it for [playing games]("http://www.ubuntuforums.org/showpost.php?p=1929486&postcount=22").

Then plug in your linux disk as the primary disk and install Ubuntu, with windows now connected as secondary. Partition how you want, but the following is always a good scheme - ```
Root|Swap|Home|Others if you use them|shared fat32
```
You only need 512mb of swap, btw, unless you want to use suspend-to-disk or hibernation, but even then 512mb may be enough (you're likely to never use it, but it's good to have it there anyway).

Your shared partition should always be fat32, and can be as large as you need, subject to fat32's 32GB limit, of course. Mine's only about 10GB because I don't have much need for it, just storing some game demo files and game patches, plus windows system stuff like copies of drivers etc. 

Ubuntu will detect windows and configure it's bootloader to chainload to the second disk. You should install the GRUB bootloader into the master boot record of your linux disk, too, btw.

When your installation is done you will be able to boot whatever OS you want from the GRUB menu.

Enjoy! :)

---

### Post by SoftTaco on 2007-01-05
cool, thanks guys

also i have been using dapper and just wanted to ask if edgy is stable now  
 
and 

what is linux swap partition for?

and 

how do i set which os boots by default?

---

### Post by pseudonym on 2007-01-05
> **SoftTaco said:**
> also i have been using dapper and just wanted to ask if edgy is stable now
no probs here apart from the version of my distro's burning app (xfburn) I had to use the dapper version but it's no big deal.  
 
> **SoftTaco said:**
> what is linux swap partition for?
It's linux's
[virtual memory]("http://en.wikipedia.org/wiki/Virtual_memory#Swapping_in_the_Linux_and_BSD_operating_systems").

> **SoftTaco said:**
> how do i set which os boots by default?
If you do things the two disk way, make sure your linux disk is configured in your bios to boot before other hard disks (but after your floppy and CD/DVD drive). When it boots there is a menu to choose which os you want.

---


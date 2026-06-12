---
title: "Seeking re-assurance before I install a dual boot"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-05-12
Please excuse the relatively lengthy posting: I wish to be clear.

I am slowly converting all of the 4 PCs on my small home network to Ubuntu, and now get to my first case of dual boot: it's my son's new machine and he has a lot of Windows games he wants to keep, so I'm going to learn how to do a dual boot. Please also excuse the paranoia- I'm a little worried by this and would like some re-assurance that I'm not going to screw his XP installation up. The last thing we need is family ructions about operating systems!

He has one large HD which is partitioned as C (for windows) and then D,E and F, but he only uses C. It's all been done by Windows, and the partitions are all NTFS because that's what happened when we installed XP. The disks D Eand F were invented for the ubuntu installation, and have never yet been used. They are respectively in gigabytes 50 20 and 5 (for the swap space?: is that what it's called?)

After defragging his C disk, I loaded the feisty live CD and it found all of the hardware quite happily. So I moved on to install- but I aborted because of a momentary paranoia: I could no longer understand clearly which of the hard disks it wanted to modify, and it asked me a whole series of difficult questions about what disk format to use . How can I be sure it's not going to overwrite his windows partition? Should I scrub out disks DE and F before starting?  What disk format should I choose? I see that ext3 is often talked about, but I don't know.

So- thanks for answers to my paranoia!

---

### Post by ladida on 2007-05-12
I'm curious too. Bumping this thread.

---

### Post by louieb on 2007-05-12
if D, E and F are empty. You are in good shape on this PC.  I have the most trouble when I have to shrink a partition which you don't have to do. 
What I would do if I were you.[LIST]
[*]Choose manual partitioning.
[*]Delete the 20 and the 5 gig partitions. This leave you with 25 gig of unallocated space.
[*]Click on the unallocated space and create an extended partition using all 25 gig. (this gets around the problem of the 4 primary partition limit).
[*]Now create 3 logical partitions inside the extended partition for / /home and swap.
[*]7- 10 gig for /   (format ext3)
[*]1 gig for swap   (format swap)
[*]balance for /home (format ext3)
[*]click apply[/LIST]The next screen you select you mount points. Be sure to remember the name GParted gave you after partitioning.   
Just be careful that you don't format you c and d drives (probally called sda1 and sda2)   there is a check  box for that. 
Daughter graduates from college today gota go but that should get you started.

---

### Post by CongoJim on 2007-05-12
I have to use dual boot because my computers are used to teach students in the Congo and they have to learn to fix windows so I have XP on them.

Grub will give you a very simple menu to boot from and is installed automatically when you install Ubuntu. For ease, install Ubuntu after windows. I use GAG for a nicer boot menu but takes a little extra effort to install unlike Grub which I emphasize, is done entirely for you during install. 

Fear not. I find boiling water is far more complex.

---

### Post by CongoJim on 2007-05-12
[QUOTE=louieb;2640358]if D, E and F are empty. You are in good shape on this PC.  I have the most trouble when I have to shrink a partition which you don't have to do. 
What I would do if I were you.[LIST]
[*]Choose manual partitioning.
[*]Delete the 20 and the 5 gig partitions. This leave you with 25 gig of unallocated space.]

At this point why not just accept changes and then let Ubuntu "Use largest unallocated space to create the needed drives?

---

### Post by sandman55 on 2007-05-12
Hi ginestre you have plenty of disk space which is good (I'm jealous :D ) your 5 gig for swap is a bit big people usually use twice their ram I have 512meg of ram my swap is 1 gig you wouldn't want more than 2gig for swap and when you format it during install its called swap the othe two 20gig for root refered to as / format this as ext3 and the 50 gig for Home format as ext3 write down the sizes of all your partitions to identify them in particular the windows partition what size is that not the same as one of your other ones, it should be called sda1 or hda1 depending what type of drive  PATA or SATA.
if your not installing feisty 7.04 but one of the earlier you could do with another partition formatted fat32 to transfer files between windows and linux the size is up to you I have kept my fat32 partition even though I now have Feisty.
When you get to the 3 options about preparing disk space choose to do it manually see this [Link ](http://www.psychocats.net/ubuntu/installing) because its good to have your home and your root on separate partitions that way if you upgrade or do a reinstall you only upgrade your root and you are left with all your documents on your home partition intact.
when you get to where it shows you all the partitions make sure root (shown as / ) and home and swap are on the partitions you want them to be if not change it also make sure they will be formatted root ext3 home ext3 swap as swap and **_make sure only these three have a tick next to them for to be formatted_** you can go back from here but once you format there is no going back. I don't mean to frighten you because its really quite straight forward easier than windows. I leave every thing turned on during install example printer so that hopefully it finds  everything. 
Here are some good [Link](https://help.ubuntu.com/community/WindowsDualBoot) [Link](http://www.psychocats.net/ubuntu/) from some of the more knowledgeable people here I'm still a learner but Ive installed 4 versions of Ubuntu some several times and I feel confident in that and the most important point I can emphasise is where you put a tick (I think Americans call it a check) for the partitions to format Good luck

---

### Post by ladida on 2007-05-12
If you check the partition, it will be formatted, right? That means everything in it will be wiped out?

If I have an existing partition with a lot of files, how do I shrink it? I have the 7.04 livecd, on the prompt where it asks me "How do you want to partition the disk?", I chose "Manual" and I was then presented with a list of my existing partitions. I don't exactly understand how to resize them. When I click "Edit Partition", the installer shows me a prompt asking which memory type and mount point I want.

Thanks.

---

### Post by john.ie on 2007-05-12
Did exactly what you are doing last Friday, and I can tell you I was a lot more than a little paranoid.
However,  the installer/partitioner works very well. Indeed, it even takes a peek into your Windows and ask you if you want some of your profiles etc imported into linux....nice touch huh ?

What I did was print off a whole load of advice, reviews and dual boot stuff from the net (especially here). I also found screen shots of the installer steps.....if memory serves it was on the Softpedia web site. I was imagining the worst case scenario whereby I could'nt access Windows OR Linux....see I told you I was more paranoid than you :) 

Follow all the good advice above & Good luck.

---

### Post by sandman55 on 2007-05-12
Thats right if you check the partition everything will be wiped out If you want to work on your partitions example shrink your partition to make space for more partitions boot up with your live cd  when it boots up dont choose install go to the top of your screen to System and either under Preferences or Administration you will find gparted with it you shrink your existing partition and with the remaining space you make all of it an extended partition  and within the extended partition you make your partitions be they one partition or several partition think of the extended partition as a container for your partitions. I personally havent used gparted Ive used Acronis Disk Director but gparted looks straight forward.
Or you could use the first option as shown [Here](http://www.psychocats.net/ubuntu/installing) half way down the page I have only used the third option because I like to have three partitions swap root (/) and Home that way if I reinstall I only install root and leave my home intact (I only check root and swap but on a completely new set up you will obviously have to format home as well)

---

### Post by louieb on 2007-05-12
> **CongoJim said:**
> At this point why not just accept changes and then let Ubuntu "Use largest unallocated space to create the needed drives?
Because the default partition scheme does not create a separate /home partition. 
I play around a lot and sometimes have to reinstall. having a separate home keeps my data safe after I screw something  up.

---


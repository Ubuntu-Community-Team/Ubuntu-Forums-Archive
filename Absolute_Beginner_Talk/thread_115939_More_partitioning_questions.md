---
title: "More partitioning questions"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by seakiwi on 2006-01-11
Hi again  :)

I'm about to install Ubuntu - hopefully today if my new hard drive ever arrives.

I've been reading heaps of information from various links I've stumbled over plus many that people have pointed me to. I think I have my head around most of what I need to know to get this installed and up and running.

The only thing that's concerning me now, is the partitioning part of the install and GRUB.

I'm installing Ubuntu on my new second HD so at least I don't have to be messing anywhere near Windows to do this.  What I need to know is ...

If I let the installer automatically do the partitioning, how many partitions will it create and what size?  What's the default? I was thinking of doing it manually and setting it up as follows but I really don't have a clue what I'm doing:

/ (boot)  5 GB
swap  2 GB
/home 10 GB (or more)
FAT 32 ( so that I can read/write to Windows files)  5 GB

My drive will be an 80 GB drive so I have an overkill of space but I'd like to get it set up the best way possible initially so that I don't have to worry about repartitioning it later.

Could someone who REALLY knows what they're doing please give me an idea of how best to do this? The other thing I'm never sure about is the file system for each partition ext 3? (no idea what that actually means)

The other thing thats worrying me a bit is GRUB. I've probably been reading too many  "Help! I can't boot to Windows!"  posts, but messing about with the MBR scares me. Is there an option within the install process to create a boot floppy/CD instead of installing GRUB? I'd be happy just booting into Ubuntu from a boot disk if that was an easier option - I did that with Mandrake after not managing to get LILO to work.

I know I'm repeating some of what I last posted here, but I still don't feel that I have this aspect of the install sussed out quite yet. I just prefer not to have any "surprises" once I've started the installation.

Many thanks for all your help. Great forum! :)

PS. Oh, btw - I'll be the only user on this machine, if that's relevant.

---

### Post by jorn on 2006-01-11
Hi!
The more surprises you get, the more you learn. When I was a beginner I dit a reinstall several times. Just do the partitioning as you think it's the best. Your suggestion is not bad.
Jorn

---

### Post by manicka on 2006-01-11
You'll probably need to choose manual partitioning during the install to set things up just the way you want. An automatic install won't setup the fat32 partition for you. The process is fairly straight forward.

You'll want to choose Ext3 for your / and /home partitions, 'swap' for your swap partition and fat32 for your shared partition.

Don't be to worried about grub, it's never given me any grief.

---

### Post by aysiu on 2006-01-11
80 GB hard drive?
I'd recommend this partitioning scheme:

6 GB /
2 GB /home
1 GB swap
71 GB FAT32

Do not let Ubuntu's installer partition automatically--pick your own sizes and partitions.

If you're really worried about not being able to boot into Windows, I wouldn't install Ubuntu just yet. I would play around with the live CD for about a week--get comfortable with Ubuntu. Make sure it works with your hardware. Get to know the interface. See if you can accomplish your daily tasks in Ubuntu.

Once you're pretty confident Ubuntu suits your needs and your computer, go ahead and install it. Grub on the MBR will almost always add Windows to the boot menu, and if you know Ubuntu well enough by then to be comfortable using it, you can wait a few hours or possibly a day to get Windows bootable should you run into any Grub problems.

Personally, I've never had any problems with Grub on the MBR, and I've install Ubuntu and many other Linux distributions on two computers. Leaving Windows on the MBR makes things complicated, as you'll have to find a way to add Ubuntu to the boot.ini file, and that's not easy.

---

### Post by hillbilly on 2006-01-11
[QUOTE=seakiwi]
 What's the default? I was thinking of doing it manually and setting it up as follows but I really don't have a clue what I'm doing:

/ (boot)  5 GB
swap  2 GB
/home 10 GB (or more)
FAT 32 ( so that I can read/write to Windows files)  5 GB

[/QUOTE]


Hmm...you dont actually need so much swap if you have a good amount of RAM. Like I have 1gb of ram and I used only  512Mb for swap. 

And another thing, just my two cents really. I really dont think keeping just 5GB for your / partition is enough. Coz, if you are going to do all app installation through synaptic, then all apps are bound to be installed under /. So I thnk its better to just set aside a "/boot" partition of around 512MB and then have no separate "/home" partition, but rather just a "/" parition.  But, I guess security conscious people may not like clubbing together a / and /home paritions.

And hey grub rocks ;) !! Having to boot into linux using a boot flopppy or another media, makes me lazy to boot into it at all :D !! So I always use a boot loader.

---

### Post by hillbilly on 2006-01-11
:)) hey seakiwi, like jorn said, everybody has there own modus operandi for partitioning. So maybe just go ahead and think of how exactly you want it and go for it. Best of luck.

---

### Post by johnnymo87 on 2006-01-11
What is the difference between / and /home partitions? I'm new to linux in general.

As far as I know / is for everthing on my harddrive (for some reason called ext3) and swap is for helping everything move faster ... sort of like RAM.

What does all of that stuff really mean?

Edit: On a side note, I have been continually reinstalling ubuntu to try to get everything to work. In the past, during the installation, I could not finish installing all the packages ... and the error message said it may because it just ran out of room on the drive (I had 19.7 GB ext3 / (primary) .... and 871.8 MB swap swap (logical)). I added about 2 GB to swap, and the problem was fixed. I thought swap wasn't used for that!

---

### Post by Sef on 2006-01-11
Read this post about installing Ubuntu, I found it really helpful:

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by manicka on 2006-01-11
Sounds like you may be installing ubuntu into the swap partition somehow.

This page explains the purpose of seperate partitions in Linux and further up the page has some stuff on the purpose of Primary and Logical partitions

[http://www.tldp.org/HOWTO/Partition/requirements.html#AEN493](http://www.tldp.org/HOWTO/Partition/requirements.html#AEN493)

---

### Post by hillbilly on 2006-01-11
[QUOTE=johnnymo87]What is the difference between / and /home partitions? I'm new to linux in general.

As far as I know / is for everthing on my harddrive (for some reason called ext3) and swap is for helping everything move faster ... sort of like RAM.

What does all of that stuff really mean?

Edit: On a side note, I have been continually reinstalling ubuntu to try to get everything to work. In the past, during the installation, I could not finish installing all the packages ... and the error message said it may because it just ran out of room on the drive (I had 19.7 GB ext3 / (primary) .... and 871.8 MB swap swap (logical)). I added about 2 GB to swap, and the problem was fixed. I thought swap wasn't used for that![/QUOTE]


There is no specific difference other than the fact that /home will be in a different logical partition than /. b
Like for e.g. "/" was present on /dev/hda1 and /home is present on /dev/hda2. So now one good reason for having it is even if your /home filesystem gets corrupted, your / partition stands. Some people (i guess i shud say "server") have different partitions for /tmp, /var, /boot and so on.  just thnk of it like you have directories on windows.

---

### Post by manicka on 2006-01-11
[QUOTE=Sef]Read this post about installing Ubuntu, I found it really helpful:

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")[/QUOTE]

nice site, thanks for the link :)

---

### Post by johnnymo87 on 2006-01-11
Thanks everyone for the tips. Even though I was not dual booting, I read the dual boot page as I went through my installation. I noticed that I had set my swap to bootable and my ext3 to not bootable! I'm working through the installation now ...

Edit: Nope it's still seems to want to install in my swap partition. I'm moving this to a new thread: [http://www.ubuntuforums.org/showthread.php?p=649274#post649274](http://www.ubuntuforums.org/showthread.php?p=649274#post649274)

---

### Post by seakiwi on 2006-01-12
Yay!!! I did it! :D 

I just installed Ubuntu onto my brand new second HD and the install went flawlessly. The partitioning process was very intuitive and user friendly much to my surprise (although it probably wouldn't have been had I not done some "homework" prior to installing) and GRUB installed with no hitches either. I've rebooted and so far everything is looking fine.

I'll have to spend some time playing around with bits and pieces but I'm online (duh!) which is a relief.

Thanks to everyone for your help with this. I couldn't have done it without you! 

Now, back to my my new toy :mrgreen:

---


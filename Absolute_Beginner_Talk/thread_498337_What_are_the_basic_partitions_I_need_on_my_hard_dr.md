---
title: "What are the basic partitions I need on my hard drive?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-07-11
Hi I know you need a Swap, a boot and a partition for everything else for a basic setup. I know the swap partition is supposed to be double the size of the amount of ram in your system but how big should my boot partition be?. I forgot that I needed a boot partition when I installed Feisty so I just created the swap partition, one for my /home and one for everything else. But I didnt add a boot partition? everything seems to be running fine? What does this boot partition do. If it helps I used the GUI installer.

---

### Post by LaRoza on 2007-07-11
You only need one partition. Swap is optional, but recommended.

Many people have a boot, home, and os partition, but this is just preference.

It is a myth that swap should be two times your RAM. People have tested that and determined it to be false. I find that 512 MB is more that enough.

---

### Post by nite owl on 2007-07-11
Thanks for the reply LaRoza. Do you know what a boot partition does and how big it should be?

---

### Post by LaRoza on 2007-07-11
> **nite owl said:**
> Thanks for the reply LaRoza. Do you know what a boot partition does and how big it should be?

It holds the OS files that boot the system. It is very small. Some OS's make a seperate boot partition. (Slackware, I believe is one of them).

---

### Post by Inxsible on 2007-07-11
Like LaRoza said, you only "need" 1 partition for the install.
 
But it is good practice to have an additional swap and a /home partition.
 
I think you are confusing the root partition with the boot partition. root holds the entire OS, boot only holds the files necessary for booting up and is generally very small.
 
If you didnt create a separate boot partition, the folder will still be there under the root (denoted by /). Check the size of the boot folder and you will notice it to be quite small.
 
 
I have a swap of 904 MB ( dont ask why...I made my other partitions and was only left with that much for swap ;) ) and I have never seen it be used more than 33% = 300MB.
 
I also have 2GB of RAM, so maybe thats why I dont really need a huge swap.
 
root (/) partitions : anything above 3 GB is good enuff, but 10GB is a good approximation (I have 9GB of root)
/home : I have a 20GB home which in my opinion is pretty decent. havent filled it much yet
swap : 1GB is more than sufficient....irresepective of how much RAM you have (as long as it is 256MB or more-- running Ubuntu on less would be quite slow i think)

---

### Post by nite owl on 2007-07-11
Wow sooo many people are wrong about the swap needing to be double the RAM. I even had my lecturer at uni tell me it should be double. ah but I never had much faith in him anyway lol

---

### Post by jayson.rowe on 2007-07-11
It may just be old habits (I started w/ slackware back in the 90's), but I still make a 200MB /boot partition, and format it to ext2. 

I have loaded Ubuntu a couple of times w/o it just to see if there was a difference, and it seems to boot faster w/ a ext2 /boot partition.

Could be my imagination though.

---

### Post by nite owl on 2007-07-11
> **jayson.rowe said:**
> It may just be old habits (I started w/ slackware back in the 90's), but I still make a 200MB /boot partition, and format it to ext2. 

I have loaded Ubuntu a couple of times w/o it just to see if there was a difference, and it seems to boot faster w/ a ext2 /boot partition.

Could be my imagination though.

Why ext 2 instead of ext 3?. Sorry if this is obvious.

---

### Post by glaubergoncalves on 2007-07-11
I've got 4: one for / (17.9GB), one for /var (17.9GB, same size as /) one for /home (73.9GB, actually the hole hdb, all the others are in hda), and one for swap (1GB... yes, I bought that doubled size RAM swap partition story).

   I've made a separate partition for /var because it's where my backups stay, just thought that it would be interesting to keep them in a separate partition, so if I have any problems with my / or /home ones, the backups would be safer and more up to recovery...

---

### Post by stalkingwolf on 2007-07-11
As I recall when installing Fiesty you must have a / and a swap (installer suggests a min of 512mb as I recall)
or it will not let you proceed with installation.  Again as I recall, swap is used to store active applications
and reduce drain on RAM.  With the current 1GB + RAM in computers this may indeed no longer be necessary,
but like command line it is useful.

---

### Post by UnixAnt on 2007-07-11
Yep, I have a /boot partition (100mb), / (10gb), /var (1gb), /tmp (1gb) and /home (whatevers left).

As far as swap is concerned, there is no set-in-stone answer for this.  I have always used 512mb to 2gb for desktop and laptop installs, and 2gb - 8gb for professional server installs I do for a living.

It is worth pointing out that having an enormous swap file is never a good idea, as this could potentially mask an actual capacity issue you have with your box.  If you are short of memory - go and buy some physical memory to suit the task you wish to accomplish...

---

### Post by UnixAnt on 2007-07-11
> **stalkingwolf said:**
> Again as I recall, swap is used to store active applications
and reduce drain on RAM.

Quite simply, swap (or virtual memory) is used when your system runs out of physical memory.  It is much slower than physical memory and is subject to paging between it and physical memory.

---

### Post by jayson.rowe on 2007-07-11
> **nite owl said:**
> Why ext 2 instead of ext 3?. Sorry if this is obvious.

Honestly - I don't know - it's what I was taught when I first started messing w/ Linux years ago. I'm assuming the /boot partition doesn't need Journaling, so having ext3 on that small partition is unnecessary overhead.

Again - none of this is really necessary any more. I just do it because I like having an organized system.
I have a 
/boot (ext2)
/ (ext3)
/usr (ext3)
/home (ext3) 
 and I have another partition formatted in xfs that I have mounted as /home/jayson/data so that although it is a seperate partition in xfs for better handling video and large audio files, it simply shows up in my home folder as a folder. That partition is also on my second hard drive- my swap is the first partition on that second drive, and the /home/jayson/data is the second partition...the other partitions are all on my first hdd.

I used to do /var and /tmp partitions as well, but decided against it this time loading.

---

### Post by niteshifter on 2007-07-11
You need – as in required – just one. The entire filesystem goes there and files are used to swap memory to disk (automatically) when a need arises. However ....

The “default” of two, a partition for “/” and all that is under it and a dedicated swap partition generally offers better performance over the single partition method.

Setting up a separate partition, specifically the first or lowest numbered partition for /boot is principally for reliability: After booting, the disk's read/write heads will seldom, if ever be over that physical area of the drive. Makes no difference to a desktop system, worth considering for a laptop - even though modern disk data structure make this less of a "sure thing". Some folks like to separate it out for experimenting with different kernel builds.

A separate partition for /root – with enough space to work in for things like making, loading and mounting CD or DVD ISOs can facilitate repairing a damaged system. The thinking here is that one is seldom doing anything as the superuser (root), so that area would remain intact when other “high-traffic” areas could experience damage from rogue processes.

A separate partition for /home makes tar or or other backup of all user(s) data very quick and easy.

Separate partitions for /var and /tmp are sometimes setup to make dealing with abandoned files (like in /tmp) or runaway logs and spools (in /var) a bit easier and to keep them from eating space and impacting the other folders in the filesystem.

Placing the more-or-less “static” portion of the filesystem (/usr) in a separate partition is sometimes done for performance and-or reliability reasons. The same thinking can be applied to separate partitions for /sbin, /bin and /lib.

A key thing to consider is that partitions give one a degree of immunity from software malfunctions, if some program / process goes nuts in one it's not going to impact any other. Hardware malfunctions: all bets are off. When (not if!) the drive's electronics go psycho .... that's what backups are for :)

What partitioning scheme should one use? At a minimum, two (/ and swap). I've always been uncomfortable with this – it's to “Windows-ish” for my taste. I think more is better, at the very least a /boot, /, /home and swap for laptops, skip the /boot on a desktop if you like (but considering the small size needed – why not do it anyway). 

I dual boot Edgy and XP on a Dell 8600 laptop with 2GB RAM and 120GB drive. I have this arrangement (in partition number order):

50MB – Dell Diagnostics
40GB – XP, 50% used, give or take - it's been awhile since I booted it ;)
15GB – Shared (VFAT) between XP and Edgy, currently has 4GB used.
(from here on it's Linux in extended partitions)
200MB - /boot. Currently has GRUB and two boot images totaling 20MB. Has had 80MB.
8GB - / Currently has 340MB used, has been up to 6GB
4GB - /root. Currently has 200MB
4GB - /var. Currently has 500MB, has been 3GB (MySQL databases).
10GB - /tmp. Currently has 128MB, grows to DL-DVD size when I burn one.
10GB - /usr. Currently has 3GB. 
20GB - /home. Currently 3GB. Has been bigger, could be much bigger, but I have a 250GB NAS for music / videos and databases.
1.5GB – swap. Has seen 800MB used, but that's because I do weird things (db design) and needed to stress-test the system after first install. “Ordinary” use it's typically 50MB or less when I hibernate the machine.

Now, as to what size swap needs to be ... that depends :) By and large the old rule of 2x RAM has fallen by the wayside for nearly all users on modern kernels. Half to equal works well and allows for hibernate on most machines. But for folks who might be generating huge in-memory data structures that have no disk file basis the rule should still be applied: 1.5x to 2x RAM - in some really weird cases, even more.

---

### Post by UnixAnt on 2007-07-11
> **niteshifter said:**
> Setting up a separate partition, specifically the first or lowest numbered partition for /boot is principally for reliability

Actually, mine is just force of habit from the old LILO days, where it had to be installed on the first 1024 cylinders of the disk in order to be bootable.  I've been using Linux since 1996 and some of the old priciples are still with me :D

---

### Post by moljac024 on 2007-07-12
I've set up a separate /tmp partition and gave it 2GB space....is this enough ?

I was wondering would it impact my DVD burning ?

---

### Post by nite owl on 2007-07-12
Wow thanks to everyone for taking some time out to help me...Actually does partitioning stop viruses at all or does it just make it a whole lot easier to recover?

---

### Post by longlegs on 2007-07-12
If I have a terabyte of memory, do I need 2 terabytes of swap file? Not hardly. Don't need any swap at all !
To decide how much swap space you need, FIRST add up all the memory used by the OS, programs, etc. For a typical user this will be in the neighborhood of .5 - 2g. Users needing more than that are probably doing some heavy image or sound processing, definitely not an average user. 
Once you decide on the memory you need, (say 2gB) subtract from that the memory you actually have, (say 784mB). 2gB-784mB=~ 1.2gB for swap size.. SInce HD space is generally many times that, round it off to 2gB. OR just pick a number, no biggie  unless you are tight on HD space, in which case round it up to the nearest .25 gB
You need 5 partitions. 
1: a small partition containing all files/apps/ stuff to rescue a broken main OS, bootable direct or with a Live CD. This partition may BE the live cd.
2: a small partition to hold the OS with some room to grow.(as all OS's do!)
3: a boot partition, probably only 128mB or so. This partition is called by the MBR and contains grub which boots the main OS on the OS partition as in 2. It does not get changed when you re-install or upgrade the main OS in 2.
4: a large partition for data.This one you backup for emergencies.
5: a swap partition if you don't have a lot of memory.
Have a good day!
longlegs

---


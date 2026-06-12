---
title: "how to custom partition an install"
date: 2011-08-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by mattig89ch on 2011-08-16
howdy all,

i wanted to just a manual install of ubuntu, see if that would work.  only, I don't know how to custom partion a drive.  is there a set of instructions that makes it very simple?

I found this: [https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

but i wasn't quite sure what type of partion i would be creating.  I'm pretty sure its a logical one...but not 100%

---

### Post by sikes on 2011-08-16
This describes an installation of 11.04: [https://help.ubuntu.com/11.04/installation-guide/i386/module-details.html](https://help.ubuntu.com/11.04/installation-guide/i386/module-details.html)

As for partitioning, I prefer to set the following (based on 250Gb hdd):
1st, 100Mb to /boot
2nd, 30 to 50Gb to /
3rd, a swap partition equal to the amount of RAM in my system.
4th, the remainder set to /home

There are other schema for partitioning, but the one above keeps my home files safe... marginally safe, anyway.

---

### Post by mattig89ch on 2011-08-18
oh, wasn't aware that the size of the space was a factor.  Honestly, whenever installing any linux os i just let the auto installer take care of it all.

lets see...56.8 GM is the free space that i'm installing this on.  since its not a physical hard disc just the free space i'm pretty sure thats logical...um...don't know what else is needed.

---

### Post by mikewhatever on 2011-08-19
The size of the space is not a factor. The only partitions you need is the system (or the root) and the swap. Creating a separate boot partition is redundant in most cases.
Logical or primary depends entirely on your current partition layout, and doesn't matter for Ubuntu.

---

### Post by mattig89ch on 2011-08-19
huzzah for ubuntu then.

the root is the one i'll be booting from correct?  if so then the swap will be the one i'll be using when on the desktop, correct?

also, is there a required size for the root?

---

### Post by mikewhatever on 2011-08-19
The root partition will contain all of the Ubuntu installation, the swap is used as virtual RAM and for suspending to disk. The bare minimum size for root is 5GB, but around 20-25GB is recommended.

---

### Post by munchlaxy on 2011-08-21
Quick question about swap-

My swap was initially set to around 2gb. I recently upgraded my RAM from 1 to 2gb, will I need to go in and change swap to 4gb or am I still fine?

---

### Post by adrien214 on 2011-08-22
I think you should read [this ]("http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space")and decide for yourself, also read the comments [here]("http://www.cyberciti.biz/tips/linux-swap-space.html"). You will be safe with 2GB depending on your computer use, even 1GB. If it's a desktop computer with 2GB the physical memory might not even fill up.

---

### Post by mikewhatever on 2011-08-22
No. 2GB of swap is more then enough.

---

### Post by mattig89ch on 2011-08-25
ok, so i could get away with 10 gigs for the root?  I want as much space as possibe for my data.

also, swap is the virtual memory?  Im on a little EEEPC with 2 gigs of physical memory, do i need swap even then?

finally, do i need to partition off the space for my data?

Edit: well i tried to custom partition part of my drive using all the stuff you guys told me.  only trouble is i couldn't fnd where to define 1 partition as a root partition.  found the boot partition but not the root.

how do i define the root partition?

---

### Post by mikewhatever on 2011-08-26
The symbol for root is / (the forward slash). It's found in the same menu with boot.
Whether or not to create the boot partition is really up to you. 2GB of RAM is plenty for Ubuntu with moderate usage. If you have a tendency to open lots of programs at once, or hundreds of browser tabs, create a 2GB swap partition.
Lastly, it you want a separate data partition, then yes, you'll have to create that partition, unless it already exists.

---

### Post by mattig89ch on 2011-08-26
ok, to be clear, you need the floowing partitions:

/ (at least 5 gigs, but 20 is recommended)
Swap (virtual memory)
Usr/local

is any of this in-correct?

---

### Post by mattig89ch on 2011-08-26
huzzah!  using the partitions i just mentioned i just booted for the first time!  guess that answers that.

is it tacky to ask another question in a forum post like this around here?

---

### Post by mikewhatever on 2011-08-28
Congratulations!
As for another question, it's your thread. If the question is unrelated to the topic, it's probably best to start a separate thread. If you ask here, I might be the only one to see it.

---

### Post by mattig89ch on 2011-08-30
meh, its not terribly important.  but it might very well have something to do with my install.

when i bring up the default tetris install it the whole machine starts running slow.  i brought up the...um...system diagnostic tool (i think thats what its called)...Ubuntu's task manager, and it says only 15% of the swap mem is being used, and only 10% of the cpu.  when i close the game out the machine has no trouble.  mind you, i don't have the same issues with any of the other games, or when i'm watching a movie.  just that game.


and here's another, i've used ubuntu for about a week on here, and have nothing but praise.  So i'm thinking of just backing up my windows files and blowing the partution away from here.  now if i do this, can i incorporate the new free space into my existing usr/local partition w/out having to re-install the entire os?

edit:  it might help you to know that i gave the root partition 10 gigs, for the first question i mean.

---

### Post by Jar12 on 2011-12-22
Hi

would like to be advised on partitioning. I am a new-route in Ubuntu.

my system is Lenovo s10-2 mini lap. it has 1 GB ram, 160 GB hard disk, N280 Atom processor & other standard equipments. 

I want to use only Ubuntu 11.04 as single OS (and no other).

Kindly advise me how can i go for partitioning the whole 160gb hard disk.

shall there be any /boot needed separately? can i go as --
1. / -- 35 GB.
2. SWAP -- 2.5 GB (may be in future can add ram upto 2 gb).
3. /home -- 122.5GB

Now I have /boot for 40GB, but is /boot mandatory?

Rgds,
Raj:D

---

### Post by oldfred on 2011-12-22
@Jar12
It would be better to start you own thread. Most desktops do not need a separate /boot. Servers, RAID, LVM or other special formated partitions may need a separate /boot.

My standard starting recommendations.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---


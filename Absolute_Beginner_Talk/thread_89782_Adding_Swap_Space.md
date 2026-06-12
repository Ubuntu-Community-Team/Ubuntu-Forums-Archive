---
title: "Adding Swap Space"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by jeffreyvergara.NET on 2005-11-13
hello, how do I check how much Swap space I have? and is it possible to add more swap space without formatting/deleting files on my HD?

---

### Post by Xian on 2005-11-13
[QUOTE=jeffreyvergara.NET]hello, how do I check how much Swap space I have?[/quote]

Issue this command in a terminal.
Note the swap file usage listed at the bottom.

```
$ top

top - 11:20:22 up  8:58,  2 users,  load average: 0.36, 0.39, 0.37
Tasks:  93 total,   2 running,  91 sleeping,   0 stopped,   0 zombie
Cpu(s): 50.0% us, 50.0% sy,  0.0% ni,  0.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    451660k total,   445580k used,     6080k free,     8880k buffers
Swap:  1052216k total,   165704k used,   886512k free,   171052k cached
```

[QUOTE=jeffreyvergara.NET]and is it possible to add more swap space without formatting/deleting files on my HD?[/QUOTE]
In short, no. You will have to assign more space on the HD.

---

### Post by jdong on 2005-11-13
[QUOTE=Xian]In short, no. You will have to assign more space on the HD.[/QUOTE]

Actually, *yes*. You can supplement your swap partition with a swap *file*. It goes something like this:

First, create a large empty file:
```

sudo dd if=/dev/zero of=/swap_file bs=1M count=1000

```

Replace 1000 with the size of the swap file desired, in MB. You can also put the swap_file in a different location if desired.

Next, we'll secure the swapspace, so ordinary users cannot read the contents (potential security breach):
```

sudo chown root:root /swap_file
sudo chmod 600 /swap_file

```

Then, turn it into swap space:

```

sudo mkswap /swap_file

```

Next, turn it on:
```

sudo swapon /swap_file

```


To make it turn on at every bootup, open up /etc/fstab:
```

sudo gedit /etc/fstab

```

Add this line to the end of the file:
```

/swap_file       none            swap    sw              0       0

```

---

### Post by bvc on 2005-11-13
Also, if the hd has the space, you can have more than 1 swap[QUOTE=man swapon] -p priority
              Specify priority for swapon.  This option is only available if swapon was compiled under and is used under a 1.3.2  or  later
              kernel.   priority is a value between 0 and 32767. Higher numbers indicate higher priority. See swapon(2) for a full descrip-
              tion of swap priorities. Add pri=value to the option field of /etc/fstab for use with swapon -a.[/QUOTE]

so an fstab would look something like this```

/dev/hdb5       none            swap    sw   pri=1           0       0
/dev/hdb6       none            swap    sw   pri=0           0       0
```
The swap with the lower priority will not be used until it is needed.
You can also use the command;
free -m
to see swap usage.

---

### Post by jdong on 2005-11-13
Also, swaps explicitly set to the exact same priorities will be used in slices like RAID0 -- very cool for swap on multiple physical drives.

---

### Post by jeffreyvergara.NET on 2005-11-13
thank you very much guys!

here's my original swap thingy.. taken from the command $ top

> top - 12:32:10 up 28 min,  2 users,  load average: 0.05, 0.36, 0.39
Tasks:  86 total,   1 running,  85 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.7% us,  0.7% sy,  0.0% ni, 94.3% id,  0.0% wa,  0.0% hi,  0.3% si
Mem:    776364k total,   591072k used,   185292k free,    54856k buffers
Swap:  1609720k total,        0k used,  1609720k free,   329328k cached


is there a limit on how much swap space I can use? I have 2 ata HD 40gb(main) 80gb(files) so, it is possible for me to add additional swap?

the reason I'm doing this is that, I read from other forum that adding Swap space will increase the performance of online Games played on WINE. I'm playing Tantra Online using compile WINE 0.9 but the performance is poor unlike running it in Window$, other people on that forum doesnt have a problem with it so I think adding swap space will be the solution

---

### Post by poptones on 2005-11-14
1.6GB of swap?

You're not even using what you have. You don't need more swap space.

---

### Post by jdong on 2005-11-14
Mem: 776364k total, 591072k used, 185292k free, 54856k buffers
Swap: **1609720k total, 0k used**, 1609720k free, 329328k cached

You are not using any swap at all! No need for any more! Most likely, you'll never ever use any more than maybe 100-200MB swap on the average desktop, because as soon as you need to actively swap system performance degrades to unacceptable degrees.


Another command to examine is **free -m**. On my system:

```


jdong@shuttle:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1012        999         12          0        101        654
-/+ buffers/cache:        242        769
Swap:          956          6        950
jdong@shuttle:~$

```

1012MB RAM, 999MB used, though 654 being used as cache and 101MB is being used as buffer. (Both of these yields immediately when a RAM-hungry program is launched and demands more than 12MB RAM. Meanwhile, they significantly improve disk IO performance).

I have 1GB swap, and only 6MB is being used. I've seen no more than 10MB swap usage.... ever.

---

### Post by lito on 2005-11-14
hello,
im new in linux-world and this forum but im loving it,man i've been missing out...but anyway is there a way to change the size of that supplementary swap-file(or to remove it completely) described in jdongs method ?

i would like to know,many thanks.:smile: 

lito

---

### Post by poptones on 2005-11-14
Lito, unless you really need the space I see no benefit in mucking with the partitions and possibly enadngering your data. If you ever reinstall just remove it and make a new swap partition of more reasonable size, like 500MB.

---

### Post by jeffreyvergara.NET on 2005-11-14
fresh install breezy:

> 
top - 02:04:41 up  1:24,  3 users,  load average: 0.33, 1.04, 1.50
Tasks:  87 total,   1 running,  86 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.0% us,  1.0% sy,  0.0% ni, 94.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    776364k total,   761920k used,    14444k free,     9996k buffers
Swap:  **1614492k total,    12532k used, ** 1601960k free,   581108k cached



hmmm...it says  12532k used

---

### Post by poptones on 2005-11-14
Before I rebooted this morning (power went out) I had about 220MB of swap space used on a machine with 512MB ram. It's not unusual and it doesn't mean the machine is going to slow to a crawl... but a GB of swap would be a LOT and it probably WOULD mean the machine was running pretty slow by the time it filled that up.

*500MB should be enough for anybody...*

---

### Post by jdong on 2005-11-14
[QUOTE=lito]hello,
im new in linux-world and this forum but im loving it,man i've been missing out...but anyway is there a way to change the size of that supplementary swap-file(or to remove it completely) described in jdongs method ?

i would like to know,many thanks.:smile: 

lito[/QUOTE]

First off, **poptones**: there is no endangerment in making a swap **FILE**, like I suggested. A swap **PARTITION** means you'd have to resize a partition, and that's where the danger would come in. My method is 100% harmless.


lito, look at the dd command, under **count=1000**. Change the number 1000 to the desired size of the swap space, in MB. For example, **count=512** creates a 512MB swap file.


To get rid of it later on, first you need to remove the line you added to /etc/fstab. Then, reboot to deactivate the swap. Next, run **sudo rm /swap_file** to get rid of the file. That's it.

---

### Post by poptones on 2005-11-14
Perhaps you should **read his question again, jdong**. then **read my answer**. Neither of this addressed *creating a new swapfile*. he asked about REMOVING the swap partition he HAS. This would mean removing and/or resizing an active partition. that is absolutely NOT "100% harmless" nor is it certain to work without borking access to the data on the affected partition.

There is nothing at all "dangerous" about creating a new swap file as you describe (that is how mine is setup, only encrypted). It is, however, **completely pointless** to someone who *already* has about a GB too much swap space.

---

### Post by jdong on 2005-11-14
[QUOTE=poptones]Perhaps you should **read his question again, jdong**. then **read my answer**. Neither of this addressed *creating a new swapfile*. he asked about REMOVING the swap partition he HAS. [/QUOTE]

No, he didn't. Perhaps you need to cool down and read his question again:
> 
but anyway is there a way to change the size of that supplementary swap-file(or to remove it completely) described in jdongs method ?

He asked:

(1) How to make a swap file of a different size than my example of 1GB
(2) How to get rid of a swap file when he doesn't want it anymore.

---

### Post by lito on 2005-11-14
thanks for the replies!

there seems to be some confusion about my question but jdong is right,it's exactly what i meant and wanted to know.;) 
anyway thnx the both of you since the intention is good.

btw great forum,very informative:D 

lito.

---

### Post by ninocass on 2006-02-03
is there a way to mount the swap space?

im trying to get the suspent2 working and it needs to to specify a swap space, i tried just entering the file but it wasnt having any of it so im assuming i need to mount it.

im a total noob btw :)

nino

---

### Post by nik on 2006-02-03
Don't mean to hijack the thread, but since lito already got his answer.. :)

I'm just wondering, is it possible to have an installation without a **swap partition** and only a **swap file**? And if so, what is the advantage / disadvantage of this setup?

---

### Post by Sycrat on 2007-05-25
Thanks for the help with mounting the swap at startup :) I just removed the old one and put a new one on an extended partition, and it wasn't mounting it at startup, thank you :) have a good one.

~Sycrat@ONYX
~Teh Lin'hux Brova's

---

### Post by JC Denton on 2007-06-10
I added a swap file but to my great dismay when the laptop is about to hibernate it still complains there is insufficient swap space:

```

Mem:    483352k total,   459664k used,    23688k free,     5116k buffers
Swap:  1546096k total,   517736k used,  1028360k free,   116992k cached

```

This is after creating the swap file and using swapon.

mkswap did report the following:
```

 mkswap /mnt/hda6/swap_file
Setting up swapspace version 1, size = 1048571 kB
no label, UUID=cb3a03fe-7851-4db5-a6f7-7180891b12d0

```

---

### Post by Delkster on 2007-06-10
> **nik said:**
> I'm just wondering, is it possible to have an installation without a **swap partition** and only a **swap file**? And if so, what is the advantage / disadvantage of this setup?
Advantages:
- More flexible (you can change the swap size without changing partitions)

Disadvantages:
- May be a little slower, although I don't think you'll notice
- Linux can only hibernate to a swap partition, not to a swap file (as far as I know anyway)

> **JC Denton said:**
> I added a swap file but to my great dismay when the laptop is about to hibernate it still complains there is insufficient swap space
See above.

---

### Post by jdong on 2007-06-12
A third disadvantage is that swapfiles cannot be used if the disk it's on can't be mounted (for obvious reasons). So, for fsck and other emergency operations before boot, you will not have access to swap. Ordinarily this is not an issue, but at times a disk repair can be very memory intensive and you'll be scrambling for swap :)

---

### Post by bimargulies on 2007-10-18
Follow the procedure here.

[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

### Post by SABOT00 on 2008-04-10
does ubuntu even need a swap partition and if yes does it have to be a primary?
oh yeah by the way i have 4 gb of ram

---

### Post by Delkster on 2008-04-13
> **SABOT00 said:**
> does ubuntu even need a swap partition
It's not really required, but it's probably a good idea to have either a swap file or a swap partition. For differences between the two, see the older messages in this thread. Disk space is usually so cheap nowadays that in most cases it makes sense to spend some disk space to give you some more flexibility in memory use.

> and if yes does it have to be a primary?
A primary partition? No, it can be a logical drive in the extended partition just as well.

> oh yeah by the way i have 4 gb of ram
Well, it all depends on your memory use, of course. If you never use that much memory, you don't necessarily need swap. Still, if you run anything memory intensive and there's even a slight chance that you may need more memory, having some swap space is a small price to pay for avoiding any trouble later.

---

### Post by jdong on 2008-04-13
> **SABOT00 said:**
> does ubuntu even need a swap partition and if yes does it have to be a primary?
oh yeah by the way i have 4 gb of ram

With 4GB RAM, you probably won't **require** any kind of swap, but I'd still **recommend** it. The reason? Swap allows Linux to shove unused apps (or leaky portions of apps) onto disk and utilize system RAM more efficiently for cache and running applications.

---

### Post by likerice on 2008-05-23
i recently deleted and then re-created swap space on two separate physical drives. i had wanted to install xp but had too many primary partitions on the destination drive, so i deleted the swap partition, carved out some swap space on the second drive, and then re-added swap space on the first drive once xp was installed. *phew

the problem: neither swap is turned on automagically after boot. what's wrong? 

here's my ftab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=2439cf65-c6cb-4183-964e-bdda8a698ec0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=1e927f15-3e17-4fd6-b245-bfc52947631c /home           ext3    relatime        0       2
# /dev/sda3
UUID=3f689ca9-b2de-4e0d-8674-c899ef588500 none            swap    sw              0       0
# /dev/sdb5
UUID=521f67bc-9bc3-4d55-a394-f8426c0283f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /media/STORAGE ext3 defaults 0 0
```  

how should i edit the above--if indeed i should edit it at all--so that swap is turned on at boot?

thanks!

btw, total n00b here :-P

---

### Post by ziedrich on 2008-06-08
> **Delkster said:**
> 
Disadvantages:
- May be a little slower, although I don't think you'll notice
- Linux can only hibernate to a swap partition, not to a swap file (as far as I know anyway)


See above.

Hello all,
I'm using swap file as swap space.. what i want to ask is, i couldn't hibernate .. and there are this command 
Class driver suspend failed for cpu()
some devices failed to power down (3) aborting suspend.
timing out command waited 120s

is it because im using swap file not swap partition? or there are any other problems? 


im really still newbie here..  thanks all.

---

### Post by knut100 on 2008-06-11
Okay, so people can make the swap bigger, or add a swap FILE. 

My Problem;
first of all, I'm a beginner.
I installed Ubuntu on my own the first time, and something went wrong under the partition-****...long story short...I've got a swap PARTITION going on 50GB! it's a 160gb ata disc.

HELP ME, I want my space back.

**How do I make it smaller?**

---

### Post by Krupski on 2008-06-27
> **jdong said:**
> Actually, *yes*. You can supplement your swap partition with a swap *file*. It goes something like this:

I know this reply wasn't directed at me, but the info was very useful to me as well! Thank you so much for your excellent procedure! It worked perfectly!

-- Roger

---

### Post by Krupski on 2008-06-27
> **SABOT00 said:**
> does ubuntu even need a swap partition and if yes does it have to be a primary?
oh yeah by the way i have 4 gb of ram

Here's a question. Sorry if it's something simple... but I'm a newbie, so bear with me please.

I built a network attached storage device using SATA hard drives mirrored in a RAID-1 configuration. Linus 64 bit server itself is on an 8 gigabyte compact flash card, installed in a CF-to-IDE adapter card, plugged into the motherboard IDE port.

The hard drives themselves do not have one byte of Linux on them... they are 100% storage space available on the network via SAMBA.

So, here's the question: IF I create a swap file on the RAID drive (i.e. /dev/md0), will it work?

It works when LINUX is up, but during boot will LINUX need the swapfile before the RAID device is up and running?

Will it fail to mount if SWAP tries to activate before /dev/md0 is available (during boot)?

Alternatively, I could probably put a swapfile on the CF card since Linux doesn't need anywhere near 8GB to run... heck 2 gigabytes is more than enough. But, swap on the CF card is bound to be slow and it will also add to the wearing of the flash memory.

So, in summary:

(1) With 8 GB of ram, do I even NEED a swapfile?
(2) If I put a swapfile on a RAID drive will it fail if swap is needed before the /md0 device becomes ready?
(3) If I instead put swap on the CF card, will it excessively use and wear the flash memory?

Sorry if these are dumb questions... but I'm at the bottom of a VERY steep learning curve!  :D

Thanks in advance for any help!

-- Roger

---


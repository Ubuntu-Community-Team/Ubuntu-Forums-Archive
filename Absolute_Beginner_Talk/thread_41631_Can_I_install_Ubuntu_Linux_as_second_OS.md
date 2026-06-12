---
title: "Can I install Ubuntu Linux as second OS?"
date: 2005-06-14
forum: Absolute Beginner Talk
---

### Post by Darius on 2005-06-14
Hello for all guys,

I'm new in this forum, and Linux.. So, my friend gave for me new UBUNTU LINUX CD. Now I'm crazy for this, i want to know, why a lot of peoples like this OS. 

So, Can I install this OS as second OS, or no? If yes, how? Thanks for all informations.


Sorry for my english, if I did mistakes, please say for me :) Have a nice day.

---

### Post by Leif on 2005-06-14
Yes, you can. The ubuntu installer will automatically detect if there's an existing installation of windows and put it in a menu so you can choose what to use when you start your computer.

---

### Post by lorenzo on 2005-06-14
If you have windows as OS, you should follow these steps:

1) Enter in Windows and defrag the disk the best you can
2) In windows, resize the C: partition to make space available for linux (with a program like "partition magic") and for a FAT32 partition (probably you have to reboot to complete the operation)
3) If you have only on disk (C:) : create a D: partition with FAT32 filesystem. This disk  will be used to share documents among the two OSs.
4) Boot with ubuntu installer disk and follow the instructions... (take care that disk formatting does not erase C: and D: partitions
5) once in linux you have to edit /etc/fstab and add  a line to be able to view C: and D: 

well, there's a lot more. With this you can begin.


Good luck,
lorenzo

---

### Post by Darius on 2005-06-14
Thanks :) I found all things in [www.google.lt](www.google.lt) :)

---

### Post by az on 2005-06-14
You can use the ubuntu installer to resize your windows partition.
  
[http://test.wiki.ubuntu.com/forum/installation/Partitioning](http://test.wiki.ubuntu.com/forum/installation/Partitioning)

---

### Post by wirjo on 2005-06-14
Certainly, that's one of the good things about installing Linux nowadays. It's so simple to just partition your hard-drives and be able to dualboot.

---

### Post by Darius on 2005-06-14
My hard-disk is 20Gb,  what's recommendations for partitions? For example:

C: 10Gb
D: 10Gb

Or smth another way?

---

### Post by wake-kitty on 2005-06-14
i also have a 20gb hd but i put greater ratio of the partioin in my 1st partition which is xp cause the programs are way too huge compared to linux.  but i also created a swap partition which is around 500mb i think.

---

### Post by aysiu on 2005-06-14
[QUOTE=Darius]My hard-disk is 20Gb,  what's recommendations for partitions? For example:

C: 10Gb
D: 10Gb

Or smth another way?[/QUOTE]

What's your RAM like? If it's under 256 MB, you may consider setting up a SWAP partition as well. Are you using Windows XP, NT, 2000? If so, your Windows partition is probably formatted using NTFS instead of FAT32.

If that's the case, I'd set it up like this:

**C: 7 GB** (or however much you need just for the operating system and programs)
**D: 7 GB** for a FAT32 partition, as this can store files that both Windows and Linux can access
**Ext3 partition (no label): 6 GB** for root (and all its associates--boot, home, etc.)

---

### Post by Darius on 2005-06-15
[QUOTE=aysiu]What's your RAM like? If it's under 256 MB, you may consider setting up a SWAP partition as well. Are you using Windows XP, NT, 2000? If so, your Windows partition is probably formatted using NTFS instead of FAT32.

If that's the case, I'd set it up like this:

**C: 7 GB** (or however much you need just for the operating system and programs)
**D: 7 GB** for a FAT32 partition, as this can store files that both Windows and Linux can access
**Ext3 partition (no label): 6 GB** for root (and all its associates--boot, home, etc.)[/QUOTE]

Hello aysiu, my RAM is like 256Mb, I'm using Win XP, My Windows partitions is formatted using NTFS. So, what's recommendations?  Are u sure? Set it up like u? 

How I can do it? How to do Ext3 partition? Thanks for all answers.

Best wishes.  :grin:

---

### Post by poofyhairguy on 2005-06-15
[QUOTE=Darius]
How I can do it? How to do Ext3 partition? Thanks for all answers.

Best wishes.  :grin:[/QUOTE]

For 256, make a half gig swap I'd say. Do most of what the other poster says with a windows partitioning tool (split ntfs partition, create three- one fat32, one ntfs, one nothing). Then tell the Ubuntu installer while you are installing it to create the ext3 partition (and swap parition) in the blank space.

---

### Post by Darius on 2005-06-15
[QUOTE=poofyhairguy]For 256, make a half gig swap I'd say. Do most of what the other poster says with a windows partitioning tool (split ntfs partition, create three- one fat32, one ntfs, one nothing). Then tell the Ubuntu installer while you are installing it to create the ext3 partition (and swap parition) in the blank space.[/QUOTE]


Sorry for a stupid question, how to do three partitions? I read all technicial documentations in Microsoft, so, I can do it in "Disk Management", but I can't find Unallocated Space, where I could do new partitions.  ](*,)

---

### Post by Elim on 2005-06-15
Hello all,

Yeah, you've got another completely unexperienced Linux n00b knocking on your door. ;)  I hope you don't mind if I chime in with a few questions...

I am completely new to Linux and after reading for a few days I deciding to set up Ubuntu to dual-boot with Win XP Pro.  However, I'm new to this whole hard drive partitioning thing.  I have a 20 Gig hdd, so not much space, and I've got about 8 Gigs free right now (although I need to reserve about three or four of that free space for more Windows programs and files).

--If I use Partition Magic in Win XP to create a Linux partition, do I need two partitions or three?  I was under the impression that Linux could read NTFS, so I didn't think a FAT32 partition that both could access was necessary.

--I have 384 MB of RAM; is a SWAP partition necessary?

--Do I need to format the Ubuntu partition as ext3, or can it run on NTFS or FAT32?  If it can run on the other types, what are the advantages of formatting it as ext3?

--In about three months I am giving this computer to my sister so she'll have one at university.  I had hoped to collapse the hard drive all back to one partition, which I'd been told I could do; however, if I format these other partitions as FAT32 and ext3 I am fairly certain that won't be possible, yes?  (If push comes to shove I can just buy my sister a new hard drive in three months.)

I think that's all the questions I have....for now.  Of course, once I get Ubuntu installed I'll have a whole new can of worms.  I hope my questions are clear.  Thanks for any and all help or links you can provide.

---

### Post by poofyhairguy on 2005-06-15
> **Elim]
--If I use Partition Magic in Win XP to create a Linux partition, do I need two partitions or three?  I was under the impression that Linux could read NTFS, so I didn't think a FAT32 partition that both could access was necessary.[/QUOTE]

Two. One for Windows, one for Linux. The Ubuntu installer will split the free (non ntfs) space into a swap and root parition like it needs.

Ubuntu can only read NTFS, it cannot write to it.

[QUOTE]--I have 384 MB of RAM said:**
> 

I say yes for anything less than a gig.

[QUOTE]--Do I need to format the Ubuntu partition as ext3, or can it run on NTFS or FAT32? 

The root partition (where ubuntu installs itself) needs to be ext3, or another kind of Linux partition.

---

### Post by Elim on 2005-06-16
The 20 GB hard drive that I am trying to shrink is formatted as NTFS; however, the only Windows partition shrinking utility that supports NTFS (that I can find) is Partition Magic, and I'd rather not plop down $50.  I looked around and found out that Ubuntu comes with it's own NTFS resizer (after all that work, only to find out Ubuntu already had the answer...), and that there is another utility called the System Rescue CD ([http://www.sysresccd.org/](http://www.sysresccd.org/)) that will also work.  Is one of these safer than the other?

---

### Post by jsuen on 2005-06-16
> **Elim]The 20 GB hard drive that I am trying to shrink is formatted as NTFS said:**
> http://www.sysresccd.org/[/url]) that will also work.  Is one of these safer than the other?
 can you add another partition to your current HDD via windows? afaik, ubuntu doesn't boot with an ntfs (pls chime in if i'm wrong..) and *might* just use the resizer to create a new partition for the ext3 FS. i'm not familiar with the NTFS resize on ubuntu, though..

---

### Post by DavidF on 2005-06-16
Will the partition program included with the installation also allow deleting or modifying of existing partitions? My HP has a D: drive partitioned as a restoration drive, and I might want to get rid of it.

---

### Post by Elim on 2005-06-16
Update: I am posting this from a very happy Linux PC.

So, maybe I can help you guys out.  The partitioner that comes with Ubuntu did a great job on my system.  (In case you're wondering, Win XP Pro, Pentium III).  I had one NTFS partition which I successfully shrunk to about 14 GB, and then I split the remainder into a half gig swap file and a 4.5 gig ext3 partition.  I've tested out a number of the apps in Linux and I went back to Windows and opened up various files and programs, and everything seems to be perfect.  (Note: the partition program isn't GUI and can be a bit confusing, but you should be able to figure it out, and I'd be happy to try to answer any questions.)

[quote] can you add another partition to your current HDD via windows? [\quote]
I'm not sure exactly what you mean; AFAIK, fdisk cannot shrink an existing partition, but it can of course add one if you haven't already formatted your entire drive.  There are a couple commercial apps that will do this in Windows, but it can be done just as easily with the Ubuntu installer.  You can shrink your current partition and divide up that new free space however you choose.

[quote] Will the partition program included with the installation also allow deleting or modifying of existing partitions? [\quote]
I believe it will, but I am not sure.  It showed all of the new partitions that I created (the Linux partition and the swap file) and allowed me to delete those, but I'm not sure about deleting or merging existing partitions.

Now a couple questions of my own:
1.) What format is the swap partition that I created?
2.) How can I see the partitions on my drive in Windows and/or Linux?
3.) Can I tell Windows to use the swap partition as it's virtual memory, or must it continue to use part of my C: drive?
4.) How can I see my Windows partition and files?

Okay, I guess that's more than a couple.   Sorry 'bout that.  Thanks for your help!

---

### Post by davahmet on 2005-06-16
[QUOTE=DavidF]Will the partition program included with the installation also allow deleting or modifying of existing partitions? My HP has a D: drive partitioned as a restoration drive, and I might want to get rid of it.[/QUOTE]
 Yes.

I would also highly recommend that you make a partition (let the Ubuntu installer do this as ext3 or reiser filesystem) for /home.  By doing this, you will find it much easier to upgrade your Ubuntu distro in the future without losing your data.

Linux does not run on the NTFS or Fat32 filesystem, nor would you want to for quite a lot of reasons.

1.  Plan out your partitioning scheme, dependant on what you want to do with your system.
2.  Defrag your Windows to get all those files relocated near the beginning of the hard-disk.
3.  Option--partition your drive with 3rd party tool.  I say it's optional right now because Ubuntu can do this if you wish.
3.  Or, boot from the Ubuntu install disk, answer the prompts until you get to the partitioning.
4.  If you created the second partition (planned for Ubuntu) with windows, it will be a NTFS or FAT32 filesystem.  Delete this second partition with the Ubuntu fdisk.  That's right, delete it.  The space will be available but now it will be free of those other filesystems.
5.  Make your /boot partition as etx3.  Set it to about 400MB in size.
6.  Make a swap partition.  Set to it about twice your memory size up to a maximum of about 1GB.  Very very few people will need swap space larger than this, ever.
7.  Make a partition for /home as ext3 or reiser, your choice as they are both excellant filesystems.  The size is up to you but remember that this is where you will store your data.
8.  Make a partition for / as etx3 or reiser, your choice.  This is where the applications and system data will live.

After these steps it's just a matter of finishing the installation and letting grub handle the boot loading for your dual-boot system.  Dow the road, when you decide to upgrade Ubuntu or even to change to another distro (gasp), you can do so without losing the data in your /home because it's safely on its own partition.

Hope this helps.

---

### Post by Ozitraveller on 2005-06-16
I'd just like to add my 2 cents here too. I've found it very useful to also make a partition for /etc as this is where most of the setting and init scripts live.

---

### Post by jsuen on 2005-06-17
***1.) What format is the swap partition that I created?***

it's type 'swap' isn't it? at least that's what my fstab tells me... i don't think it's in a format readable by windows, and i wouldn't try imho.

***2.) How can I see the partitions on my drive in Windows and/or Linux?***

for windows via linux:
less /etc/fstab
this is a file containing a table of the filesystems currently mounted

for linux via windows... i thought i saw a program mentioned here on UF about something like this further back... maybe searching or googling for it may help you there.

EDIT: The UF post [(http://ubuntuforums.org/showpost.php?p=194680&postcount=5)]here]([http://ubuntuforums.org/showpost.php?p=194680&postcount=5)  gives a link to explore2fs, which looks likes it can read ext2/ext3 FS into an NTFS drive.
[http://ubuntuforums.org/showpost.php?p=194680&postcount=5](http://ubuntuforums.org/showpost.php?p=194680&postcount=5)

***3.) Can I tell Windows to use the swap partition as it's virtual memory, or must it continue to use part of my C: drive?***

i don't think you can - correct me if i'm wrong. the swap partition also seems smaller than the virtual memory used by windows, at least for me?

bash$ fdisk -l /dev/hda5
Disk /dev/hda5: 509 MB, 509935104 bytes
255 heads, 63 sectors/track, 61 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

and in windows it's about 1.5gb, for me.

***4.) How can I see my Windows partition and files?***

to 'see' the contents of the partitions i believe you'll need to fiddle around with how mounting partitions to your linux kernel:
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)
and
[http://ubuntuforums.org/showthread.php?t=32603&highlight=fat+access](http://ubuntuforums.org/showthread.php?t=32603&highlight=fat+access)
could help..

---

### Post by davahmet on 2005-06-17
Can I tell Windows to use the swap partition as it's virtual memory, or must it continue to use part of my C: drive?

That would be nice for Windows users, wouldn't it.  :)

I don't believe you can do this because of the way Windows works with its filesystem and the way that the Windows memory manager handles read/write requests to secondary memory.  In short, Windows doesn't play well with others.

---

### Post by poofyhairguy on 2005-06-17
[QUOTE=davahmet]  In short, Windows doesn't play well with others.[/QUOTE]

XP won't install for me unless my Ubuntu drive is unplugged.

---

### Post by davahmet on 2005-06-18
I'm not surprised, Poofy.  I learned a long time ago when I first tried dual booting with Win95 and Red Hat 6.0 that Windows is a jealous OS and does not like the presence of others.  Back then, it was pretty much a standard rule that you had to install Windows first, then do the Linux installation.  Since then, Windows has gotten better about it, but from what I hear from others, it still seems to be more reliable if Windows is installed before Linux.

---

### Post by mrgnash on 2005-06-19
Hi am extremely new to Linux, partitioning and pretty everything of this nature so please forgive my newbness.

I am currently using Windows XP and like a couple of the other guys that posted in this thread, I wish to create a dual boot system. However, I am extremely worried about the following two possibilities:

1. I'll do something wrong and ending up wiping all my current data from the HD.
2. I won't configure the bootup properly and won't be able to get back to Windows (I know this doesn't sound like such a bad thing, but I'm not the only user on this comp lol)

I really can't afford to lose my data, so I'm really nervous about partitioning my HD... I had a look at the partitioner and it wasn't user-friendly enough for dumb ol' me, so I downloaded partition magic.. I just wanted to ask, if I create an ext3 and swap partition with PM, how do I instruct the Ubuntu installer to use these two rather than my NTFS partition? And secondly what are the various ways I can get back to Windows if something goes wrong?

Many thanks in advance...

---

### Post by X-Jumper on 2005-06-19
Another Hi from me, also fresh user of Ubuntu.  :) 

Today I managed to install Ubutnu on my second drive. So now it goes like this:
(primary disc) **SATA disc** - Windows XP Pro
**IDE** (Primary Master) disc have 2 partitions. First one Ex2 (Installed Ubuntu) and the second one with free FAT32 space.

I can't get 'Dual Boot' to work properly. If I set in BIOS FirstBoot Device HDD-0 and SecondOne SATA I get dual boot screen (GRUB I think) but I can boot only Ubuntu. For WinXP booting fails - somekinda error - 0x7 ...
But if I set for FirstBootDevice the SATA disc I don't get any 'Dual Boot' screen. The system will load Windows.

The only thing I did about the 'Dual Boot' option was confirming 'YES' at the end of the Ubuntu installation. The part asking about GRUB Dual Boot.

How can I fix that? And BTW I'm a total freshman on Linux  :) Tnx!

---

### Post by aysiu on 2005-06-19
A few things to consider:

1. If you're sharing the computer with other users, have you consulted them to make sure a dual-boot is okay? People may not want to have a grub menu appear asking what OS they want to boot into every time they start the computer.

2. No matter how much you know what you're doing (and, clearly, you don't), it's *always* a good idea to back up your data. Especially since this is the first time you're configuring a dual-boot, back up *all* your data, and make sure you have the restore disks and all the installation software for your Windows programs.

3. If you want a user-friendly partitioner, try Mandriva or Mepis (you can use their partitioning tools and still install Ubuntu).

4. You may want to try playing around with the Ubuntu live CD a bit until you feel comfortable enough with the OS to know what you're doing.

---

### Post by X-Jumper on 2005-06-19
OK, here's the error msg that I get:

root (hd1,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

And after this nothing happens.

---


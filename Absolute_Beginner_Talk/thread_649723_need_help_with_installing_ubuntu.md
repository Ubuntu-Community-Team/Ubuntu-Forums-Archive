---
title: "need help with installing ubuntu"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by draze on 2007-12-25
so, here's the deal.
i have and old IDE 80 gigs hard drive with Win XP pro on it and like 8 gigs free space.

i decided to buy another 320-500 gigs hard drive since 80 gigs is not enough. so i wanted to partition my second hard drive and have like 2-3 operating systems on it (ubuntu, fedora, vista) and everything else for storage. but i have no idea how to partition it and how much space each operating system should require and since i will have 2 hard drives how do i choose which one to boot up from (from BIOS) or is there a faster way to choose between all of my operating systems. so as you noticed i'm copletely new to this.

please help with step-by-step instructions.

---

### Post by Dr Small on 2007-12-25
Greetings,
Please check out this link:
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

Dr Small

---

### Post by draze on 2007-12-25
that was useful reading. but it describes having XP and Ubuntu on the same hard drive. in my case it's 2 hard drives:
-1- 80GB with Win XP
-2- 320-500GB with Ubuntu, Fedora, Vista (or something else instead of fedora, i might change in future)

i want to know how to partition my second hard drive, since my first one is not partitioned i'll just leave it alone. so i want to have vista, ubuntu, and something else (eg. fedora). Ubuntu is gonna stay so will vista, but my 3rd partition is for other OSs, i'll just to play around with it. Plus everything that's left i guess is gonna go for data storage like videos, music.....and i guess it should be formatted with FAT32 since i can access  it  with win XP with Ubuntu and with Vista. is that right? if i have the right thinking, please give STEP-by-STEP instructions on how to partition the hard drive the best and the most productive way for my system.

please help.

---

### Post by Abboudi on 2007-12-25
please read it thru b4 u actually start doing anything

having two drives is not a problem,
the thing is to do this cleanly u need to sort ur installations right and hopefully u won't need to edit
the boot record or change any settings in ur machine's bios..

1.plug ur 2nd drive and install Vista Home Basic with  15 GB on it             ([http://support.microsoft.com/kb/919183](http://support.microsoft.com/kb/919183))
2.install fedora or any othes os u may go with using it's requirement for disk space
3.install "mighty" ubuntu 7.10 with 8 GB

note that u only need 1 swap partition for the "mighty" ubuntu and as well as the other os.. (given that it needs a swap partition)

the good thing is that "mighty" ubuntu is gonna take care of the boot record
and even better, it's gonna offer u to import ur win accounts into the sys
and also thru the partitioning part u can partition what's left of the drive for storage..

and about the fat32, you're right

I hope I was clear..

---

### Post by John.Michael.Kane on 2007-12-25
These may also be of help.
[Dualboot Two Hard Drives]("http://ubuntuforums.org/showthread.php?t=179902")
[How to dual-boot Ubuntu after installing them separately on two HDs]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=%28dual%29")

---

### Post by LunatikOwl on 2007-12-25
> **Abboudi said:**
> and about the fat32, you're right

Ubuntu Gutsy offers NTFS Read/Write out of the box, plus older kernels offer it with NTFS 3g or something(I used it successfully in Feisty and i was a REAL n00b back there so it shouldn't be a problem).

I would recommend using NTFS as the shared partition like i do since FAT32 is extremely prone to fragmentation.

---

### Post by draze on 2007-12-25
ok i kinda got the part of how many partitions i need but how do i actually partition then from the whole chunk? eg. NTFS format, or how to create /home partition for ubuntu

---

### Post by draze on 2007-12-25
still loking for some help please.

---

### Post by overdrank on 2007-12-25
> **draze said:**
> still loking for some help please.

HI and maybe these links will help
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by Abboudi on 2007-12-25
> **LunatikOwl said:**
> Ubuntu Gutsy offers NTFS Read/Write out of the box, plus older kernels offer it with NTFS 3g or something(I used it successfully in Feisty and i was a REAL n00b back there so it shouldn't be a problem).

I would recommend using NTFS as the shared partition like i do since FAT32 is extremely prone to fragmentation.

it's not win & :mighty: ubuntu, he wants another os as well....

---

### Post by Abboudi on 2007-12-25
> **draze said:**
> still loking for some help please.


what exactly didn;t u understand?

the partitioning, u don;t need to partition all of 'em from the begining:
1.l Vista Home Basic has  partitioning
2.fedora has 1 as wel or any othes decent os will have one
3."mighty" has partitioning

be specific draze

---

### Post by draze on 2007-12-26
if i get it right i : 

1)install Vista and during installation i make a partition with ~15 GB (NTFS) of space and install Vista on it.

now i got this 15GB with Vista + everything that's left from my SATA hard drive.

2)install ubuntu and during installation i make a Ubuntu partition ~8 GB  (Ext3) and a /home partition

now i got ~15GB (Vista/NTFS) + 8GB (Ubuntu/Ext3) + /home partition + all that's left

but here's the problem....when installing ubuntu is it going to ask me to create a new partition for it? or is going to offer me to choose from existing partitions already? and also how do i make a /home partition and what format?

3) since i havent decided about other OS, i'll leave it untouched (probably fedora core 8) .

4) make a swap partition (1.5-2 times the size of RAM) how do i do that? what format should it be?

so if i'm right i will get

~15GB (Vista/NTFS) + 8GB (Ubuntu/Ext3) + __GB (/home for Ubuntu / __format) + __GB (swap/__format) + __GB (someOS/some_format) + ~~(space/_ntfs or fat32 or what_)~~

as you already noticed, i'm a complete noob, but please, have patience and help me.
guide with step by step instructions. tell me i went wrong or where i might go wrong. just tell me what would you do but in noob language.

please and thanck you.

---

### Post by shareMenaPeace on 2007-12-26
You need to use manual partioning in ubuntu...delte the 8gb partition *NTFS* which vista made, thaen create a 256mb partition ..and choose from the menu SWAP ...the make the rest ext3 and choose mount point for it  .... and i would get a new HD btw ...very low space you have there :)

IMPORTEND is after you set the partioning and clicked next ...there comes a new window where you have to click advanced options ..so ubuntu makes the GRUB boot loader where you choose what to boot ..


Or get a external USB drive ...500gb under 100 euro

---

### Post by draze on 2007-12-26
yea. i'm leaving my old 80 GB with XP on it untouched adn buying a new one.

thx for help.

what about /home partition? and what is GRUB? and what does mount point means?

---

### Post by LaRoza on 2007-12-26
> **draze said:**
> 
what about /home partition? and what is GRUB?

You don't need a separate partition for /home, although some prefer it. It makes it easier to reinstall without losing data and settings. I don't create a separate partitions.

Grub is the bootloader. It is what is loaded when POST is done, before Linux or Windows loads.

---

### Post by draze on 2007-12-26
so...how big is grub? what format is it? and why not do the /home what if i might want to reinstall a newer version?

---

### Post by LaRoza on 2007-12-26
> **draze said:**
> so...how big is grub? what format is it? and why not do the /home what if i might want to reinstall a newer version?

The MBR is 512 bytes but grub is a little larger than that, so the MBR has code that points to it.

You can use a /home partition if you want, it can certainly make things easier for you.

(I don't store any of my files in /home, so I just backup the settings that are stored there. I use partitions for storing my data, mounted under /media)

---

### Post by chessercizes on 2007-12-26
> so...how big is grub? what format is it? and why not do the /home what if i might want to reinstall a newer version?

I would reccomend that you have a home partition because, if i'm not mistaken, you can share that home partition between both fedora and ubuntu; this would probably make life a lot easier for you.

---

### Post by draze on 2007-12-26
that's some good advices guys. thank you. is there anything else i should be aware of?

---

### Post by LaRoza on 2007-12-26
> **draze said:**
> that's some good advices guys. thank you. is there anything else i should be aware of?

Sharing /home between distros can cause problems sometimes.

---

### Post by overdrank on 2007-12-26
> **draze said:**
> that's some good advices guys. thank you. is there anything else i should be aware of?

And remember that you will have to create extended partition if you want more than 4 partitions on the drive.

---

### Post by draze on 2007-12-26
> **overdrank said:**
> And remember that you will have to create extended partition if you want more than 4 partitions on the drive.

what is that? how do you create that?

---

### Post by LaRoza on 2007-12-26
> **draze said:**
> what is that? how do you create that?

For a single hard disk, you can only have 4 primary partitions. If you want more, you have to use an extended partition. You make them with GParted. With an extended partition, you can create many (up to 64 I think) logical drives (partitions)

---

### Post by draze on 2007-12-26
so can i make after installing ubuntu? or do i have to do it before? since i got already 1 for vista, one for ubuntu, one is /home another one is swap, grub.....so i got 5 already.

i guess i'll need to use gparted....does it work with vista or xp?

---

### Post by LaRoza on 2007-12-26
> **draze said:**
> so can i make after installing ubuntu? or do i have to do it before? since i got already 1 for vista, one for ubuntu, one is /home another one is swap, grub.....so i got 5 already.

i guess i'll need to use gparted....does it work with vista or xp?

It works fine with both. Vista will want to check itself when you boot it, don't worry about it.

You can make:

1 Primary Vista NTFS (already in existance)
1 Primary Partition Ubuntu EXT3 (for root)
1 Extended:
and make the swap and /home partition in the extended partition.

---

### Post by draze on 2007-12-26
ok...where do i get departed for Vista? since i have  it installed already...or is only for linux?

---

### Post by LaRoza on 2007-12-26
> **draze said:**
> ok...where do i get departed for Vista? since i have  it installed already...or is only for linux?

GParted, see the link in my sig.

It is a bootable disk, so you boot from it. All it can really do is run GParted, although it is a Linux distro, stripped of almost everything.

---

### Post by draze on 2007-12-26
ok. thanx. i got it. do i have to waste the whole cd fro 50 mb? =D

---

### Post by LaRoza on 2007-12-26
> **draze said:**
> ok. thanx. i got it. do i have to waste the whole cd fro 50 mb? =D

You can get the GParted + Clonezilla cd.

Trust me, it isn't a waste, is the most useful tool I know of.

---

### Post by draze on 2007-12-26
> **LaRoza said:**
> You can get the GParted + Clonezilla cd.

Trust me, it isn't a waste, is the most useful tool I know of.
clonezilla.....what does this do?

can i put gparted.iso with ubuntu.iso on the same cd? actually nevermind...it won't fit.

---

### Post by LaRoza on 2007-12-26
> **draze said:**
> clonezilla.....what does this do?

can i put gparted.iso with ubuntu.iso on the same cd?

Isn't it describe in the link in my sig?

It can image drives and partitions and restore them.

Yes, but it takes a lot of work to get them both bootable, and I don't know how to do it.

---

### Post by draze on 2007-12-26
> **LaRoza said:**
> Isn't it describe in the link in my sig?

It can image drives and partitions and restore them.

Yes, but it takes a lot of work to get them both bootable, and I don't know how to do it.

so do i just download Gparted and after Clonezilla and put two iso on cd? how they gonna work?

nevermind. i found it. gosh...i'm so impatient.

---

### Post by LaRoza on 2007-12-26
> **draze said:**
> so do i just download Gparted and after Clonezilla and put two iso on cd? how they gonna work?

nevermind. i found it. gosh...i'm so impatient.

On the page, there is an entry for GParted, one for Clonezilla and one for GParted+Clonzezilla

The third one is an ISO of both of them, which you burn like a regular ISO. When it starts, you get a boot menu.

---

### Post by draze on 2007-12-26
> **LaRoza said:**
> It works fine with both. Vista will want to check itself when you boot it, don't worry about it.

You can make:

1 Primary Vista NTFS (already in existance)
1 Primary Partition Ubuntu EXT3 (for root)
1 Extended:
and make the swap and /home partition in the extended partition.

1 extended is a swap and /home only or is it with everything that's left from hard drive. how do i make a /home partition? does gparted has this option?

---

### Post by LaRoza on 2007-12-26
> **draze said:**
> 1 extended is a swap and /home only or is it with everything that's left from hard drive. how do i make a /home partition? does gparted has this option?

Just make the partitions, when you install Ubuntu, you can specific the mount points.

What size is your drive?

---

### Post by draze on 2007-12-26
500

---

### Post by draze on 2007-12-26
how to make mount points, and my my hard drive is 500GB

---

### Post by LaRoza on 2007-12-26
> **draze said:**
> how to make mount points, and my my hard drive is 500GB

You have Windows installed already right?

Use GParted to shrink the Windows partition, to about twice the size that it is full. (If it is 16 GB full, make it 32) Remember to defrag and backup before doing this.

Create:

1 Primary Partition, the same size as the Windows partition, format as EXT3

1 Extended Partition, in it:
    create an EXT3 Partition that is as big as you think /home needs to be
    create Swap, about 512 will be enough

In the extended partition, you might want to make a logical drive that you can use to share data between Linux and Windows. Don't format it with Gparted, just make the partition

After applying this scheme, boot into Windows, and format the unformated partition as NTFS

Now boot the Ubuntu disk and install it, but specific the / to be in the second primary partition (ext3) and home to be in the third (logical drive, ext2) and swap as swap (shoudl be automatic).

---

### Post by draze on 2007-12-26
> **LaRoza said:**
> You have Windows installed already right?

Use GParted to shrink the Windows partition, to about twice the size that it is full. (If it is 16 GB full, make it 32) Remember to defrag and backup before doing this.

yea i have Vista installed. It's 15 GB why do i double up the space for Vista?

---

### Post by LaRoza on 2007-12-26
> **draze said:**
> yea i have Vista installed. It's 15 GB why do i double up the space for Vista?

For the page file and future programs. It is just a little convention I follow. It always works for me.

When you reboot into Vista (to do the final format of the NTFS partition, Vista will do a file system check, don't worry about it.

---

### Post by draze on 2007-12-26
alright. looks like i'm ready to start working. i'll let you guys know if i'll have any problems. thnx to evryone who helped. big thanx to LaRoza for time and patience.

---

### Post by LaRoza on 2007-12-26
> **draze said:**
> alright. looks like i'm ready to start working. i'll let you guys know if i'll have any problems. thnx to evryone who helped. big thanx to LaRoza for time and patience.

I have been on the forums since last night, I haven't slept. This is fun, am I dedicated or insane?

Actually, I am just a bot.

---


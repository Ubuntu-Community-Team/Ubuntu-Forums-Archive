---
title: "Dual-boot Partition Strategy Recommendations"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Curbuntu on 2007-08-08
"Look for the silver lining in every cloud."  My dark cloud is that an aborted WUBI installation seems to have trashed my MBR in WinXP.  If I can't get the restore CD to fix it, it may be time to slick the drive and start from scratch.  (Don't worry -- we are systematically paranoid about data backup here at the house, so not a bit of data will lost if I have to slick the drive.  BTW, is the an Ubuntu-compatible functional equivalent of Windows-based Memeo software?)

Anyway, the **silver lining** may be that I can start out with partitions the way they ought to be for a dual-boot install of Ubuntu 7.04.  Here are my specs, and here's what I'm thinking.  (Warning: I am a Linux newbie and don't have a clue about what is best for Ubuntu.)

On my laptop (the machine in question), I'm running an AMD64 Athlon 3200+ (2.2 MHz -- should I really used the 64-bit version of Feisty Fawn?).  The hard drive is nominally 120 Gb (more like 111 Gb in actuality), of which almost 66 Gb are taken up already (after a ruthless delete session in WinXP "safe" mode this afternoon).  FWIW, there's 1 Gb of RAM (but only 64 Mb of discreet VRAM).  Right now everything is in one partition.

My proposal: 

[LIST=1]
[*]A partition for WinXP and related Win apps (Office 2003, etc.)

[*]A partition for (essentially) "My Documents" -- all docs, spreadsheets, data, pictures, music, etc.  The thought here is that if there is a file scheme that is read/write compatible to both WinXP and Ubuntu (FAT32? I've heard NTFS can't be read by Linux on the same machine, and WinXP can't read etc), such a setup would allow data sharing (say between OpenOffice and Office 2003), essentially making the Ubuntu partition "bigger" (because it won't have to store data).  How big partitions 1 & 2 will be I still have to work out.

[*]Then would come the Ubuntu partition.  (Or would there be more than one?)  I think I could devote at least 10 Gb to it.  (WinXP gets downright lethargic if it doesn't have at least 15% of drive/partition capacity free for defragging, etc.)
[/LIST]

Does this plan make any sense?  Is there a better way?  I'd like to have a setup where the data ("My Documents") looks like it's arranged in more or less the same way, whether I access it from WinXP or Ubuntu.  

If I didn't rely so heavily on an application (Libronix/Logos) that hasn't been ported to Linux (though it's finally being ported to the Mac, so there's hope), and if we weren't so heavily invested in the multiplicity of features in Outlook 2003 (complete with synching to a PocketPC), I might just take the only-Ubuntu plunge.  But being able to truly dual-boot (as opposed to the WUBI method) will give me some time to really get to know Linux and Ubuntu.

P.S.: Any recommendations on free disk-partitioning software that can either run from Windows or from a boot disc/CD?

---

### Post by Murrquan on 2007-08-08
I'd just like to say that I'm in the same boat the OP is! I know Ubuntu is great about installing alongside XP, but I'm wanting to switch from Fedora 7 to an Ubuntu / XP dual-booting system, and I'd really like some advice.

I actually tried to set up Fedora in a dual-boot configuration, but I think I messed up the partitioning or something because when I booted from the XP CD (OEM, came with the notebook), it briefly flashed some text about loading it and then just stayed there with a blank screen. I don't know what I did, but I sure hope there's a way around it. x_X I do know I didn't set up the partitions properly that time, but I don't remember how.

I'm not as concerned about a partition both OSes can access. I just want to get XP and Ubuntu running on the same notebook, and would like to know how to set up the partitions and in what order to install things. I would be interested in hearing about ways to cross over partitions, though.

---

### Post by MQMike on 2007-08-08
P.S.: Any recommendations on free disk-partitioning software that can either run from Windows or from a boot disc/CD?

No question about that:

GParted:   [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
GParted how-to:   [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by MQMike on 2007-08-08
Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)
The Classic dual-boot GRUB reference

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by deserthowler on 2007-08-08
My last windows linux multiple boot was Win98 and Win2K dual booting.  I then added Linux to dual boot with the windows dual boot.  This was Mandrake 10 so what I say might not apply but this is the way I would do it.

First partition WinXP
Second partition WinXP swap partition (I find a separate Windows swap partition with the full partition allocated as swap works best.)
Third partition Fat32 files to be shared with Win and Ubuntu
4th partition (extended) Ubuntu.

I run WinXP, 2K, and 98 in VirtualBox on my Ubuntu laptop as I make some of my living fixing these systems for people and need them handy.:lolflag:  I make more money off fixing Windows systems than I ever will off Linux tight-wads.

Earl

---

### Post by Curbuntu on 2007-08-08
Thanks.  This looks like the tool, and the tutorial doesn't appear intimidating.  (I used older versions of Partition Magic in days of yore.)  I do wish I knew more about the Linux file system, though, before starting.

---

### Post by Curbuntu on 2007-08-08
> **deserthowler said:**
> My last windows linux multiple boot was Win98 and Win2K dual booting.  I then added Linux to dual boot with the windows dual boot.  This was Mandrake 10 so what I say might not apply but this is the way I would do it.

First partition WinXP
Second partition WinXP swap partition (I find a separate Windows swap partition with the full partition allocated as swap works best.)
Third partition Fat32 files to be shared with Win and Ubuntu
4th partition (extended) Ubuntu.

I run WinXP, 2K, and 98 in VirtualBox on my Ubuntu laptop as I make some of my living fixing these systems for people and need them handy.:lolflag:  I make more money off fixing Windows systems than I ever will off Linux tight-wads.

Earl

Thanks for the feedback.  Some quick responses:

[LIST=1]
[*]Does that mean that I was correct about the FAT32 partition being shareable/accessible by both operating systems?  Does this mean that it's also correct that NTFS can't be read?

[*]As for the idea about the swap partition -- I'm open to the idea.  Why would it be better that way?  And (given the nominal 120 Gb size of the entire drive) any recommendations about the size of the swap file/partition?

[*]Third Partition: would this make this "Drive E:" in Windows?  (Not that it matters too much.)

[*]Fourth Partition: could you elaborate on the word "extended"?  I recall the term from previous forays into FDISK, but that was some time ago...

[*]VirtualBox: Here you throw a major curve ball.  Only one partition would be needed, and there wouldn't be a need to guess the size of the other partitions.  It also opens up other options (e.g., Win98, as you mention; I am my family's "tech guy," for better or for worse).  It does make me wonder where the files to be shared by Ubuntu and WinXP would actually "reside" and how Ubuntu apps could get at them.  Do you find VirtualBox better than VMWare or other products?  Is this a better way to attack the problem, or would it be "way over my head" as a newbie?
[/LIST]

Thanks for your patience.  It helps to know that you have feet firmly planted in both camps (Ubuntu and WinXP).

---

### Post by Curbuntu on 2007-08-08
> **MQMike said:**
> Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)
The Classic dual-boot GRUB reference

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

Wow.  Between the two of these links, there are nearly 110 printed pages (so says Print Preview).  Do I need to read it all (the thought makes all of the Linux horror stories stir in the back of the newbie's mind) or are there particular important passages or concepts on which I should be concentrating?

---

### Post by _duncan_ on 2007-08-09
If I'm installing a multi-boot system to a new 120 GB drive, I'll probably partition the drive this way:

partition 1:   8 GB, ext3, Ubuntu Feisty root (/)
partition 2: 20 GB, NTFS,  Windows XP
partition 3:   8 GB, ext3, spare root partition for other linux distro.
------------------------
partition 4: Extended partition (the rest of the hard drive)
partition 5: 1 GB, linux swap (can be shared by both linux OS)
partition 6: 2 GB, FAT32, for transferring files between linux and windows.
partition 7: what remains of partition 4 after 5 & 6, Ubuntu Feisty home directory (/home)


Notes:

1. Partition 4 is not really a *true* parition (i.e. extended partition). It's main purpose is to contain partitions 5, 6 and 7 since you can only divide a drive into a maximum of 4 main partitions.

2. Change the allocated space for win xp to suit your needs. If you need more than 20 GB, that space will be taken from partition 7, and consequently partition 4.

3. Partition 6, the FAT32 partition, is solely for transfer purposes. As such, it should be sized to accommodate the largest single file you expect to transfer between OS's. It's not meant for keeping common files. I personally like to keep my OS's as independent from each other as possible. *Due to technical limitations of the FAT32 format, the maximum possible size of a FAT32 partition is only 4 GB*.

4. A default install of Ubuntu takes up 2-3 GB space, leaving about 5-6 GB on the root (/) partition. You can make partitions 1 and 3 smaller or bigger based on how much additional packages you plan to install.

5. Having a separate /home partition for linux installation is good practice. It saves the trouble of having to recreate/reorganize your personal linux files in case of reinstallation. Notice that I normally make this the largest partition, since I also use it to contain virtual machines running under ubuntu. The virtual machine files tend to be huge.

6. Partition 3 can be used to experiment with other distros. It also comes in handy when it's time to upgrade Ubuntu to the next version. Instead of updating the existing ubuntu installation directly (partition 1), it is more conservative to install the newer version to another partition (in this case partition 3), work out the kinks for a week or two, then decide if you want to keep the newer version or revert back to the earlier version. If the new version is OK, then partition 1 becomes your spare partition and partition 3 becomes the main linux root partition.

7. In terms of process, I'll partition the hard drive to the above scheme using gparted live CD, then install windows first, then ubuntu last. That's because the xp installer is a bit egocentric. It assumes that xp is the only OS in a computer, and will configure the MBR that way. Ubuntu and most linux distros are better at recognizing the existence of other OS's on the same computer.

---

### Post by Curbuntu on 2007-08-09
This is an interesting strategy.  Let me respond seriatim:

> **_duncan_ said:**
> 
1. Partition 4 is not really a *true* parition (i.e. extended partition). It's main purpose is to contain partitions 5, 6 and 7 since you can only divide a drive into a maximum of 4 main partitions.

Ah, yes, the whole thing about extensions starts to come back.  I guess once Windows started to recognize large hard drive capacities, I never felt like I had to partition again.

> 
3. Partition 6, the FAT32 partition, is solely for transfer purposes. As such, it should be sized to accommodate the largest single file you expect to transfer between OS's. It's not meant for keeping common files. I personally like to keep my OS's as independent from each other as possible. *Due to technical limitations of the FAT32 format, the maximum possible size of a FAT32 partition is only 4 GB*.

Again, it's been so long that I had forgotten about the 4 Gb limitation for FAT32.  Thanks for the reality-check reminder!  But this "transfer" partition is a good idea.  In fact, it could also be used for current projects, and thus accessible to either OS's apps.

*Which brings up another thought:* **would it be better to keep Windows docs, files, etc. in their own NTFS partition** (in case I ever have to reinstall Windows (and other apps) in its own partition?  Looking at your partitioning strategy (which I didn't "quote"), I wouldn't have any need for an extra Linux partition -- learning Ubuntu and the command line will be all the experimenting I need to do for the time being.

> 4. A default install of Ubuntu takes up 2-3 GB space, leaving about 5-6 GB on the root (/) partition. You can make partitions 1 and 3 smaller or bigger based on how much additional packages you plan to install.

As the whole purpose of this exercise is the learn Ubuntu and Linux-based apps, I'm wondering if 10-12 Gb wouldn't be more in line.  But maybe "my eyes are bigger than my stomach." Or maybe Linux/Ubuntu apps aren't nearly as bloated as Windows apps.

> 5. Having a separate /home partition for linux installation is good practice. It saves the trouble of having to recreate/reorganize your personal linux files in case of reinstallation. Notice that I normally make this the largest partition, since I also use it to contain virtual machines running under ubuntu. The virtual machine files tend to be huge.

Ah, an interesting strategy!  (Especially in keeping with your Point #6 below.)  I  hadn't thought about Ubuntu *updates.*  But remember that you're dealing with a newbie.  Getting all of these partitions made with gparted should be straightforward, BUT is there a way to tell the Ubuntu 7.04 installer that I desire to declare a different partition as /home?

> 6. Partition 3 can be used to experiment with other distros. It also comes in handy when it's time to upgrade Ubuntu to the next version. Instead of updating the existing ubuntu installation directly (partition 1), it is more conservative to install the newer version to another partition (in this case partition 3), work out the kinks for a week or two, then decide if you want to keep the newer version or revert back to the earlier version. If the new version is OK, then partition 1 becomes your spare partition and partition 3 becomes the main linux root partition.

It's a good thing I re-read this.  As I indicated above, I had sort of written off this part of the partitioning, thinking, "Hey, I only want to try Ubuntu, not some other Linux."  I assume changing the root partition in this instance means figuring out how to edit the GRUB menu, right?

> 7. In terms of process, I'll partition the hard drive to the above scheme using gparted live CD, then install windows first, then ubuntu last. That's because the xp installer is a bit egocentric. It assumes that xp is the only OS in a computer, and will configure the MBR that way. Ubuntu and most linux distros are better at recognizing the existence of other OS's on the same computer.

Out of curiosity, why would Ubuntu have to be in the first partition, especially if WinXP is (as you say) "egocentric"?  Will XP be "happy" in the second partition?  If I left my current XP installation alone (assuming that we get past the current MBR problem) and just repartitioned "after" it (that is, shrank its partition using gparted) and followed your general partitioning scheme, would that still work (assuming the XP partition/install/data survived the "shrinking")?

Your feedback and that of other contributors on this thread is saving me a LOT of trial and error (and maybe *generating* some for me as well :) ), and I really thank you all for the unstinting mentoring.

---

### Post by _duncan_ on 2007-08-10
> Which brings up another thought: would it be better to keep Windows docs, files, etc. in their own NTFS partition (in case I ever have to reinstall Windows (and other apps) in its own partition? Looking at your partitioning strategy (which I didn't "quote"), I wouldn't have any need for an extra Linux partition -- learning Ubuntu and the command line will be all the experimenting I need to do for the time being.

It really depends on the amount of work you're going to do with Windows vis-a-vis ubuntu. If it's significant, then yes, it may be worth having a separate NTFS partition... It's also a question of comfort level. The scheme I mentioned already has 7 partitions, so a lot of users would balk at the thought of adding yet another partition... BTW, you have to view this comment with a grain of salt. You are talking to a guy who hasn't booted into his xp partition for more than a year. :)

> As the whole purpose of this exercise is the learn Ubuntu and Linux-based apps, I'm wondering if 10-12 Gb wouldn't be more in line. But maybe "my eyes are bigger than my stomach." Or maybe Linux/Ubuntu apps aren't nearly as bloated as Windows apps.

I don't think anyone can help you narrow this down. It shouldn't be a major issue though since you're working with a 120 GB drive. What's 4 GB if it makes you feel a lot better. :)

> Ah, an interesting strategy! (Especially in keeping with your Point #6 below.) I hadn't thought about Ubuntu updates. But remember that you're dealing with a newbie. Getting all of these partitions made with gparted should be straightforward, BUT is there a way to tell the Ubuntu 7.04 installer that I desire to declare a different partition as /home?


Yes, the ubuntu installer is designed for that.

> It's a good thing I re-read this. As I indicated above, I had sort of written off this part of the partitioning, thinking, "Hey, I only want to try Ubuntu, not some other Linux." I assume changing the root partition in this instance means figuring out how to edit the GRUB menu, right?

Not necessarily. All you have to do is tell the installer you want to put the new install in the spare partition. After installation, a new GRUB menu list will be made. If done correctly, you will have the choice to boot to 3 OS: windows, the old ubuntu, and the new ubuntu. Like I said in the orig post, ubuntu is good at detecting other OS's. So the new installation will *see* the old version plus windows and add itself as the 3rd OS automatically.

Ha ha ha... come back and read this post after a year. By then, you probably have 2 or 3 other distros installed alongside ubuntu and xp. Once the steep learning curve has been breached with one distro, it's quite easy (and sometimes beneficial) to experiment with other distros.

> Out of curiosity, why would Ubuntu have to be in the first partition, especially if WinXP is (as you say) "egocentric"? Will XP be "happy" in the second partition? If I left my current XP installation alone (assuming that we get past the current MBR problem) and just repartitioned "after" it (that is, shrank its partition using gparted) and followed your general partitioning scheme, would that still work (assuming the XP partition/install/data survived the "shrinking")?

The order of the first 3 main partitions doesn't really matter. If you can *save* your current xp installation at the first partition, ubuntu will work equally well on the 2nd or 3rd partition. In fact, you can even use an extended partition for ubuntu... XP is egocentric when it comes to the MBR, not with regards to partition it is placed.


BTW, if you are able to save the current xp installation, please defragment the NTFS partition before attempting any *shrinking*. I've heard horror stories caused by shrinking a heavily-fragmented NTFS partition.

---

### Post by Curbuntu on 2007-08-11
> **_duncan_ said:**
> 3. Partition 6, the FAT32 partition, is solely for transfer purposes. As such, it should be sized to accommodate the largest single file you expect to transfer between OS's. It's not meant for keeping common files. I personally like to keep my OS's as independent from each other as possible. *Due to technical limitations of the FAT32 format, the maximum possible size of a FAT32 partition is only 4 GB*.

Something's been gnawing at the back of my mind about this statement. so I went to the MS Knowledge Base and discovered that this 4 Gb limitation is not quite on target.  **File size limitation** under FAT32 is 4 Gb.  Partition size limitation is... well, it depends on what program sets up the partition.  Win2K and XP limit the partition-creation size to 32 Gb, but *they can **use** a larger FAT32* partition if made by another program.  (Curiously, "the maximum [FAT32] volume size that Windows 98 can create is 127.53 GB"!)  But one MSKB page clearly says, "FAT32 supports drives up to 2 terabytes in size," by which I assume it means that the partition can be that large.  (FWIW, MSKB reports that the FAT**16** theoretical volume limit was 4 Gb (but effectively 2 Gb or less, because of the of the 64Kb cluster size).  See [http://www.microsoft.com/technet/prodtechnol/windows2000serv/reskit/prork/prdf_fls_pxjh.mspx?mfr=true]("http://www.microsoft.com/technet/prodtechnol/windows2000serv/reskit/prork/prdf_fls_pxjh.mspx?mfr=true")  for the details.

So that might let me combine ideas.  Basically, my idea of having my WinXP data, docs, etc. on their own FAT32 partition would serve that purpose *and* the purpose of your proposed 2 Gb FAT32 swap partition.  This would allow storage of all "work" files from both OSes in one place, making backup easier.  Thoughts?

---

### Post by Kilgore_Trout on 2007-08-11
Hi Curbuntu,

I am in the midst of setting up a dual boot myself (have to start using a windows only app as well), and for what it's worth, this is what I am planning on doing:

HDD 1 (30 GB)

8GB ubuntu / (ext3)
4GB ubuntu /home (ext3)
16GB windows xp (ntfs)
1GB ubuntu swap (swap)

HDD2 (120 GB)

30GB work-related storage (ntfs)
~80GB music/photos storage (ntfs)

The idea being that I'll be able to access the storage drive from xp or from ubuntu using ntfs-3g.  The reason for not using ext3 (and a windows utility) is to keep windows from having write access to linux.

From what I gather, ntfs-3g is in the repos and is relatively stable, but I can't say either way as I haven't started using it yet.  Anybody else care to weigh in?

---

### Post by _duncan_ on 2007-08-11
My apologies. I stand corrected regarding the 4 GB limitations. However, there are security considerations opting for FAT32 format vs. NTFS format which I'd rather not go into.

Like I mentioned in my orig post, my personal preference is to keep OSs as independent from each other as possible, even to the point of duplicating files, with the only gray area being the transfer partition. Hence, such a partition scheme. At the end of the day, you will have to weigh the risk / convenience factors and choose the one that suits you best.

---

### Post by Nevon on 2007-08-11
I haven't read through the entire thread, so excuse me if I'm repeating something that has already been said. 
When I was setting up my partitions, I had the same things as you in mind. I wanted to have XP on one partition, Ubuntu on one, and a big storage partition. I read up on the different file systems, and quickly found that ext3 is not supported by Ubuntu, and NTFS is not natively supported by Ubuntu. However, using a program called ntsf-3g (in Ubuntu) you can make NTFS partition read- and writable in Ubuntu, thus solving my problem with having a common storage media. 

I have a total of  372.6gb of hard drive capacity, and this is how I spread it out:
11.1gb for a windows partition (NTFS)
20.5gb for Ubuntu installation (ext3)
4gb for a Linux swap (linux-swap)
74.5gb storage (NFTS)
262,7gb storage (NTFS)

In retrospect I wish I had set the ext3 partition to maybe 30gb instead, just to make sure I never run out of space when I install stuff in Ubuntu. My original thought was that I would install all programs on the storage partitions, but I didn't know then that you usually don't get to decide where to install programs in ubuntu. 
Except for that, I'm pretty happy with my set up. The reason I have two different storage partitions is because I have two physical hard drives.

---

### Post by deserthowler on 2007-08-11
> **Curbuntu said:**
> Thanks for the feedback.  Some quick responses:
[*]Does that mean that I was correct about the FAT32 partition being shareable/accessible by both operating systems?  Does this mean that it's also correct that NTFS can't be read?
At the time i was doing this was true so I habitually stick to FAT32 for all of my Windows partitions.  It also lets me get into the partition with a live CD if necessary.

> [*]As for the idea about the swap partition -- I'm open to the idea.  Why would it be better that way?  And (given the nominal 120 Gb size of the entire drive) any recommendations about the size of the swap file/partition?
In Windows the swap partition is always used.  If I make it a separate partition  (3xmemory) it doesn't get fragmented.

> [*]Third Partition: would this make this "Drive E:" in Windows?  (Not that it matters too much.)
Yes

> [*]Fourth Partition: could you elaborate on the word "extended"?  I recall the term from previous forays into FDISK, but that was some time ago...
I think it is some kind of ancient DOS mumbo-jumbo that is a legacy of the 386 or earlier.

> [*]VirtualBox: Here you throw a major curve ball.  Only one partition would be needed, and there wouldn't be a need to guess the size of the other partitions.  It also opens up other options (e.g., Win98, as you mention; I am my family's "tech guy," for better or for worse).  It does make me wonder where the files to be shared by Ubuntu and WinXP would actually "reside" and how Ubuntu apps could get at them.  Do you find VirtualBox better than VMWare or other products?  Is this a better way to attack the problem, or would it be "way over my head" as a newbie?
Well, I haven't gotten everything to work with Virtual Box.  Sound and USB support are two I'm working on yet.  If you want to do multimedia with Windows I can't recommend VBox as I haven't got them going yet.  I am still experimenting but it works well enough for my purposes.

> Thanks for your patience.  It helps to know that you have feet firmly planted in both camps (Ubuntu and WinXP).

Here, from my notes and memory :confused: , is my last use of Windows in a dual boot (using Windows notation)
C: Win98 --- 3GB FAT32
D: Win2K --- 10GB FAT32
E: shared --- 8GB FAT32
F: extended ---20GB
I had Ubuntu and Kubuntu installed on this partition but don't remember what they were DOS notationwise.  I think they each totaled 9 GB and shared a 2GB swap file.
There was a triple boot with Ubuntu, Kubuntu and Windows.  There was a dual boot between Win98 and Win2K.

I hope this helps
Earl

---

### Post by hartdg on 2007-08-12
> **_duncan_ said:**
> 
The order of the first 3 main partitions doesn't really matter. If you can *save* your current xp installation at the first partition, ubuntu will work equally well on the 2nd or 3rd partition. In fact, you can even use an extended partition for ubuntu... XP is egocentric when it comes to the MBR, not with regards to partition it is placed.

I'm in the process of setting up a new PC as a dual-boot (or is it duel-boot?).

I first used gparted on the Ubuntu Live CD to create the partitions on a new (virgin) disk for Linux and Win XP. The NTFS partition (for XP) was the 2nd or 3rd partition partition. I then tried several times to install XP on the partition (booting from the XP installation disk). On each occasion the installation failed about 30min later. :confused:

Eventually I deleted all the partitions (using Ubuntu Live CD and gparted) and let the XP installation disk create it's own partition (which I limited to 25GB out of 320GB). Once XP was installed I used gparted (again on the Ubuntu Live CD) to create the other partitions I needed.:)

Fortunately (as Duncan says) Ubuntu (& grub) is pretty well house trained and flexible about how it is installed.

For those who have an interest in disk partitioning strategies: have a look at 
[http://radified.com/index2.html](http://radified.com/index2.html) (look down the list of Guides on the left side of the page). The author has some interesting and well motivated views on partitioning hard disks. There is also a guide to installing Windows which I'm trying to follow as part of the XP side of the dual-boot.

Dave

---

### Post by deserthowler on 2007-08-12
> **Curbuntu said:**
> So that might let me combine ideas.  Basically, my idea of having my WinXP data, docs, etc. on their own FAT32 partition would serve that purpose *and* the purpose of your proposed 2 Gb FAT32 swap partition.  This would allow storage of all "work" files from both OSes in one place, making backup easier.  Thoughts?

It worked fine for me.  I used OpenOffice and MS office on my Windows machine but MS office for only very few docs that didn't translate and kept them on the Windows partition.  OO translation has improved greatly since then. 

Earl

---

### Post by steve.horsley on 2007-08-12
> [QUOTE]Fourth Partition: could you elaborate on the word "extended"? I recall the term from previous forays into FDISK, but that was some time ago...I think it is some kind of ancient DOS mumbo-jumbo that is a legacy of the 386 or earlier.[/QUOTE]
I have to correct this.
The original PC hard disk had exactly 4 partitions, although often only 1 would be used. The MBR has space allocated for a table that says how much of the disk each of the 4  partitions occupies. When nore that 4 partitons were wanted, they invented an "extended" partition, which behaved as a container for any number of "logical" partitions.  So a disk has 4 primary partitions, 3 of which might not be used, and one of which is allowed to be an extended partition. The extended partition could be the only primary partition and encompass the whole disk. If there is an extended partition, it will contain any number of logical partitions, each occupying a propoption of the space that the overall extended partition contains. 
 
It's like having planning permission for a short road with 4 houses, one of which can be a block of flats instead.

---

### Post by Curbuntu on 2007-08-13
> **steve.horsley said:**
> It's like having planning permission for a short road with 4 houses, one of which can be a block of flats instead.

I think that's a very apt and easy-to-understand analogy!  Thanks.

---


---
title: "How exactly do you partition a hard drive for dual booting Xubuntu and xp?"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by farmer26 on 2006-12-08
At the moment I have xp installed on a pc with a 68.5gb hard drive. I want to dual boot xp and Xubuntu. Do I need to partition my drives with software prior to installing, or can I do it in the installation? The way I want to do it is like this (which may be completely wrong):

The primary drive with xp (NTFS), an extended drive for sharing files between xp and linux (fat32), a logical drive for /home (ext3), another logical drive for swap (1gb as I have 512mb ram), and another logical for Linux (ext3).

Is this about right or is it a load of rubbish? How much space do you think each drive should be. I would like to put most things on the shared drive. Would I need the Linux drive for anything other than the original install of Xubuntu, as I intend to save as much as possible to the shared drive? Could I install new Xubuntu versions as they come out without changing anything apart from the Linux drive?

I am completely new to linux as you can probably tell, so any help would be appreciated.

---

### Post by aysiu on 2006-12-08
You can partition during the installation, but make sure you defragment and **back up** before you do anything.

For partition planning, read this:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Here are two dual boot guides...

**Desktop CD**:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

**Alternate CD**:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by farmer26 on 2006-12-08
Thanks a lot I'll read those guides

---

### Post by aysiu on 2006-12-08
> **farmer26 said:**
> Thanks a lot I'll read those guides
Post back any questions you may have, no matter how "stupid" they may seem to you. It's always better to take it slow.

---

### Post by farmer26 on 2006-12-08
I have looked on the partition planning website and I would like to have my hard drive the same as I said above, except merging the /home and shared in a ext3 drive, using FS-Drive so that Windows can access it. Will this work properly, and what does access rights mean, as that is mentioned as being a possible problem? Thanks for your help so far!

---

### Post by aysiu on 2006-12-08
Sure, that can work.

---

### Post by farmer26 on 2006-12-08
Okay, so can I set it up like this:
windows ntfs drive as the primary (partition 1)
shared + /home ext3 as extended (partition 2)
Xubuntu ext3 as logical (partition 3)
swap as logical (partition 4)

---

### Post by aysiu on 2006-12-08
Well, I don't really know what a logical partition is and an extended partition is, but the general layout looks fine to me. I would try to make the shared and home partition as large as possible.

Xubuntu won't need more than 4 GB, but you can give it 6 GB to be safe.

---

### Post by farmer26 on 2006-12-08
Ok, I'll give it 6 GB as I don't want to mess anything up. I need 1 GB for swap and that leaves me with 61.5 GB on shared and /home, minus whatever Windows takes up. Do you know how much I should need for xp? I have started installing FS-Drive and it says I need to "create the drive letters of my volumes with the ext2 file system." What does this mean?

---

### Post by loserboy on 2006-12-08
I think what it means is that windows has to see drive letters (as in  "C:" to be able to read from it, whereas linux doesnt use it like that, but I haven't used fs-drive so maybe i should keep my mouth shut

---

### Post by farmer26 on 2006-12-08
So does it matter what drive letter I assign to it?

---

### Post by loserboy on 2006-12-08
I should really take a look at Fs-drive before i say anything, but i assume you should give it higher letters starting at G: or something so it doesnt mess with any other possible drives you might have virtual or physical

---

### Post by farmer26 on 2006-12-08
Ok I only have a C: and D: (Disk) drive at the moment so I'll call it E: as that's the highest I have left.

---

### Post by farmer26 on 2006-12-08
I called it E: and it works fine, but it is only 6 GB and I want it to be the largest partition on my computer, allowing me to copy non-windows files from C: for access in Linux. How can I make it larger? By the way, which files are the windows files (the ones which need to stay on C: , my primary partition)?

---

### Post by loserboy on 2006-12-08
@aysiu maybe I shouldnt have taken over lol

@farmer ok its hard for me to picture what you're saying without seeing the partitions on the screen. 
1. I thought the 6gig part was made for the root xubuntu files?
2. important windows files will be on c:/winodows if thats what you mean
3. are you using Gparted for partitioning?

---

### Post by loserboy on 2006-12-08
I dont wanna make things more difficult for you now that you're in this sorta deep, but for me it's easier just to have a Fat32 partition for sharing between windows and linux (as they can both read/write on it)

for example my setup is

|XP - 20GB| Linux/home&/root - 40GB|Fat32Share - 19GB|Swap - 1GB|

obviously xp is primary (cuz it likes it that way) the rest is extended/logical

---

### Post by farmer26 on 2006-12-09
Yeah I agree with you, I've got rid of the fs-drive thing as I don't want to over-complicate things.

I haven't made any partitions yet, I was going to make them when I installed Xubuntu - is that possible?

I know I need to keep xp on the primary drive, but is it only the C:/windows folder that needs to stay there so it can boot ok?

---

### Post by vash5556 on 2006-12-09
yes it is possible to set up the partitions durring the install.  other than that i am not sure what you would need to have on the windows partition, just leaving the files as it is on the partition so far should be fine for your uses.

---

### Post by farmer26 on 2006-12-09
All my files, music, videos, pictures, games are on an ntfs file system. When I partition my drive, if I leave those files on there they will not be accessible to Linux. I want to move as much as I can to a shared fat32 partition. This means I want to have the windows ntfs drive as small as possible, allowing me to have the shared fat32 partiton as large as possible. So I want to know which files I need to leave on the ntfs partition in order for xp to boot up ok.

---

### Post by louieb on 2006-12-09
I guess I will add to the confusion with my two cents worth.[LIST]
[*]I don't know where the 1.5 - 2 x memory for swap space came from but I have found that .25 gig to .5 gig is plenty for swap. The more real memory you have it goes to reason the less swap will be used.
[*]FS-Drive is a piece of cake. After you install it you go into the control panel and open it up and assign a drive letter to your EXT3 EXT2 Linux partitions. (It list them for you) after its setup your Linux partition(s) look like any other Windows Drive. Because of that I use ext3 for my shared data on my dual boot machine.
[*]As far as Drive letters in windows goes you got A-Z you can use. But don't know if A&B  can be used for anything but a floppy.
[*]Space allocation. I have XP installed on an 8 gig drive on 1 computer. It has just the base install with just a few added programs and that disk is about half full.
[*]On that same computer Ubuntu is installed on a second hard drive. My / partition is 10 gig and it is about half full, but I have quite a few programs installed over the base.
[*]The remainder of the second drive is my /home partition minus .5 gig of swap. This is where I keep any file I want to share between XP and Linux stored.
[*]Just remember it really bad news when a Linux system runs out of space. IF you think you will be adding a lot of stuff. It would be much easier to install LVM from the beginning if you know you are going to add more space later.    (this is clearly a case of do as I say and not as I do).  I don't use LVM, if I fill up a partition I'll deal with it then.[/LIST]

---

### Post by loserboy on 2006-12-09
ok i see what you're saying, ok best thing to do i think would be 1st find out how much all the stuff you want linux to have access to takes up, if its only a couple gigs or less than just make you're xp partition big enough to hold all that, who knows you dont wanna cut yourself short on xp hd space anyways cuz it still used areas on C: for virtual memory anyway plus u may install something on it later, then just make the rest or your partitions like we talked about and move the stuff you want to your shared folder after install

---

### Post by loserboy on 2006-12-09
well ubuntu says to use a Max of 1 gig swap, since I have plenty of room I make a 1 gig swap, although ive never seen my swap get more than 50% usage, so...

Edit: scratch that i dunno if ive even seen 30%

---

### Post by loserboy on 2006-12-09
one more thing to add and i'll stop,  the cool thing about X/Ubuntu is that if you dont like your partitions the worst case scenario is that you can reinstall as many times as you like till you feel good, hehe there arent any codes or registrations to run out of  :)

---

### Post by farmer26 on 2006-12-09
ok, thanks for letting me know that I can reinstall and redo my partitions. I really need to make sure that I don't mess windows up as I share this pc with my brothers and they just play games on xp, which would be incompatible with linux.

Is it possible to make my xp partition only big enough to hold the actual xp o/s, and then install all other programs and store all other data on the shared partition? Would they still work ok if they weren't on the same partition as the xp o/s?

I want linux to have access to everything exept the partition which only contains the xp o/s, so the shared drive would be the largest.

This is how I want my partitions to go:
xp o/s ntfs 2gb??? ] shared + /home fat32 59.5gb ] Xubuntu o/s ext3 6gb ] swap 1gb

---

### Post by loserboy on 2006-12-09
you might be able to do it that way,but the thing is,  linux can read off an ntfs it just can't write to it so I always leave windows, program files, docs, etc alone because even if you can put those in a fat32 partition, when things are installed or are going to be run, they automatically check the factory installed places as far as i know, which isnt impossible to change but is sorta painstaking, so like i was saying just remember that you can read off of ntfs and make your choice from that.

also dont forget that u said other people are using windows and if you don't give them enough hd space then they won't be happy

---

### Post by farmer26 on 2006-12-10
that's a fair point. I will rethink how I'm going to do this (again), with it the way you suggested. It probably is best to leave all the windows programs and such on the ntfs drive. So it will mean that I will have about 20gb each for windows, /home, xubuntu root, leaving 1gb for swap. This is probably the best way. I looked in the xbuntu installer (without actually doing anything), and when it came to the manual partitioning it was asking me for file formats of the drives and flags. Should the swap be ext3? I know the /home and Xubuntu root partitions do. Also, the windows drive is already flagged as 'boot'. Should I flag the Xubuntu partition as 'boot' also? Would this allow me to choose which o/s on the boot screen? Do the Swap and /Home need to be flagged as anything?

Sorry for posting so many questions, but there are so many things I don't know about this and I don't want to get it wrong.

Thanks for helping out so far.

---

### Post by bulldog on 2006-12-10
Just jumped in to give a little feedback too :D 
Hard disk is about 70GB.

Windows as primary 20GB
Fat32 primary 10GB as a share for both OS's and if windows ran out of space,you can add space from this one to windows.
Than the rest of the free space make this an extended partition [about 40GB]

10GB for the / (root)  ext3 file format partition flagged to boot
1GB swap partition formatted as swap file format no flags
Rest of your space /home ext3 file format no flags

I think this is a safe way of partitioning,you can add space to windows from the FAT32 in case of trouble,and you can add space to / (root)
from your swap and your /home.
If your /home needs extra space,it's time for a larger disk I suppose :-)

---

### Post by farmer26 on 2006-12-10
Thanks Bulldog that's a really good system, I think I'll end up doing it like that. The only problem is that at the moment I have about 40gb used on my ntfs windows hard drive, and I will need to temporarily move everything that I wish to use in Xubuntu to a different disk on another pc, or use a removable hard drive, so that I can put it onto one of the ext3 drives after I have partitioned. I don't have a removable hard drive, but my dad has a laptop with 80gb of storage. Would it be possible to move the files onto his disk with a usb cable or something?

---

### Post by bulldog on 2006-12-10
It could be done with an USB cable I suppose [never tried though]but I should make a network between the two computers using a router or with a ethernet cable directly between them.

To make a direct connection between the computers,you need a crossed ethernet cable,not a straight one.

---

### Post by farmer26 on 2006-12-15
Ok. I don't have a crossed ethernet cable, but I should be able to get one. Do I need to use My Shared Folders?

---

### Post by Kazna on 2006-12-15
Just to add... in Windows, most installed applications are not runnable from another OS on a different partition as they are installed in the Win registry. So as you asked earlier if you were to move the programs from WinXP (NTFS) to a FAT32 partition, many of them will not run under WinXP anymore. Thats why Linux has separate software and its not the same as Win software. each software will have to be downloaded/installed separately on each these 2 OS's.

XP only needs a few folders such as the Windows/Documents&Settings folder to run with the system.ini, the boot.ini etc files. 

I'm having some problems.. but anyway. This is what I would do:

*Leave the free space unallocated
*Defrag it well before hand
*Do any chkdsk runs and run a HDD test utility beforehand
*Check your RAM with Memtest86 beforehand
*Run installation of CD (preferably from the Live/Desktop CD)
*Partition it during installation

XP NTFS 5Gb ] Shared + /home FAT32 56.5Gb ] Xubuntu ext3 6Gb ] Swap 1Gb

Partitioning actually will decrease your space a little so it'll probably come to 66-67Gb at the end.

For transferring files.. Slave another HDD onto your present Master HDD. Transfer everything over (copy or cut).

Hope it helps a little.

---

### Post by farmer26 on 2007-02-11
OK, I'm finally installing XUbuntu and I've worked out all the partitions and everything but I'm stuck on one part of the installation. It says GRUB will be installed to (hd0). I can change the (hd0) bit, but I have no idea what it means. I'm wondering what it should be set as.

---

### Post by bulldog on 2007-02-11
HD0 means the first hdd,the second should be hd1 and so on.
If you had sata drives it would be sda,sdb and so on.
Did take you a while didn't it?

If you still have one hdd it is save to put grub in there.

---

### Post by farmer26 on 2007-02-11
Yes it did lol. So which hd should I install GRUB to?

P.S Thanks for replying so fast!

---

### Post by bulldog on 2007-02-11
How many hdd's do you have?
I should install GRUB on the hdd which has ubuntu on it,in the case you have more than one physical hdd [not partitions].

---

### Post by farmer26 on 2007-02-11
I have 2 physicals. One has windows on it. The other was empty and I'm now dividing up for ubuntu. I've given it 3 logicals - a swap, a /, and a /home. Linux will be installed on the ext3 / drive which is a logical of the empty physical.

---

### Post by bulldog on 2007-02-11
If you have two hdd's it's important to know which drive is the master hdd were you boot from.
If this is the windows disk it is hd0 and you should install GRUB to hd1.
To see GRUB you have to make the slave [ubuntu] disk the master boot device otherwise it will boot directly into windows.

But if it's no matter to you,you can savely install GRUB to hd0 your windows hdd.
This is the easiest methode and will work without a glitch.
If you want we can always change this in the future it's no big deal anyway.
So install GRUB to hd0 and you can boot windows and ubuntu from your GRUB menu.

---

### Post by farmer26 on 2007-02-11
Ok I'm installing it to hd0 and it's installing XUbuntu! The only thing is that it wouldn't let me use my 30gb fat32 logical partition as /home, so I called it/media/sda6 as it suggested.

---

### Post by farmer26 on 2007-02-11
It's now all installed and it all works fine! The only thing is that I can't share files. It's probably got something to do with when it wouldn't let me call it /home.

---

### Post by farmer26 on 2007-02-14
OK, I now want to install normal ubuntu onto another pc, again for dual-booting and I have been defragging it lots. However, there are some 'unmovable' files. When I partition my disk, will these files be deleted? And will this affect windows?

---


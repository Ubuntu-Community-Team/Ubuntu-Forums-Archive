---
title: "Installing Ubuntu and Kubuntu over windows in a dual-boot"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by lewisskinner on 2007-11-24
Hi there everyone.  New poster on the forums, and I wondered if I could get some help.

Basically, I downloaded Ubuntu and Kubuntu vers 7.10 a few weeks ago, and have been trying out both using the live CD.  I have read that it is possible to install (say) Ubuntu, and then add Kubuntu over the top and use the KDE applications by a simple switch, and this is what I would like to do, since there are some KDE apps I like, and some GNOME ones I like.

I also need to use windows, as my girlfriend and I are both gamers, so I want a dual-boot set-up (I may at a later date try to run windowns in a VM within K/Ubuntu).

Now, my first problem.  All the documentation and walkthroughs about installation (in particular [this page](http://www.psychocats.net/ubuntu/installing) state that when the option of partitions comes up, I will get three options, but I do not seem to be given the option of changing the windows partition size (basically, I do not have the first option as shown in [this screencap](http://img379.imageshack.us/my.php?image=feistydual06rw5.png)).  So, can anyone guide me through using the advanced option, so I get the following set-up:

c;\ windows OS
d:\ Ubuntu/Kubuntu OS
e:\ shared memory
f:\ a /home partition (so I can do a clean reinstall when new K/Ubuntu vers come out)

and, of course, a swap partition and the Windows backup (if you feel it is still necessary).

I also have a lot of files and folder already on the windown partition, so I would like to move them to the new e:\ and re-size the partitions later (if possible!)

Please, I am a BRAND NEW user of Linux, and have been brought up on windows since 3.1, so please can someone provide a step-by-step guide, using words of fewer than 2 syllables! :)

I have a Dell Inspiron 531 with AMD live x2 processor 5000+ (2.6GHz), 2GB RAM (dual channel, 2x 1028MB, 667MHz DDR2) and a 500GB Serial ATA non-raid Harddrive.  I use the nVidia GeForce 8600GT and Soundblast X-Fi Xtreme

---

### Post by Sarteck on 2007-11-24
First of all, keep in mind that you can only have four *Primary* partitions.  Your setup there is fine, BUT you are forgetting the swap partition.  You may have to use extended partitions.

If I were you, I would first partition your 500GB hard drive into three sections: the section you will have Windows on, the section you will have for shared space, and your Linux section.  If you are using Windows Vista, it has a built-in partitioning tool you can use for this.  If not, there are various third-party partition tools that you can use (I used partitionMagic for my first Linux install, but I don't know if it's around anymore.)

Next, I would move anything you want in the shared partition to it from your Windows.  (Or copy, if you just want it as a backup.)

Then partition Linux how you want it. :)

---

### Post by candtalan on 2007-11-24
Get windows in a good state - defrag once or twice and scandisk.
Ensure you have backed up your (windows) data. Consider re-sizing the windows partition by using the facility within windows? or possibly use a live cd such as parted magic or gparted to re size, leaving a suitable size of un partitioned space on the drive. The ubuntu installer should offer as an option to install into the largest uncommitted space on the drive.

However, if you decide to use the Manual install option as you suggested, you should create your own partitions first I think. Say a 1GB for swap, a larger one, say 30GB for / then say 100GB for /home maybe 100GB for a shared partition (format this to fat32 or vfat). During the manual install, mark only the swap and system (   /  ) and the new  /home and the new shared partition to be formatted . Be sure that your windows stuff is NOT going to be formatted.
Note that linux drive and partition names are not the same as windows names!
Your hard drive will probably be sda (serial disk (device?) a) and the windows partition(s) may be sda1 and or sda2 assuming there is a recovery or help partition or something. linux will need a minimum of two partitions - you will be requiring four. You can only have four total of primary (old style) partitions, so you should initially create a large extended partition to house all of your new partitions inside. This will be easy using the parted magic or gparted live cd mentioned above.
Take it gently.

---

### Post by lewisskinner on 2007-11-25
Right, so I need to partition my drive within windows into three, a smaller main windows drive, the windows backup and a shared drive to use with K/Ubuntu, and leave a large part of the drive as an exteded partition, and then I can install Ubuntu into this using virtual partitions?

Again, very new to this, what is fat32/vfat, and what does sda2/ext3 etcetera mean?

---

### Post by louieb on 2007-11-25
> **lewisskinner said:**
> Again, very new to this, what is fat32/vfat, and what does sda2/ext3 etcetera mean?

lol: I can tell your a windows user.  Dual booting and Linux is going to be a brand new world. 1st off please backup your data and have what you need to restore you PC to the way it is now.  

Fat32, vfat, NTFS, ext2, ext3, JFS, reisnerfs. These are names given to file systems. The 1st 3 are MS inventions and primarily used by MS products. The rest are open source file systems. There are a bunch of them out there but **remember 2 NTFS - Windows and ext3 - Linux.** 
More info than you'll ever need here [http://en.wikipedia.org/wiki/File_system](http://en.wikipedia.org/wiki/File_system)

/dev/sda, /dev/sda1, c:, d:. The 1st is a name for a storage device such as a hard drive, CD drive, pen drive ... The rest are just names for partitions on a storage device. [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm") Theres no getting around it you really need to do some study and at least know that there are 3 types of partitions: primary, extended and logical.  

> step-by-step guide, using words of fewer than 2 syllables!       Sorry but the psychocats site about a good as it gets. Just wait till you look at man pages.

You have a nice system. Have you considered adding a 2nd drive to put Ubuntu on? Its much safer and if you decided Linux is not for you then theres some extra storage for you.   [Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by lewisskinner on 2007-11-25
Hah, Yea, as I said, brought up since windows 3.1, although prior to that I did once an Atari and an Amega.

You're saying that linux can't access some windows partitions, so (I assume) I need to format the shared as vfat so both can access it?  Is this assumption correct?

The prob with the psychocats site is this section (about halfway down):
[quote=psychocats]You'll then be presented with three options. This first option is ideal for users who want to set up a dual-boot (where you can choose whether you want to use Windows or Ubuntu each time you boot up your computer) but know very little about setting one up. Ubuntu will guide you through shrinking your Windows partition and creating a new Ubuntu partition out of the free space.
[http://img379.imageshack.us/my.php?image=feistydual06rw5.png](http://img379.imageshack.us/my.php?image=feistydual06rw5.png)[/quote]
I only seem to have the last two of these options (no option for resizing IDE1 master and resizing free space).  I'm worried the first will wipe windows, and I'm scared I'll wipe it if I choose advanced!

Is it best to repartition in windows, allow (say) 50GB for windows, 10GB for windows backup (as it is currently) and a 300GB shared drive (all as primaries), leaving the remaining 140GB unpartitioned, so Linux can install itself there with a 5GB swap partition and a 10GB /home partition as extended partitions?

And yes, I have thought of buying a 160GB or even 250GB HD, but I basically spent as much as I could afford getting the best spec I could, so there's not a lot of spare cash floating about in the bank :(

---

### Post by louieb on 2007-11-25
Ok you want the good news or bad new first. Ok the bad news 1st.
You have the most [COLOR=Red]dangerous [/COLOR]part of setting up a dual boot system ahead of you. In fact the 1st thing you need to do[COLOR=Red] shrink[/COLOR] your Windows partition and leave some unallocated space on the drive for Linux. Just do a proper prep job before you begin. (clean up temp files,  defrag ...)  

I've heard VISTA has a tool to shrink itself and if that is what you have the use it.
If you have XP the use GParted on the Live CD. In fact if you have internet with the LiveCD please post a screen shot of GParted. System>Administration>Partition Editor.  Press Alt+PrintScreen. Just don't want any surprises.

The good news is once you have space for Linux and Windows still works then if something should go wrong 99% of the time Windows can be fixed with the [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/")  or your Windows install CD.

BTW: I go back to DOS and Win 3.1. Sure is a lot nicer now. 
> You're saying that linux can't access some windows partitions, so (I assume) I need to format the shared as vfat so both can access it? Is this assumption correct?
Not a problem: remember NTFS for windows and ext3 for Linux. Go with that and Linux can read/write Windows and Windows can read/write the Linux ext3 file system. (your choice ntfs, ext3 or fat32. I've used all three.) The only limit is Windows has to be installed on NTFS or fat32. Linux has to be install on a Linux file system (ie. ext3)     

Get that Screen Shot and I get back with some partition ideas for you.

---

### Post by lewisskinner on 2007-11-25
Thanks for the help Louieb.  I have Vista, so I'll have a try with the in-built partition resizer.

As for file systems, do any have an advantage in terms of size/speed over the others?

---

### Post by candtalan on 2007-11-25
> **lewisskinner said:**
> 
As for file systems, do any have an advantage in terms of size/speed over the others?
ext3 is a journalling system (as is NTFS I think?) so it can have a good chance of recovering from file system damage. It is a little slower than ext2 though which is not journalled. Reiser is a bit on hold now since the author is in court on serious charges. On a modern machine you will not see a difference in speed.

Initially concentrate on getting a trusted backup of your windows stuff, just in case.
Clean up windows as suggested.
Maybe explore by using gparted or parted magic live CDs - but initially make no changes, just look.
Then consider resizing using vista. And you are on your way to freedom.  :-)

>  Is it best to repartition in windows, allow (say) 50GB for windows, 10GB for windows backup (as it is currently) and a 300GB shared drive (all as primaries), leaving the remaining 140GB unpartitioned, so Linux can install itself there with a 5GB swap partition and a 10GB /home partition as extended partitions? 
This will allow ubuntu to instal into the unallocated, unused space on th edrive. It would create its extended partiton containing a swap and a system partiton. If you wanted a separate /home partition and a shared fat32 partiton at this stage, things get a little more complicated.

---

### Post by louieb on 2007-11-25
Don't think you'll see any advantage of one file system over the other. I don't use fat16  (the one you used when you had dos and Win 3.1) or fat32 (used by Win95 and 98).  Just depends on what operating you think you'll use the most. 

By way of example here is how my P4 dual core 3.1gHz is partitioned. 

[LIST=1]
[*]XP is installed here in hindsight probably  should have given it about  30-35 GB.
[*]xpdata is a data partition anything I want both Ubuntu and XP to have access to. This partition is also shared of my home network it is formatted NTFS. In hindsight should have made it larger using space from the xp partition.
[*]Ubuntu install formatted ext3 just about the right size since don't store data here. Just the operating  system and configuration file.
[*]data actually have Puppy Linux installed on this 1 GB partition.
[*]swap partition.[/LIST]

---

### Post by lewisskinner on 2007-11-25
> **candtalan said:**
> This will allow ubuntu to instal into the unallocated, unused space on th edrive. It would create its extended partiton containing a swap and a system partiton. If you wanted a separate /home partition and a shared fat32 partiton at this stage, things get a little more complicated.

More complicated how?  Do I need to create the shared partition before or after I install Ubuntu?  I would hope before, as I would want to create a new partition, move some data to it and then resize before installing Ubuntu.  Also, what about the /home drive?  This sorts personal settings for Ubuntu right?  Do I need to tell the installer to do anything different?

One last thing.  If Vista and Ubuntu data were both stored on a single partition, how would windows (installed on C:\) recognise e:\lewis\documents as being my own?  And is there a way of sharing the folders between my two user areas on both of the OS', but keeping my porn hidden away from the eyes of my girlfriend? ;)

Also, just noticed this:
[IMG]http://i4.photobucket.com/albums/y122/darkeyes_lewj/systemspec.jpg[/IMG]

Does this mean I should use the 64-bit OS?

---

### Post by lewisskinner on 2007-11-25
OK, part 2.  Here's the Vista partition manager:
[IMG]http://i4.photobucket.com/albums/y122/darkeyes_lewj/partitionsettings.jpg[/IMG]

Why will it only let me shrink down to 400GB?  I want no more than 20/25GB really!

Any anyone know what the 55MB portion is at the start?

---

### Post by louieb on 2007-11-26
> **lewisskinner said:**
> ..Do I need to create the shared partition before or after I install Ubuntu? ... but keeping my porn hidden away from the eyes of my girlfriend? ...  Does this mean I should use the 64-bit OS?
Once you get unallocated space : use GParted to create your partitions all at once before you start the install.

:twisted:Nothing is safe: Linux doesn't give a rat about windows ownership  or  permissions. (any file in a windows partition can be seen from Linux). The same can be said about Windows it doesn't care about Linux security.

32 or 64: your choice. I use the 32bit on my Dual Core.

---

### Post by lewisskinner on 2007-11-26
> **louieb said:**
> :twisted:Nothing is safe: Linux doesn't give a rat about windows ownership  or  permissions. (any file in a windows partition can be seen from Linux). The same can be said about Windows it doesn't care about Linux security.

Fine, I'll use an external HD :)

> **louieb said:**
> 
32 or 64: your choice. I use the 32bit on my Dual Core.

Is there any more speed/functionality in 64 bit?  I actually didn't realise I had a 64 bit processor, so I'm quite surprised (and pleased!)

---

### Post by maybeway36 on 2007-11-26
If you can shrink C: enough, make an extended partition for all your Linux stuff. Linux can boot off an extended partition.

---

### Post by lewisskinner on 2007-11-26
so primaries for windows and the windows backup (I may in fact stick the windows backup onto a DVD and do away with it totally) and then linux OS, swap, shared data and /home all on an extended partition.  Can Windows read & write to a shared drive on an extended partition?

Also, how do I actually go about setting up the /home partition?  Is there an option in the linux installer?

---

### Post by candtalan on 2007-11-27
> **lewisskinner said:**
> so primaries for windows and the windows backup (I may in fact stick the windows backup onto a DVD and do away with it totally) and then linux OS, swap, shared data and /home all on an extended partition

the extended partition area will need to house all the remaining partitions, no problem, they behave like primaries in all respects. Have you had a look at gparted live cd  or parted magic live cd yet? they are very intuitive, and you can initially just look.
> 
.  Can Windows read & write to a shared drive on an extended partition?
yes. traditionally it will have to be fat32, but you can get windows apps now to write to linux file systems.
> 
Also, how do I actually go about setting up the /home partition?  Is there an option in the linux installer?
Only if you decide to use the 'Manual' install. If you do this without local help or friend etc then consider going slowly and having facility to ask detailed questions here as you go along. And anyway - have a backup of your windows data which is in a location which is not going to be at any risk in your machine under change (DVDs or cds?, external hard drive etc etc ) Any partitioning has a potential small risk of big problems.

---

### Post by louieb on 2007-11-27
> **lewisskinner said:**
> Can Windows read & write to a shared drive on an extended partition?
Window can read/ write to an extended partition.
> **lewisskinner said:**
> Also, how do I actually go about setting up the /home partition?  Is there an option in the linux installer?
If you want more that the basic / (root) and  swap partitions you have to use the manual partitioning option. (ie.. a separate home and/or data partition ).

---

### Post by lewisskinner on 2007-11-27
Yeah, I can shrink the Windows OS and backup partions now, Should I also add new partitions (in Gparted), or leave unpartitioned space and do it in the Ubuntu installer?

---

### Post by candtalan on 2007-11-28
> **lewisskinner said:**
> Yeah, I can shrink the Windows OS and backup partitions now, Should I also add new partitions (in Gparter), or leave unpartitioned space and do it in the Ubuntu installer? (Gparted?) I believe leaving unpartitioned space will be the easiest as long as you are happy to accept the default install conditions - if you want a separate /home partition then you will go for a manual install and then it is easiest to have partitions all prepared in advance

---

### Post by lewisskinner on 2007-11-28
> **candtalan said:**
> (Gparted?) I believe leaving unpartitioned space will be the easiest as long as you are happy to accept the default install conditions - if you want a separate /home partition then you will go for a manual install and then it is easiest to have partitions all prepared in advance

Great.  Roughly how much do you recommend for /home. Ubuntu, Shared Ubuntu/Windows memory etc?

---

### Post by candtalan on 2007-11-28
> **lewisskinner said:**
> Great.  Roughly how much do you recommend for /home. Ubuntu, Shared Ubuntu/Windows memory etc?
home will be your main data partition, so make it fairly big - 100gb at least,out of your 500gb?. Shared ubuntu/windows - depends on whether you use it heavily as a main data store or just as a transitory store (50 gb  -depends?) Windows, say 100 gb(?). Swap 2gb or 1gb, Ubuntu system (root /) 30gb (minimum 6gb, say). I know it does not add up to 500 but you get the general idea if it was me doing it?

It is fairly easy to change sizes of partitions later (with care), but it is a bit more effort to resize -and- create new partitions later, but it still can be done with care.

---

### Post by lewisskinner on 2007-11-28
Thanks for all your help, but Gparted initially failed on three occasions, before eventually looking as though it had worked, but with Ubuntu then currupting my Windows installation.

I appreciate all the help I've had, but I think I'd better stick with Windows if it's going to be this difficult to switch.

Bubye lads

lewis

---


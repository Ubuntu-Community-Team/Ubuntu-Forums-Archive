---
title: "Separate HD? Partition C drive? Format?"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by tripbeetle on 2006-04-07
I am keen to try Ubuntu. I have 5 HDDs in my system, one of which I want to devote to Ubuntu. 
I have a couple of questions:

1. Is devoting a whole HD to Ubuntu a good idea? Partitioning my C drive (which presently has Windows XP Pro on it) appeals more because I assume when it starts up I'll have a choice of whether to launch Windows or Ubuntu, whereas if I devote a whole non-C-drive HD to Ubuntu I will inevitably have to boot up Windows first and then switch to Ubuntu - won't I?

2. I bought Partition Manager 7.0 which can format in FAT12/FAT16, FAT32, NTFS, Ext2, Ext3, ReiserFS, Linux Swap v.2, and HPFS. I read that ext2 is the HD format used most for Linux. Is that right?

Any help appreciated. :p

---

### Post by trent dillman on 2006-04-07
OK, first off, you can use a separate drive. You'll probably have to overwrite the Master Boot Record of the first drive to dual boot, but no biggie there.

Second, ext2 sucks. It's old (like FAT). Use ext3 or Resier.

---

### Post by ncappel1 on 2006-04-07
1) When installing, just make sure that windows XP pro is on the "Master" drive, and not the "Slave." Installing ubuntu on the separate drive is the easiest thing to do. The installation will ask if you would like Grub to be installed to your boot loader, choose "yes." 

When the computer starts, you will get to a screen where you can choose which operating system to boot into. It will not be necessary to boot into XP first, then go into Linux. (is that even possible?)

2) You will not need to use Partition Magic to partition the drive first, the Ubuntu install disk will do everything for you! It couldn't be easier. When the partitioning screen pops up during install, simply choose to completely erase and overwrite the drive of your choice, but remember: make sure that windows XP stays on the MASTER drive, if not you will not be able to load it anymore (unless you do some serious command line magic). 

Let us know how it works out!

---

### Post by catlett on 2006-04-07
Dual booting is done with Grub(grand unified bootloader). This program will be setup at the end of install. Grub is very stable. You don't have to worry about never accessing your drives again.
You have two choices when you install. You can take the choice of erasing ide slave hdb and using the entire disk for install. Or you can shrink the existing windows partition. The first is using your sedcond hard drive. I wrote it like that because that is how it will(kind of( look when you install. Linux doesn't use C and D. It uses dev/hda, hdb. device hard drive a, device hard drive b.
Whichever one you install you don't need a seperate program to partition. The install disk will handle all of that.
Just run the default install at the prompt i.e. press enter. Choose erase second drive or shrink 1st drive. Then let the install do the rest. At the end you will see Grub being configured. Just hit enter to all prompts. It will confirm the windows install and ask for a final approval.
The installation process and grub work very well. You shouldn't have any problems. Good luck.

---

### Post by da5id on 2006-04-08
Tripbeetle,

There's much misinformation floating around these forums.  I believe much of the misinformation arises because the Linux experts have forgotten much of what they knew about Windows and what they still remember is outdated.

Before you go any further, describe your set-up in more detail.  Particularly, as to each drive state whether it is PATA or SATA, partitioned, external (the connector type, i.e., USB, FireWire, ethernet) and which, if any, contain backup information.

Let me quickly address the misinformation that has been posted in this thread already.

"OK, first off, you can use a separate drive. You'll probably have to overwrite the Master Boot Record of the first drive to dual boot, but no biggie there.

Second, ext2 sucks. It's old (like FAT). Use ext3 or Resier."

This is irrelevant, confusing, and distracting information.  Ubuntu uses  the ext3 filesystem and will partition and format your hard drive it accordingly.  You do not need to make any choices.  If you have an academic interest, then examine the relevant entries in Wikipedia -- it provides plenty of information for your purposes.

If you have a standard Windows install, you already have a boot manager of a sort (see your boot.ini file in msconfig) -- it allows you to boot into regular Windows, Windows (safe mode), Windows (safe mode) with and without network support, etc.  I have read that Ubuntu changes the Master boot record when it installs its own boot manager.  After that you will get approximately 6 choices of Ubuntu (in the AMD 64-bit version) and Windows.  You will lose all your Windows subcategories.  It makes a change to the MBR to enable this dual-boot loader.  If everything goes right, it will not make any other changes that you will notice.  (I am not saying that I am technically savvy enough to tell you whether it makes other changes in the MBR because of the two Linux partitions it adds.)  Basically, in a default installation, it makes *about *an 8.5 GB main partition and a 400 MB swap drive partition YMMV.  You can see these graphically in Windows after the installation in Start/All Programs/Administrative Tools/Computer Management/Disk Management.  This Windows tool is very important to see what has happened before and after your Linux installation.  Take a good look both before and after each install attempt, if you do more than one.  Some screenshots would be nice.  It is very similar to Partition Manager or Partition Magic.  If you want to see a botched Ubuntu installation, see my Partition Magic screenshots in my dual-boot thread.  (Search theforum for :'dual-boot" and "Raptor" -- look for my screen name to see the carnage.)

If you are using SATA drives instead of IDE drives, this master/slave stuff is completely irrelevant.  The topography of SATA drives results that they are all primary and, as you may see if I am able to attach a screenshot to this post, Ubuntu can install in two partitions of an aggregate size of approximately 10 GB in the middle of a non-C: drive, in Ubuntu-speak, "hdb."  Catlett's post with the implication that if Ubuntu installs on a "D" (hdb) drive, it must utilize the entire drive may be true for IDE drives, but it is most certainly not true for SATA drives as my own installation demonstrates.  My PC has no IDE drives so I can't say much more about this.  (But I actually agree about just hitting the "Enter" key until finished.)  So, defragment all of your hard drives first.  (Simply unplug any external drives you not want to Ubuntu to install upon.)

As near as I can tell, Ubuntu begins with your C: drive and "names" each one serially as hda, hdb, hdc, etc. counting from the lowest letter to the highest and assigning a separate "hd*x*" name to each logical partition and installs a second primary partition on the first physical drive where it finds a partition with 10 GB of contiguous "FREE SPACE."  So, defragment all of your hard drives first.  (Simply unplug any external drives you not want to Ubuntu to install upon.)  You will see this reference ("FREE SPACE") in your Ubuntu install.  It will identify the maximum contiguous "empty" space such as, for example, 80 GB, and giving the impression that is going to wipe (destroy) any data contained in that space.  If you do a default installation it will do no such thing, but rather, it will merely install the two approximate/aggregate 10 GB partitions I mentioned before.

Finally, my real question to you.  You say you are keen to "try" Ubuntu.  The default 10 GB installation is the safest and least likely to result in the destruction of Windows data.  As near as I can tell, it is rather difficult to "make" Ubuntu install on any particular partition or even physical drive.  That is where the real risk comes in not utilizing the default installation. This is your best bet.  Then when you graduate from from an "Absolute Beginner" Ubuntu User you can reinstall Ubuntu exactly the way you want to with your newfound expertise.

This assumes that your brand-new installation of Ubuntu uninstalls in a well-behaved fashion.  I have actually no factual information either way on that issue.  I was only able to install Ubuntu  using the default method.  I burned a bunch of DVDs to my C: drive (filling it up -- crude but effective) because I did not want Ubuntu installing there -- that worked, it installed on my D: just as I wanted.  It boots just fine from the Grub boot loader and, other than the 9 MB orphan unallocated space on my C: drive and my rather useless 2 GB partitions on my D: that I made with Partition Magic (that's the short story -- see prior to read for the long one), Ubuntu works fine and I'm having a lot of fun with that.  I'm sure you will too.  Best of luck.  With the smallest amount of perseverance it is impossible that you will not successfully install Ubuntu -- somewhere.  :-)

Regards, Gene -- Ubuntu Absolute Beginner
PS:  I'll post those screenshots tomorrow if no one is so offended by the temerity of this post they delete it.  You will find a little bit of "If it's a Windows problem it's the software; if an Ubuntu problem it is the user."  Not too bad, though. Enjoy!

I was in a hurry otherwise this would have been shorter.

---

### Post by aysiu on 2006-04-08
If you're keen to "try" Ubuntu, try a live CD.

The live CD leaves your hard drive untouched and operates off the CD itself and your computer's RAM.

I would highly recommend using the live CD for about a week or two until you're really comfortable with the interface and the command line.

Once you feel confident enough for a dual-boot, follow this guide and just ignore all the stuff about resizing partitions:

[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by ncappel1 on 2006-04-08
I always forget about the live cd, good idea!

---

### Post by tripbeetle on 2006-04-08
Thank you very much guys for the prompt and comprehensive replies - and an especially big thank you to Gene for particularly clear and detailed coverage.

I see that there are lots of things I have to address. Of my five HDDs, I am only using three at the moment. The C drive is stand alone, the other four are in master-slave pairings. Forgive my ignorance, but I'm not sure whether they're PATA or SATA, and reading the literature that came with them hasn't enlightened me on that so far. IDE sounds right, though. They are all internal disks linked to the motherboard with the wide thin ribbon-like, multi-pin connectors.

I'm pleased that the partitioning issue is going to take care of itself. (Not so pleased that I wasted money on Partition Manager, but that's the story of my life!) However, it sounds as if there are plenty of other pitfalls to make up for it. I look forward to viewing your screenshots, Gene, for reference.

I'll be able to reply more concretely once I've sat down and started on getting Ubuntu onto my PC. Will let u know what happens, and maybe pick brain some more later.
Ciao.

---


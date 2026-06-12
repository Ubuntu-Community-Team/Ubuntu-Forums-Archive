---
title: "Thinking of installing Ubuntu on a secondary partition in my Dimension 4600"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by johnd29 on 2007-06-17
I'm about to format my 80GB HDD, and thinking of leaving about 15GB free to install Ubuntu in a partition. Is this a good idea? Any precautions or steps I need to take?

It won't cause any instability in my system or anything, right'

---

### Post by starcraft.man on 2007-06-17
> **johnd29 said:**
> I'm about to format my 80GB HDD, and thinking of leaving about 15GB free to install Ubuntu in a partition. Is this a good idea? [COLOR="Blue"]Sounds Fine, Ubuntu only really needs 6-8 GB for root and 1 GB for swap (if you have 3 or 4 GB of RAM decrease swap to 256 or less).[/COLOR]

Any precautions or steps I need to take? [COLOR="Blue"]Nope, long as you know what your doing with partitions and backed up your data.[/COLOR]

It won't cause any instability in my system or anything, right? [COLOR="Blue"]Dual booting installs 2 separate OSes you can't affect one from the other, long as you make sure your windows partition is fine there aren't any issues to be concerned with.[/COLOR]

Hope that answers questions.[ Heres a guide to Live CD install]("http://www.psychocats.net/ubuntu/installing"), I assume you'll be using that.

Off I go, anymore questions don't be shy :).

---

### Post by johnd29 on 2007-06-17
I'm actually gonna format my drive tomorrow anyway, so tell me if this is right:

While re-installing Windows, I choose to install it in a 65GB partition (leaving 15GB of unpartitioned space for Linux). Then after installing WindowsXP, I can go with the installation of Linux in that 15GB right?

This way I don't have to shrink a partition, there's just that 15GB open for it (is 15GB enough btw?).

---

### Post by acowboydave on 2007-06-17
Definitely, backup your data. The live cd will partition the hard drive for you or you can do it manually. You will like ubuntu. Read the forums first and the advice that is out there first.

---

### Post by Sonofmoog on 2007-06-17
> **johnd29 said:**
> It won't cause any instability in my system or anything, right'

There is *always* that chance.  If your XP Filesystem is NTFS, make sure that ntfs-3g is installed and working properly before trying to access your XP files from within Ubuntu.  

I'd also suggest you make a second logical partition and mount /home on it.  

You can also download Ext2IFS_1_10c.exe and access your Linux files from within Windows.  Google for it.  

HTH

---

### Post by starcraft.man on 2007-06-17
> **johnd29 said:**
> I'm actually gonna format my drive tomorrow anyway, so tell me if this is right:

While re-installing Windows, I choose to install it in a 65GB partition (leaving 15GB of unpartitioned space for Linux). Then after installing WindowsXP, I can go with the installation of Linux in that 15GB right?[COLOR="Blue"] Sounds fine to me, if you really want Windows to have 65 GB... IMO, a very good way to do it is to make a smaller partition just for the Windows Core files and applications like firewall and AV. Make it 15 GB as well, thats enough for XP. Then make a second partition in the Windows install and make it 50 GB and formatted with Fat32. This way, you can use it as swap and data storage (and game installation or any other Windows large applications like Adobe Suite) between the drives. This also makes it easier to increase the size of the Ubuntu partition or a home folder at a later date if you really like Ubuntu, or the converse and add Ubuntu's space to the data partition. You will have to remember to format the partition when you get in Windows XP and apply updates, that is simple though. Then of course you will have 15 GB left for Ubuntu install. I would divvy that up as the following: 7 GB Root system (/), 7 GB home, and 1 GB RAM (unless of course you have a lot like I mentioned, then less).

To summarize, I'll just list it here.
Windows XP - 15 GB - NTFS - Primary Partition 
Data storage - 50 GB - Fat32 - Extended partition (not sure if windows partitioner makes extended...)
Root Partition - 7 GB - Ext3 - Primary Partition
Home Partition - 7 GB - Ext3 - Same Extended Partition
Swap File - 1 GB (if less, add to home) - Swap - Same extended partition[/COLOR]

This way I don't have to shrink a partition, there's just that 15GB open for it (is 15GB enough btw?). [COLOR="Blue"]Yup, its enough. Ubuntu really only needs 6 GB for a base install (5 and 1 GB swap) its a smaller install than Windows and all its applications.[/COLOR]

My answer in blue again, this is starting to be a lil habit and blue is such a nice color :D.

The partition scheme I proposed is a bit advanced, but its preferable for the long run... redoing partitions and or reinstalling is a pain once you got it all nicely set up, I'm just trying to look out for ya... I've partitioned/reinstalled enough to know.

Oh and there is only one downside to my scheme, the 50 GB data partition will have a ceiling file limit of 4 GB of course, I assume you don't handle files that large often. The 7 GB home partition can surpass that limit though for any intermediate needs (as well as of course the NTFS partitions).

---

### Post by johnd29 on 2007-06-17
> **Sonofmoog said:**
> There is *always* that chance.  If your XP Filesystem is NTFS, make sure that ntfs-3g is installed and working properly before trying to access your XP files from within Ubuntu.  

**I'd also suggest you make a second logical partition and mount /home on it.  **

You can also download Ext2IFS_1_10c.exe and access your Linux files from within Windows.  Google for it.  

HTH

What exactly is ntfs-3g? How do I know if I have it?.

And what does the bolded part mean?

---

### Post by johnd29 on 2007-06-17
> **starcraft.man said:**
> My answer in blue again, this is starting to be a lil habit and blue is such a nice color :D.

The partition scheme I proposed is a bit advanced, but its preferable for the long run... redoing partitions and or reinstalling is a pain once you got it all nicely set up, I'm just trying to look out for ya... I've partitioned/reinstalled enough to know.

Oh and there is only one downside to my scheme, the 50 GB data partition will have a ceiling file limit of 4 GB of course, I assume you don't handle files that large often. The 7 GB home partition can surpass that limit though for any intermediate needs (as well as of course the NTFS partitions).

*I would divvy that up as the following: 7 GB Root system (/), 7 GB home, and 1 GB RAM (unless of course you have a lot like I mentioned, then less*

Sorry for my ignorance, but what's the Root system and home? I was under the impression Ubuntu installed just one thing, heh :)...and the 1GB RAM? Is that memory or 1GB from the HDD?

---

### Post by starcraft.man on 2007-06-17
> **johnd29 said:**
> What exactly is ntfs-3g? [COLOR="Blue"]ntfs-3g are drivers to read and write to NTFS partitions. By default, Ubuntu only allows reading from NTFS partitions. That is why I recommended the fat32 partition, less hassle. [More info on it.]("http://www.ntfs-3g.org/") Don't install it from there, its in our repos. Oh and there is even more info on the forums, just search "ntfs-3g".
[/COLOR]
How do I know if I have it?[COLOR="Blue"].You don't unless you installed it in Ubuntu. Windows obviously doesn't need it, it writes to NTFS natively.
[/COLOR]
And what does the bolded part mean?[COLOR="Blue"][Explanation on partitions. ]("http://en.wikipedia.org/wiki/Disk_partitioning")
[/COLOR]

Blue is the word.

---

### Post by starcraft.man on 2007-06-17
> **johnd29 said:**
> *I would divvy that up as the following: 7 GB Root system (/), 7 GB home, and 1 GB RAM (unless of course you have a lot like I mentioned, then less*

Sorry for my ignorance, but what's the Root system and home? I was under the impression Ubuntu installed just one thing, heh :)...and the 1GB RAM? Is that memory or 1GB from the HDD?

[About partitions.]("http://www.psychocats.net/ubuntu/partitioning")

Sorry, I'm not trying to complicate it but it does help in the long run to put a bit more effort in, in the beginning. Like anything else you do in life, more effort = more rewards.

Oh and about the 1 GB. Yes, swap file is scratch surface on your HDD. Its like paging file in windows, except thats done for you automatically. If you have 3 or more GB, 256 swap is more than enough or less. If you have 2 or less, I recommend a nice cushion of a GB of swap.

---

### Post by johnd29 on 2007-06-17
> **starcraft.man said:**
> [About partitions.]("http://www.psychocats.net/ubuntu/partitioning")

Sorry, I'm not trying to complicate it but it does help in the long run to put a bit more effort in, in the beginning. Like anything else you do in life, more effort = more rewards.

Oh and about the 1 GB. Yes, swap file is scratch surface on your HDD. Its like paging file in windows, except thats done for you automatically. If you have 3 or more GB, 256 swap is more than enough or less. If you have 2 or less, I recommend a nice cushion of a GB of swap.

Ok, I think I'm getting it. I don't know about the FAT partition though, since I do handle large video files. (Over 10GB sometimes). But this has been helpful, a lot! And since it's my first time with Ubuntu, I think the 7GB home and 7GB root thing will work fine. Is that specified during installation? The how much for each one (including swap).?

---

### Post by starcraft.man on 2007-06-17
> **johnd29 said:**
> Ok, I think I'm getting it. I don't know about the FAT partition though, since I do handle large video files. (Over 10GB sometimes).[COLOR="Blue"] Ok, in that case make the FAT32 partition an NTFS one, the ntfs-3g drivers work really well in Ubuntu, and I can't really recommend to commit ya to Ext3 unless your sticking with Ubuntu full time like me.[/COLOR]

But this has been helpful, a lot! And since it's my first time with Ubuntu, I think the 7GB home and 7GB root thing will work fine. Is that specified during installation? [COLOR="Blue"]Yes, after reading the documentation I provided make sure you select manual partition and you can easily make all 3 for Ubuntu, it is very straight forward once you know what to do.
[/COLOR]
 The how much for each one (including swap).?[COLOR="Blue"]There is only one swap (like one paging file in Windows) used for the entire OS. I don't recommend it too large because of the 4 GB ceiling on 32 bit systems. So you only need to make 1 swap file for the entire OS if you have A) more than 3 GB make it less than 256 or B) if you have less than 2 make it 1 GB of swap.[/COLOR]

I think that's about it. Glad to be of help. I know it's a bit more than you actually need to do to get Ubuntu installed, but extra effort beforehand pays off in the long run.

---

### Post by johnd29 on 2007-06-17
> **starcraft.man said:**
> I think that's about it. Glad to be of help. I know it's a bit more than you actually need to do to get Ubuntu installed, but extra effort beforehand pays off in the long run.

*"There is only one swap (like one paging file in Windows) used for the entire OS. I don't recommend it too large because of the 4 GB ceiling on 32 bit systems. So you only need to make 1 swap file for the entire OS if you have A) more than 3 GB make it less than 256 or B) if you have less than 2 make it 1 GB of swap."*

I have 2GB RAM, do I make that 1GB still? And how does it work, exactly? Like you mentioned, the paging file, taking 1GB of space so it can work like virtual memory?

I'm excited for this. I really liked Ubuntu, and all the modifications you can do to it (I saw one modded to look like a Mac, that was funny :lol:).

---

### Post by starcraft.man on 2007-06-17
> **johnd29 said:**
> 

I have 2GB RAM, do I make that 1GB still? And how does it work, exactly? Like you mentioned, the paging file, taking 1GB of space so it can work like virtual memory?[COLOR="Blue"] Yes, ideally we would tell you to make no swap and only use RAM, it after all reads and writes much faster than your HDD. Life is not ideal though and some things actually require swap file on your drive (hibernation function is one). Hibernation requires swap because RAM is powered and hibernation is not, thus it can't store data on unpowered RAM. Mostly though the swap is an insurance policy, if you ever run out of RAM or processes start sucking it up, it can spill over into Swap and slow down a bit but certainly not as much as the OS would slow if it had no RAM/Swap left, that would make you cry at how slow it gets.

As for how to make swap, its just a partition like any other... the file system type is just swap instead of ext3 and it mounts just to plain swap by Ubuntu, its in the desktop install guide you'll see :).[/COLOR]



> I'm excited for this. I really liked Ubuntu, and all the modifications you can do to it (I saw one modded to look like a Mac, that was funny :lol:).

Yes, I can definitely say if control of your OS is what you want Ubuntu is for you. There is very little you can't do to it. Just be patient and follow things along slowly. If you have any problems during the live install you can always hop onto the internet (advantage of being live) and come ask here.

---

### Post by acowboydave on 2007-06-17
Hello, check out this site  [http://www.irongeek.com/i.php?page=videos/sosho-server-1-installing-ubuntu](http://www.irongeek.com/i.php?page=videos/sosho-server-1-installing-ubuntu)  Look at the video on installing ubuntu using your live cd. It will give at least a different view on installing ubuntu, you won't be sorry.

---

### Post by johnd29 on 2007-06-17
> **acowboydave said:**
> Hello, check out this site  [http://www.irongeek.com/i.php?page=videos/sosho-server-1-installing-ubuntu](http://www.irongeek.com/i.php?page=videos/sosho-server-1-installing-ubuntu)  Look at the video on installing ubuntu using your live cd. It will give at least a different view on installing ubuntu, you won't be sorry.

"We recently moved around some pages, please go to the main site and look for the page you requested.

Also, check the front page to see if there's any news about server problems."

---

### Post by starcraft.man on 2007-06-17
> **johnd29 said:**
> "We recently moved around some pages, please go to the main site and look for the page you requested.

Also, check the front page to see if there's any news about server problems."

Oh well, guess the screencast moved. Don't worry, I'm sure with all the text I pointed you to ya know what your doing. If theres any questions the forums are just an url away :).

---

### Post by acowboydave on 2007-06-17
Don't know what happened there, hit" hacking videos" on irongeek page, then click on installing ubuntu soho, it was helpful to me.

---

### Post by johnd29 on 2007-06-17
> **acowboydave said:**
> Don't know what happened there, hit" hacking videos" on irongeek page, then click on installing ubuntu soho, it was helpful to me.

awesome, worked now!!

---

### Post by acowboydave on 2007-06-17
good luck and enjoy a whole new world

---

### Post by johnd29 on 2007-06-17
I wasn't clear on where the GRUB has to be installed,thought. I said something like "HDD [0]", but he was using part of the Windows space, so I dunno if in my case it goes there too?

---

### Post by acowboydave on 2007-06-17
On my install during the installation it will ask you where.

---

### Post by johnd29 on 2007-06-17
Yeah but where should I install it?

---

### Post by starcraft.man on 2007-06-17
> **johnd29 said:**
> Yeah but where should I install it?

The default location is usually best, it will be to the MBR. Then you can choose to boot into either Ubuntu or XP at startup. If you install to partition you won't be able to use the boot loader. Just stick with the default which is MBR since your installing to same drive a dual boot.

---

### Post by johnd29 on 2007-06-18
I'm having a problem with the partition part.

This is what I have, and I don't know how to resize my ntfs partition to get some free space:

[http://img379.imageshack.us/img379/757/screenshothk8.png](http://img379.imageshack.us/img379/757/screenshothk8.png)

---

### Post by johnd29 on 2007-06-18
Can't figure it out.

---

### Post by acowboydave on 2007-06-19
Whoa, check out this site,[http://www.hevnikov.com/blog/2006/11/13](http://www.hevnikov.com/blog/2006/11/13)  before you start you also may want to check out Wubi 7.04 you will also need to download Ubuntu feisty alternate and put both Wubi and Ubuntu in the same folder. You wont have to partition your hard drive and my install went very well. Wubi's site is [http://www.cutlersoftware.com/ubuntusetup](http://www.cutlersoftware.com/ubuntusetup)   messed up on the hevnikov site google dual boot configuration images and the site and photo is on page 8

---


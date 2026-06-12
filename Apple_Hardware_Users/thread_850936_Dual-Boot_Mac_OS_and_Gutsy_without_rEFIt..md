---
title: "Dual-Boot Mac OS and Gutsy without rEFIt."
date: 2008-07-06
forum: Apple Hardware Users
---

### Post by rollerbladerdave on 2008-07-06
How could I best go about doing this on a Santa Rosa MBP? I'm looking to utilize the Boot Camp menu for my OS's, I don't like the look of rEFIt. Anyways, how should I partition my drive so that I can dual-boot both Leopard and Gutsy? I've already consulted the wiki, but some of the author's wording, not vocabulary, is confusing me. If possible could anybody help me to do this?

---

### Post by MaddMatt on 2008-07-06
Is your main reason for not using reFit only because you don't like the look? Boot camp never worked quite right for me, so I do use ReFit, and the main benefit is that it is almost as configurable as GRUB. It even includes an auto-OS detection at boot if your Linux partition doesn't get set up just right. 

Anyway, how you partition your harddrive is really up to you. I use Linux primarily and OS X only rarely, so I've got mine like 50gb OS X and 200gb Ubuntu. One of my main points of advice is to create a separate /home partition, so that way if you screw up your system, all of your documents and settings will not get toasted as well (theoretically. It's worked for me.) You can just do a complete new install and everything looks just like it did last time. Partitioning takes place through the BootCamp utility in OS X before you even install ReFit though.  Your root partition (/) is probably never going to exceed 7 gigs, so I usually make mine around 10 or so to be on the safe side. 

My deal was that BootCamp never actually detected Linux, or it was pointing to the wrong partition (don't really remember), but because Jobs doesn't like his users to have configuration powers, it's very difficult (and not well documented) to make these sorts of changes. ReFit installations are well documented. So good luck. Hope this helps, but try being more specific in your opening post. 

Cheers!
-M

---

### Post by rollerbladerdave on 2008-07-06
Thanks for helping, but I need specific guidance. This time I'll be more specific. On my MBP I have a 160GB HD and would like to have about 70GB for Leopard and about 50GB for Hardy (I know, changed my mind since the first post). How would my partition table have to look in the Ubuntu installer. 

For example, post how much to allocate to /dev/sda, how much for a swap, how much free unallocated space, if any, should be left and any other necessary details. If GRUB must be installed, and if so, where? Or will Boot Camp handle that? Just post an example with minimal instruction and I should be able to figure it out.

---

### Post by rollerbladerdave on 2008-07-06
[http://img155.imageshack.us/img155/3233/w2u302wy.png](http://img155.imageshack.us/img155/3233/w2u302wy.png)

An example like the link above, post something of that nature, but with Boot Camp booting in mind, and I should be alright. I'm just unsure of what partitions and of what size *need* to be created.

---

### Post by escapee on 2008-07-07
Just choose the size of the partitions you want.  If you want 50GB for Linux, allocate 50GB through Bootcamp.  Check out the tutorials on the Ubuntu wiki.  However, you may want to stick with Gutsy then possibly upgrade to Hardy.  I tried installing 8.04 three different ways and it would always come up "No bootable device detected" on restart and I'd have to hold Option to even get back into OSX.

---

### Post by rollerbladerdave on 2008-07-07
I think I've figured it out now...after reading through the Wiki a couple more times. I'll give it a try tonight, I've just really wanted to make sure that I was doing everything right. One more question, though. If /dev/sda is mounted at "/", does the swap need a specific mount point? Also, how do I insure that the partitions are formatting? What must be pressed to insure that formatting occurs?

---

### Post by flaggh on 2008-07-07
I would not create a separate partition for swap.  A swapfile is just as effective.  See the SwapFAQ for more information on creating a swapfile:
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

I would install Hardy, it is supposed to have better support for Macs out of the box.  There is however a bug in the installation as escapee mentions that will require you to reconfigure grub the first time you boot up.  This is easily solved, see this post for more information:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11]("http://ubuntuforums.org/showpost.php?p=3303463&postcount=11")

I would suggest installing rEFIt initially.  Once you have everything setup and working properly, you can disable rEFIt, or remove it completely, but initially I think it is a useful tool.

The ubuntu installation will walk you through all the proper formatting and installation.  The only thing you have to watch for is make sure you install grub to the correct partition.

If you want to get fancy (but not too fancy), MaddMatt's suggestion to make a separate /home partition is a good one.  I ALWAYS recommend doing this but to each his own.

Here's my partition scheme:
```
(parted) print                                                            

Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI system partition  boot 
 2      210MB   21.6GB  21.3GB  hfs+         Customer                   
 3      21.6GB  102GB   80.4GB  hfsx                                    
 4      106GB   120GB   14.3GB  ext3

```

partition 3 is mounted on /home and partition 4 is my root filesystem.

---

### Post by rollerbladerdave on 2008-07-07
Thanks a lot, all, I think I'm ready to install it.

---

### Post by cyberdork33 on 2008-07-08
For partitioning, the easiest way I tell people to do it is to 

[LIST=1]
[*]use BootCamp to partition the drive (shrink the OSX partition and create a new FAT32 partition).
[*]Boot the Ubuntu LiveCD
[*]Start the Partition Editor (gparted) and delete the FAT32 partition at the end of the disk that BootCamp created leaving empty space.
[*]Start the Ubuntu installer, and tell it to install to the largest free space. This will create a swap and root partition in the free space for you.
[*]The above information about the installer bug still applies!
[/LIST]

---


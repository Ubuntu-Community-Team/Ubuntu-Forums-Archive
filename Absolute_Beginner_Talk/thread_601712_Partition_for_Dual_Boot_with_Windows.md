---
title: "Partition for Dual Boot with Windows"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by madeinbrazil on 2007-11-03
I want to install Ubuntu as dual boot and planning to partition everything where if anything goes wrong with either I just place the (Ubuntu or Windows) installation CD and get back to normal.

I have 120GB HD but it only has 30GB empty. If needed I can empty more, but I can also purchase another HD.

From reading I've discovered that it is best to partition as:
[LIST=1]
[*]Windows installation (NTFS) - which are all files except the /MyDocuments/;
[*]Ubuntu installation - which are all files except /Home;
[*]NTFS partition for all documents and media files (Windws MyDocuments + Ubuntu's /home);
[*]SWAP 2GB (twice the RAM)
[/LIST]

Questions:
1) Is the above correct?
2) Is it safer to add another HD? If so, have the second one with which of the partitions above?
3) Is it really needed to have another partition for Ubuntu's /home? I plan to have all documents and media files on the NTFS partition for both systems to read. Or does Ubuntu's home have other files that only Ubuntu creates and needs?

---

### Post by defrex on 2007-11-03
I would seriously warn against putting /home on an NTFS partition. fat32, if you must share it with windows. Though I've never heard of putting My Documents on it's own partition, and honestly I didn't even know it could be done. My personal recommendation would be this:

1. ext3 (the standard Linux file system) for / (the main Ubuntu files)
2. ext3 for /home
3. swap
4. windows

The reason lots of people put home by itself is so that you can reinstall Ubuntu without losing any of the data in /home. It's not essential though.

One thing to point out, however, is that you must install windows first and then ubuntu. Otherwise windows'll own the boot record.

---

### Post by Pumalite on 2007-11-03
Best is:
1.-Windows installed first
2.-If Vista, use Vista partitioner
3.-If XP, use Gparted Live CD
4.-Good scheme: 10 GB for '/', 2x RAM up to 1 GB, the rest for /home
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by moocow1452 on 2007-11-03
1) Is the above correct?
Yeah, that's how you do it. Although I don't know a another partion for home. It could get messy.
2) Is it safer to add another HD? If so, have the second one with which of the partitions above?
Not necessarly, unless you want to keep a backup of documents and stuff, one should be fine. If you need to, I'd put the NTFS partition on it. 
3) Is it really needed to have another partition for Ubuntu's /home? I plan to have all documents and media files on the NTFS partition for both systems to read. Or does Ubuntu's home have other files that only Ubuntu creates and needs?
As I said before, I wouldn't mess with it. Especially since you're new at this, I'm new at this, and it isn't really helpful to a dual-boot. Just keep your docs on the NFTS and you should be fine.

---

### Post by Pumalite on 2007-11-03
The more space, the better; just make sure is ALL SATA or ALL IDE.

---

### Post by madeinbrazil on 2007-11-03
Thanks for the great and fast reply!!

Sorry, I didn't mention it. I'm already using Windows on the machine and this HD. So wouldn't have to worry about that. Actually, I am worried about Windows and thats why I want to try Ubuntu more seriously.

> 
The reason lots of people put home by itself is so that you can reinstall Ubuntu without losing any of the data in /home. It's not essential though.
Thats exactly why I'm researching a lot about it. I want to make the setup so if I need to reinstall any of the OS I just place the installation CD and fix my problems without losing any important data.

So, I want to make all documents and multimedia files created in either OS stand alone and outside of system files. I can manually place MyDocuments elsewhere, just wondering if the same could be done with Ubuntu.

> Just keep your docs on the NFTS and you should be fine.
So, would this mean that I could later reinstall Ubuntu without loosing files I created on it? 

Sorry if these questions seem stupid. Better be safe before I mess with the system and do it well planned to avoid later problems.

---


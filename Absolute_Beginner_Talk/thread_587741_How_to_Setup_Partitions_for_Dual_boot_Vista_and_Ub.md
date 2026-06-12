---
title: "How to Setup Partitions for Dual boot Vista and Ubuntu"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Crypto77 on 2007-10-23
Basically I have a 160 gb hardrive. I want 50 gb's to be for Windows and the rest for Linux. So what sort of partitions should I setup to do that? I know I need a 50 gig Windows partition, a 1 gb swap partition, but I am unsure as to how I should setup the logical or ext3. What does each one do and how will they affect my performance? Should I make a bare minimum sized ext3 partition and a large logical one?  What are ntfs partitions?  Is there a way to store data that would be viewable from either operating system?  

Sorry for so many questions.  Obviously I could just use the "guided" option when loading Ubuntu, but I have a feeling that a few months down the road I will bite myself for doing so and not setting it up properly from the get-go.

---

### Post by Shazaam on 2007-10-23
160 gigs huh?
Do the 50gig partition for Vista, add a 1gig partition for /swap, then make an EXTENDED partition in the remaining space. That way you have lots of room to add as many flavors of linux you want to without bumping up against the 4 primary partition limit.

This link will help...
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by William S on 2007-10-23
Hi!
You can easily shrink (resize) your Vista Partition in Vista , this should be tried first. How to do this is described here. 
[http://www.tech-recipes.com/rx/1593/vista_shrink_partition](http://www.tech-recipes.com/rx/1593/vista_shrink_partition) 
The unwritten rule is at least  3 partitions for Linux systems:  /home, root and /swap 
/home is like Documents and Settings, like if you're going to upgrade you don't need to format the /home partition only the root one. 
Root is where the OS go and basically every other thing. 
Swap is for extra memory, not strictly necesarry to have if you got a lot of RAM, but recommended. 
After you shrinked your Vista partition to a decent size you can use the Gparted live CD to setup the free space. 
[http://gparted.sourceforge.net](http://gparted.sourceforge.net)
After that you load the Ubuntu installer, choose manual partitionl and specify the mount point for each. 

NTFS partitions is the file system used by Windows systems (someone else can probably explain more about it) 
EXT 3 is the type of file system used by Linux OSes.

---

### Post by Inxsible on 2007-10-23
Psychocats has a great link on deciding the partitions. Along with the installation link, use this to figure out the sizes and the partitions that would be required

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I would second the option of having a separate home drive. A lot of advantages when upgrading the OS (which you will do eventually, since Ubuntu is released every 6 months and its FREE :) )

---


---
title: "A concerned first-timer says hello."
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by ZenMaster on 2007-03-05
Hello to all.

Here I am, ready to go into the world of Ubuntu. Pretty exciting and scary.

A little bit of a background - I know virtually nothing about Linux and only a little of Unix. Being Java developer ( and for Windows based web application ) doesn't help either. It gives me a bit of a common sense on how things are done, but that may be deceptive. I am fairly patient and receptive, or at least I want to consider myself to be :) ... so that should be of some help with Ubuntu, or so I heard.

Now, enough of the blubbering, to the aforementioned concerns.

**Note:**

I went through 5-6 pages of partitions related threads, but the information in them was not decisive enough or too complicated, especially given the risk of ruining something I don't want to. Please, bear with me.

**Some info:**

1. I do want to keep my Windows installation intact, for several reasons. Being a bit scared is one of them.

2. I have 3 partitions at around 27GB each - NTFS.
    
    [LIST=1]
[*]C: - Windows partition
[*]D: - empty partition
[*]E: - data partition ( irrelevant in our case, I think )
[/LIST]

**Target:**

What I want to do is to install Ubuntu on the empty D: partition so that I won't have any Windows related data wiped out - to the point where my Windows installation is not working. 

I am concerned with the following things:

1. How do I recognize the D: partition as the one that Ubuntu should be installed onto? From inside of the Ubuntu installer it will look something like dev/hda6, or am I mistaken and it will actually show all the partitions in the order they exist on my Windows system?

2. I have to make 4 ( 3, but recommended 4 ) partitions for Ubuntu itself - /,swap,data and home ( although, as I understand, it can be done later ). Is it possible to divide the existing D: partition into 4 parts and be done with it? Or should I repartition the whole disk again ( which is a scary thought )?

3. I understand, in case I decide to uninstall Ubuntu, that there is a "problem" with GRUB loading after the Ubuntu partition was wiped ( can I do it by just formatting that disk? ). 
This page: [[COLOR="DarkOrange"]Un-install Page[/COLOR]]("http://www.users.bigpond.net.au/hermanzone/p18.htm") suggests that there are several methods to overcome that "problem". Question is - can I perform any of them before actually uninstalling Ubuntu ( by reformatting the D: partition?

4. I read that defragmenting that D: partition is helpful, but does it apply to the empty one as well? Or should I just format it?


I hope that it was not too much to ask, as it seems to me that the answers to all this questions can be put into 3 - 4 sentences, but would help immensely.

Thank you, I look forward to become a member of the community, and, may be, one day to become a helpful one.

---

### Post by aysiu on 2007-03-05
I'll be honest and say I don't have the energy to answer all your questions, but I believe this page will shed some light on your issues.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by chaplanger on 2007-03-05
> **ZenMaster said:**
> 

1. I do want to keep my Windows installation intact, for several reasons. Being a bit scared is one of them.

2. I have 3 partitions at around 27GB each - NTFS.
    
    [LIST=1]
[*]C: - Windows partition
[*]D: - empty partition
[*]E: - data partition ( irrelevant in our case, I think )
[/LIST]



Carefully check out the size of each partition.  When you install Ubuntu one of the easy ways to determine where to install is to look to partition size.

BTW -- Is your data partition NTFS or FAT 32?  If it is FAT 32 you can easily share date with the Ubuntu partition.  (Keep in mind that FAT 32 does have some size restrictions though)

---

### Post by Phantom784 on 2007-03-05
I'd suggest deleting your D: partition with a program such as Partition Logic.  This way, when you install Ubuntu, you can simply tell it to install on the free space and it'll leave your other partitions alone.  There are different tools that can do this, partition logic is just one that has worked for me before.  You download a windows program that writes it to a floppy, and then you restart and boot to the floppy.  From there, it's pretty self-explanatory.  Your d: partition should be the one in the middle.

Here's the link: [http://partitionlogic.org.uk/](http://partitionlogic.org.uk/)
Good Luck!!!

---


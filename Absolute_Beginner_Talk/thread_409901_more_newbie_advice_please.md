---
title: "more newbie advice please"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by fast eddie on 2007-04-15
Ok this is my first post so please be gentle :) 

I have a machine that I want to use to run SlimServer for my Squeezebox. At present it has the following:

C drive - 250G with XP on
G drive - 2nd internal 500G with my music on

What I would like to do is have a dual boot system on the main C drive with a reinstalled XP and Ubuntu. I want to run this machine headless as a server using Ubuntu and still have the option of using the XP if the office pc fails.

Questions:

1. I want to use Ubuntu as the main OS for running SlimServer so is there a way I can keep the G drive containing my music partitioned as NTFS so I can copy new music from another machine over my home network?
2. I was planning to use putty to remotely control the Ubuntu machine from my new Windows box with Samba (if I can get it going) is this the best way of doing things?
3. What would you recommend the C drive partitions to be set up as: XP=200G and Ubuntu=50G or something different?

Hopefully the above makes sense and someone can help me

Cheers,

---

### Post by seshomaru samma on 2007-04-15
What your refer to as C and G , are they on the same disc?
Ubuntu will need it's own partition
You will need to resize one of the partitions and create a Linux partition
The Ubuntu installer can do it for you or you can do it yourself with Partition Magic or a similar programme on Windows
I don't think Ubuntu can write to an NTFS partition , it can read but cannot write as far as I know. It's better if you make a FAT32 partition to which both Linux and Windows can write
The default installation of Ubuntu is about 5G 
10G would be enough - it really depends what you want to do with it

---

### Post by Sef on 2007-04-15
> Partition Magic

Be careful with partition magic, it and linux have had problems with getting along with each other. Better would be [GParted]("http://gparted.sourceforge.net").  It's the partitioner that Ubuntu uses.  Get the latest version of [GParted]("http://gparted.sourceforge.net").

---

### Post by fast eddie on 2007-04-15
The C and G drives are on separate disks.

The main thing I want to do is run SlimServer in Ubuntu because I have been told that Ubuntu is much more stable for running SS . Having a dual boot system with Windows would be just in case the office pc died.

Can I have a dual boot on the C drive and format the separate G Drive for use only with Ubuntu so that when I need to add more music I can do it via Samba from the office pc runnning XP? Can I partition a separate drive using GParted? I will be starting to set this up in a couple of weeks but wanted to get some advice first to make life easier hopefully :)

I can then just have say 10G for Ubuntu on the C drive and the rest for Windows so if I want to boot into Windows I will have approx 240G.

---

### Post by Sef on 2007-04-15
> Can I have a dual boot on the C drive and format the separate G Drive for use only with Ubuntu

Do you have one hard drive with multiple partitions or two hard drives?

> I can then just have say 10G for Ubuntu on the C drive and the rest for Windows so if I want to boot into Windows I will have approx 240G.

Yes.  

Note: Linux calls the partitions differently:  hda1 is the first partiton (commonly called c in windows); hdb1 for the second partition, etc.  (For one hard drive.)

---

### Post by fast eddie on 2007-04-15
Sorry for causing confusion. At present I am running XP with 2 separate HDs which are called C & G

1st HD = C - 250G with XP on
2nd HD = G - 500G formatted for NTFS with music files on

So I guess I am looking to get the following:

1st HD - 1 x HD dual boot XP=240G and Ubuntu=10G

2nd HD - 1 x 500G Ubuntu formatted just to store and access music files using SS which would only be accessable from Ubuntu

So if I boot in Ubuntu I will be able to access the second 500G HD, but if I boot into XP all I can use is the 1st HD that has an XP partition and an Ubuntu partition.

Does that make it clearer in how I would like to set it up?

Again sorry for any confusion

---

### Post by freebird54 on 2007-04-15
It depends partly on what D: E: and F: are on your system!  If they are all primary partitions on the first hard drive it could be tricky to set up.  (maximum 4 primaries allowed)  If D: is a partition, and E: and F: are CD/DVD or others - then no problem.

You can make the second drive something that Windows can see, or not - as you choose.  The most 'native' Linux filesystem is ext3 - Windows can only read that if you wish it too, and add a driver for it.  However LInux can use lots of different file systems, so if you want it to be difficult for Windows to see it, you can do that too  :)

The partitioning program in Ubuntu can resize Win partitions, and create new ones as needed - no pre-config needed there - just prethought!

For Stability (primary purpose of a server, usually) the 6.06 Dapper edition is probably the right choice.  Any questions you have can be researched quite easily with search on these forums, or Googling - or asking specific ones here.  You would not BELIEVE how much info is out there (well - maybe you would..)

Enjoy!

---

### Post by seshomaru samma on 2007-04-15
my suggestion:

_1st HD _- 

one partition for XP

3 partitions for Ubuntu , like this:

        10 G for /  (or 'root') these are the system files, actually 10G is probably too much but you seem to have plenty of space so I chose a 'clean' number
        1G or 2G for Swap , Linux uses the Swap partition for extra memory space, the swap should be double your current memory , if you have 512Mb then you need 1G swap if you have 1G memeory then 2G swap and so on
        10G for /home - this is where Linux stores your preferences and personal data, it's good to have a /home partition cause if you ever need to reinstall or upgrade , you will save all your settings and programmes saved and unchanged

_2nd HD_ - a FAT32 music partition accessable from both Linux and Windows

---


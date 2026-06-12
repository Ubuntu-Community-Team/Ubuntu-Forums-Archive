---
title: "[SOLVED] 6.06 Live CD manual partion sizes and process..."
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Mike Krall on 2007-11-10
I've read and read... the problem is understanding...

I've got an empty machine (operator error on previous partitioning attempt) and a Ubuntu 6.06 LTS Live CD. 

The machine (white box by Saeger) has a ToshibaMK3017GAP HDD (Live CD partitioner shows 27.95 GB ~ 28,618 MB unallocated). There is 512 MB RAM (I think... there was  Pent. 4 data In "System", when XP still existed, showing 224 RAM... but I believe I see 512 RAM on start-up). 

The  things I've read that help are: 
[http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php")  
[http://ubuntuforums.org/showthread.php?&t=282018]("http://ubuntuforums.org/showthread.php?&t=282018")
[http://ubuntuforums.org/showthread.php?t=590154&highlight=manual+partitioning&page=2]("http://ubuntuforums.org/showthread.php?t=590154&highlight=manual+partitioning&page=2")

My initial thought was to do 3 primary partitions:  In order...  " / " as ext3  with 7.5 GB,  "/home" as ext3 with 19.45 GB,  "swap" as ext3 with 1 GB... now I don't know.

There is a description in the third link by "kebes" on proper file type designation of "swap" when partitioning, I have to assume is correct.

In the second link there is an added section:

**Bulldog's Partitioning advice**
[I]Quote:
Some suggestions for disk partition.
Windows as big as you like.

Create an ext3 10GB for /
Create an extended from the rest off the space.
In the extended,
Create a /home 10GB
Create a swap 1GB
Create a ext3 partition for data if you have space left.
You have a separate /home for some data and a separate /data partition to backup important data.
[/I]

"Bulldogs" advice seems logical for format... whether I can actually get that done on the Live CD's partitioning tool, I have my doubts. And based on my 27.95 GB, I don't know how to allocate.

As I said, I need help both with deciding on partition size, type, primary, extension, etc., and, once there, will likely need help with the mechanics of getting it set on the Live CD partitioning tool.

Two last things: 

My computer reality is extremely simple... no games, no music, no movies. I have what I see as large amounts of saved data that continues to grow...  .pdf's, word .docs, pictures, etc... not totaling 1 GB... and I might need to have a simple web site showing pictures of things made and/or for sale (that's a big maybe...) with no "shopping cart".

I have come to understand there is a range of "Beginner". It is very wide. I am at the extreme left end of that range... I literally know nothing of Linux/Ubuntu or computers, for sure.

Thank you...

Mike Krall

---

### Post by matthewcraig on 2007-11-10
Either one is fine.  Seems like you're splitting hairs, at this point.  Time to just buckle down and get it done.

---

### Post by bulldog on 2007-11-10
Hi Mike,

About the partition part,to do this simple use the Gparted live cd.
Download it from here,[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) and burn it on a cd.
Boot from it and partition your hdd.
You have only 27Gb of space and that isn't much,but if you don't install too many packages it should work.

First remove all existing partitions on the hdd,if there are any that is.

Create a 6GB partition for root called  /
Create a 1GB partition for the swap
Make the rest a partition for your /home

I should use the alternate cd to install,but if you have a live cd,you can boot it first to see of all your hardware will work.
Specially your internet and graphics.
If things are working properly you can start the install.

When you come to the partition part choose **manual partitioning**
This gives you a page with all your partitions.
Select the 6GB partition and click next on that page you have to set it as mountpoint /
set bootflag enable and set it to format ext3
Select the swap and mount it as swap and format as swap
Select the last partition mountpoint /home and format it as ext3
Apply your settings if done and proceed with the install.

If you have any question,just ask.

---

### Post by Mike Krall on 2007-11-10
**Matthew**,

I understand that... knowing first is my nature, the tighter wound I become, the more I need to know first... 


**Bulldog**,

I think I get it enough to do as you suggest. I've run on the 6.06 LTS Live CD enough to feel I can do the basic things I want to do... graphics I don't know about.

Questions:

1.  I size 3 partitions, all primary, all ext3, and they are in the order of " / ", "swap", "/home". Then go to next page where I mount them, etc.... yes? Or is "swap" file type "linux-swap"?

2.  In your suggestion to [http://ubuntuforums.org/showthread.php?&t=282018]("http://ubuntuforums.org/showthread.php?&t=282018") you mention "/home" in the middle as an extended partition with "swap" in it then the rest as "/data". What size would a person make "/data" and as a primary partition? 

3.  If I partition 6 GB " / " (ext3 and primary) first, then 1 GB "swap" (primary and "linux-swap"?) second, does it make any sense to make the remaining space "/home" as an ext3 and extended instead of primary?

4.  Why do you put "swap" as second partition instead of at the end,  as a "standard install" would put it... advantages/disadvantages?

Thank you... I am unwinding...

Mike

---

### Post by bulldog on 2007-11-10
The order of the partitions is of no importance :)
You need to make at least two partitions with gparted [they have no names then] that is required for ubuntu to install.
However,when you need to do a reinstall for some reason you have a harder time,cause you have to backup your data.
That's why I suggest to make a third partition which will be mounted as /home when you install.

You can do it like this too:

One partition 6GB first primary
One partition 2GB second primary
One partition rest of your space thirth primary

Or.
One partition 6GB first primary
Rest of the hdd an extended partition
One 1GB partition logical
One partition rest of the hdd logical

As you see there are options enough,but to keep it simpel do it like I said in my previous post,except if you have a problem with that kind of partitioning.

About the swap,yes it's linux swap/solaris but that makes no difference.
I make the swap in the middle so you can make the rest /home without thinking about MB's and that kind of stuff,it's just easier for you,and it won't make any difference.

---

### Post by bluepowder7 on 2007-11-10
swap partitions are of "swap" type.  i usually put it as the last partition, which SHOULD make it on the outside of the drive where it might actually have fastest access.

how many OS'es do you want on this machine?  if just one, then stick with 3 or maybe 4 partitions, all primary (no need for extended).  maybe even make a /boot partition if you'd like (that would go up front as the first one)

this is how you could arrange them, from beginning to end on the drive:

/boot (optional) --- /root --- /home --- /swap
type ext2 --- type ext3 --- type ext2 or ext3 --- type swap

for /home, i prefer ext2 since there's more tools for recovering files you delete by accident.  in ext3, they're GONE forever.  ext2 in linux is about as common as FAT in windows.  it's like apple pie and lemonade.


another option for partitions (something that i've done) is to have:

/boot --- /media/storage --- /home --- /root --- /swap
type ext2 --- ext2 --- ext2 --- ext2 --- swap

you could put the /home and /root into an extended partition, so that /boot, /media, and /swap are all primary partitions.  in that case, i'd make /home quite small (500 megs) and assign the bulk of the space to /media/storage, which is where you would keep all your docs, spreadsheets, tunes, porn, etc.  that would be like your "My Documents" folder, except that it's a whole partition.  then, the /home is used only for your config settings, and if you need to blow away the OS and install some other OS, you can reuse the /root and /home partitions, and your /media/storage stays untouched so all your hard work is forever safe.

---

### Post by Mike Krall on 2007-11-10
**Bulldog,**

I don't know enough to know if I would have a problem with your originally stated partition lay out. I asked because I thought having the extended partition with "/home" and "swap" might keep me from grief down the road if I found I wanted to add another logical partition  (if that is stated right)... like a small web site of pictures with description, say. 

**bluepowder7,**

Only one OS unless I wander over towards Xubuntu, which would be because I needed to go smaller due to this machine.

**All,**

Last question unless I get stuck... Would you say (or say more) about ext2 **vs.** ext3 as file type for "/home".  That would be, on a computer for a simpleton...

Mike

---

### Post by Mike Krall on 2007-11-10
It works... or, I think it works... I'll be back, inevitably.... but I'll try not to be... I'll try to not add to the load.

Thank you...

Mike Krall

---


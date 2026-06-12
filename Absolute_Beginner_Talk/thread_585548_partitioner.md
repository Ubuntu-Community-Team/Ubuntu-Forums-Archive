---
title: "partitioner"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by hait2 on 2007-10-21
hi
i am about to install ubuntu but want to check one last thing =p

i used gparted to slice away 15gb from my main windows partition, so now it's unallocated/free space

if i use the guided- use largest continuous free space option in the ubuntu installer, it will do what i expect, right? (aka not kill my windows and use the 15gb of unallocated/free space instead)

it says it will format partitions #6 and #7 of scsi1 (0,0,0) (sda) as ext3/swp respectively, which is strange as i don't have 6-7 partitions anywhere :confused:

---

### Post by pieisgood4589 on 2007-10-21
To be safe, just do a manual partition, and select the pre-made one that you are talking about. Good luck!:lolflag:

---

### Post by hait2 on 2007-10-21
the manual partitioner is quite intimidating though

as i get it, i have to actually have 2 partitions, swap and /, where swap is roughly 2*my ram and / is the rest, and where ubuntu will be installed/my files will be:confused:

here are what my partitions are now looking as
[http://img529.imageshack.us/img529/7480/screenshotce0.png](http://img529.imageshack.us/img529/7480/screenshotce0.png)

(the sda2 is my current windows partition)
actually i have no idea what sda5 is.. hmm


i have to create 2 new partitions from the free space ? (i'm thinking like a 13gb/2gb split)
am i on the right track?

---

### Post by Pumalite on 2007-10-21
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by steve.horsley on 2007-10-21
Short answer - yes.

Long answer - Yes, shrinking the Windows partition and then telling the installer to use Guided and use largest continuous free space will do pretty-much what you expect. 

In practice, it will probably create an extended partition from the free space and create both the Ubuntu system partition and a swap partition inside that extended partition.

---

### Post by louieb on 2007-10-21
You have already done the hard and dangerous task of shrinking the Windows partition.  So lets take out the guess work. 
I just looked at you screen shot, **You have a problem**. The free space is in a place that can't be use to create another partition.
What I would do is fire up GParted again.
It should show sda3 as being an extended partition. 
You need to grow sda3 to the left to take up the unused space. After you do that the space will still show as being unused. 
Then you can create 2 logical partiton in the free space. one for /  and another  for swap.  

Please post a screen shot of your GParted window Press (Alt+PrtScreen)
and I'll try to help some more. [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

After you get GParted to create the partitions,  it will be easy to use the manual partition option with your new partitions.

---

### Post by hait2 on 2007-10-21
thank you for the reply louieb

unfortunately, i've already gone ahead and used the guided thing to install ubuntu

everything seems to be ok (dualbooting etc. works fine, nothing exploded)
**but**
when i use gparted to look at my partitions, they look ugly. what i mean is unordered, cluttered, trash (for a lack of a better word). i dont know, there's a bunch of new partitions created out of thin air, some unusable space etc

i'll let the picture do the talking
[http://img138.imageshack.us/my.php?image=screenshotdevsdagpartedwx6.png](http://img138.imageshack.us/my.php?image=screenshotdevsdagpartedwx6.png)

i am hesitant to try and do anything and screw it up, but i think this may be problematic down the line
is there a way to 'unpartition' or some other way to clean up the drive?

edit: just to clarify, what i was thinking is everything after the ubuntu swap partition to be a joint fat32 single partition for both windows and ubuntu access. is this possible?

thanks a lot in advance,
hait

---

### Post by louieb on 2007-10-22
Well I'll be.  looks like  sda3 was grown to the left and took up the unused space,  Did you do that using Gparted? OR did the guided partitioning do that? 

But as for every thing after swap being one partition sure you can do that.

Copy whatever you have on sda4 and sda5 to sda2.  Your going to delete those partitions.

Now you going to need the a live CD for the rest. You can use the Ubuntu Live but I prefer to use    the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") its a good tool to have handy.[LIST]
[*]Fire up Gparted from a live CD
[*]Delete sda4 and sda5
[*]Click on sda3 and resize to fill the now unused space.
[*]Cilck on the unused space and an add the new partition. (my two cents if you primarily use Win make it NTFS or if you use Linux mostly make it ext3, either will work better that fat32)
[*]Click apply[/LIST]After you add the partition. Ubuntu may be broke but don't worry. Changing partitions on a drive sometime caused the UUID of existing partitions to change.   You may have to fix /etc/fstab to get swap working.
I can go over that with you if it happens. May not happen. 
Now to use your new partition in Ubuntu check the psychocats link in my signature. That site has a nice tutoral on mounting partitions in Linux.

---

### Post by glotz on 2007-10-22
Hmmm, what is that 'unusable' 8 megabytes? Is his disk dying?

---

### Post by hait2 on 2007-10-22
i sure hope my hdd isn't dying >_<

yes GParted guided thing did grow sda3 to the left

EDIT:
ok, i figured out what the partitions are now,

sda1 is DELL UTILITY, i guess it's necessary?
sda2 is my windows
sda3 consists of
-UBUNTU boot partition
-UBUNTU swap partition
-unallocted 8mb of space

**-an almost empty IMAGE partition that contains 2 hidden files: Recycled and System Volume Information. Recycled is empty, SVI has a folder called _restore{long hex string} with more folders in them.**

^what is that? do i need it?

Then, there's 4.63gb of unallocated space (i'd like to use)

**and a 3gb DELLRESTORE partition with a bunch of bin/bat/src folders/files**
^what is that?do I need this? 

then some 8mb unalloc space at the end again

thank you for all your replies so far~~

edit: other question answered by glotz

---

### Post by glotz on 2007-10-22
Ubuntu system beep? You mean the terminal bell? (e.g. when hitting tab with no input) You can disable that via edit > current profile

---

### Post by hait2 on 2007-10-22
ah, thank you glotz!
i couldn't find the preferences you were talking about, but after poking around, i found the option in the Sound submenu. could you be a little more specific as to which edit>current profile you mean (i want to change some other options)

---

### Post by glotz on 2007-10-22
You're welcome. I'm afraid I can't be more specific since I'm on an older version on Ubuntu. (and gnome-terminal)

What would you like to change?

---

### Post by hait2 on 2007-10-22
it's just small aesthetic/convenience things. a bit silly for me to worry about them before my partitions are all cleaned up, especially since fixing them might bork my ubuntu according to louieb :)

edit: although i am curious what the exclamation/orange triangle near my windows partition means. i sure hope it's referring to something trivial like linux not being able to write ntfs, rather than it about to explode? but then what do the locks represent :(

i tried to google for gparted icons but came up with nothing (admittedly i didn't spend a lot of time on this)

---


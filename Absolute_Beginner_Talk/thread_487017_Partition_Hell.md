---
title: "Partition Hell"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Delirious on 2007-06-28
Ok i had one heck of a time getting ubuntu to install on the correct partition. First it would recognize my single sata drive that houses my OS's as sdb and my raid array as sda. All i know is that it wouldnt boot ubuntu when it was installed like that. So i finally figured out that when i delete all the partitions but the windows one it puts the drives in the correct order.

Now that i figured that out i cant figure out whats wrong with gpart and am having a hard time explaining so a picture is worth a thousand words.

All i have to say is why does it leave little pieces of un partitioned space in between partitions when i definetly didnt setup the partitions like that?

And that large unallocated piece at the end of 400GB was supposed to be parrt of the /home partition but Ubuntu decided other wise for some reason even though i entered the correct number in MB.

[IMG]http://i4.photobucket.com/albums/y147/Typicalsloan/Screenshot--dev-sda-GParted.png[/IMG]

[IMG]http://i4.photobucket.com/albums/y147/Typicalsloan/Screenshot--dev-sdb-GParted.png[/IMG]

---

### Post by Shazaam on 2007-06-28
I think you may be running into the 4 Primary partition limit. Anyone else have an idea? Are you using the livecd to run gparted?

---

### Post by Delirious on 2007-06-28
> **Shazaam said:**
> I think you may be running into the 4 Primary partition limit. Anyone else have an idea? Are you using the livecd to run gparted?

Im using gparted in the live cd.

I only need 4 primary partitions on the OS drive:
/boot
/
c:
d: (for page)

The raid array only has 2 primaries:
/swap
E: (windows programs)

The rest on the array are extended. The last partition is just as wierd as it would let me use the full 500+ GB for /home, when i specified that ammount it spit out some random number.

It seems to be sporadic, sometimes it will work and do what i want others it wont.

---

### Post by Scunizi on 2007-06-28
Doesn't Raid require that both drives have an identical structure with regards to size and partitioning? Maybe that's one of the other Raid's (3,4,5).

A couple of things.  It's really hard to find the release notes currently with the new website setup.  However, I remember Dapper had issues with installing when raid was active.  Even if you weren't using raid, just SATA drives.  I had that issue.

As for your partitioning on sda (large drive), it looks like your windows partition is not at the beginning of the drive leaving that 1 meg of space there.  No worries. I'd ignore that.

If you're planning on reinstalling, I'd delete all the linux partitions and start over.  I'm not sure why you are creating a seperate /tmp partition or /boot.  I think you'd be better off creating root first (8-12 gb) then /swap (1.5 - 2gigs) then the remainder /home.  I've found that reiserFS works better on my SATA drives and if you want to try it, use it for your root.  If you need file access from windows to your Ubuntu home directory format /home to ext3 and load the appropriate driver in WinXX for access. This works better than the experimintal NTFS drivers.

If you're planning on multiple linux os's, only create one swap anywhere you want it.  2 gigs is plenty.

As for your second drive (sdb), use it for data, backups  or a different OS version install.  

I also noticed your NTFS partition on your sda drive (/dev/sda1) is mounted as /media/sdb1.  That's kinda weird.

---

### Post by Delirious on 2007-06-28
The smaller drive is the one i have Linux and Windows on. The large is my Data and Program drive.

from windows if you look at the partitions it looks like:

| /boot | Ubuntu / | Vista C: | Vista page D: |

the raid array should look like:

| Vista E: | /swap | Extended partitions: | /tmp | /home |  

There shouldnt be any space between any of the partitions and the /home should be 550 GB but when i entered that ammount it gave me 150GB :frown:

there shouldnt be any problem formating the raid array anyway you would a single drive.

I guess i could reformat, for the 20th time, and try reiserFS. Linux definetly has problems with sata drives.

I got the idea for the seperate temp and boot partition from reading several different how to's and such. Bad idea?

---

### Post by Scunizi on 2007-06-28
Yea.. personally the most number of partitions for linux you'll need is 3.  The other posts that describe seperating some of the other bits are "players".  That is, they either think they have a need to do it that way or they are developers who have reasons beyond the casual user.  If you allow the desktop cd to do its own thing instead of manually partitioning, it will only create 2 partitions, root/home & swap.  It's nice to seperate home just in case you need to reinstall or do a fresh install of a newer system.  You won't lose all your data.

sdB Partition
So, with my thinking cap back on what I would do is.......
1> On sdb - delete the two ext3 partitions so you'll have one unallocated space of apx 22.25gigs. repartition that to 12 gigs for root.  DON'T use the graphic slider bars to position the space.  It should default a the beginning of the drive.
2> The remaining space partiton with a mount point of /dev/sdb2 or whatever the default becomes and format it ext3.  This drive will now be maxed out and everything will be primary partitions

sdA Partiton
3> On sda, that 1st unallocated megabyte, you may not be able to recover that without moving the NTFS partition below it.  Personally I wouldn't risk screwing up the NTFS partition with gparted.  NTFS doesn't always like other tools messing with it. So write off that meg.
4> Delete all the partitions below the NTFS on sda creating one large unallocated amount of space.
5> Next create your /home partition to the size you want.
6> Now create your /swap to 1.5 to 2 gigs.  
7> Now your at three primary partitions.  You can elect to partition the remainder into one large partition or create an extended partition.  If this is a data drive, I'd just create one partition formatted with ext3 to handle the overflow from Windows.  It looks like you don't have much space left on the NTFS so you might need it.
8> Install Ubuntu
9> boot into windows and install the ext3 driver.  Here's one and it's FAQ page. [http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html).

Now you should be good to go..

---

### Post by Delirious on 2007-06-29
Thanks for th input!

I may try redoing it all im not sure.

My main reason for wanting to seperate some of the mount points was to do like i do in windows, just the OS on a seperate drive data and programs on another.

Seems like its really hard to do that as things are scattered everywhere.

---

### Post by Delirious on 2007-06-29
Ok i redid the partitions, this time i used an acronis 10 boot cd and partitioned and formated the drives with that.

aparently gparted is a piece of junk cause everything got partitioned and formated the way i wanted using acronis.

---


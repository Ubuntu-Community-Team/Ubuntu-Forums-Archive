---
title: "Partitioning with Ubuntu and Vista"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Justgeoo on 2008-01-08
I have been looking around the forum and haven't found a post to what I am looking to do. :)

I am a week old newbie with a Toshiba A205-S7464 notebook that installed Ubuntu 7.10 just fine. The computer came installed with Vista Home Premium. The HD is approx. 200 GB. 

I would like to partition the HD into 3 parts:
[LIST=1]
[*]Vista - 50 GB
[*]Ubuntu - 50 GB
 [*]Partition the remaining HD space
[/LIST]

The 3rd partition would be for my documents and media files. This is my dilemma, I would like this partition to be accessible to both Ubuntu and Vista. Is this feasible? How would I go about this? What partition format is needed for this to come true. Right now I don't have a clue on what to do.

Is there a better way of partitioning my HD? If anyone has some great ideals feel free to reply to this post. Your suggestions are welcomed. I really would like to dual boot my notebook, and also have both OS's have access to my documents and media files.

Any ideals?

---

### Post by bvmou on 2008-01-08
I have the same laptop, what you are talking about is doable.  What I did - and depending on how long you have been working with your vista install you may find this a bummer - was just reinstall vista with the toshiba oem disks.  It gives you the option of making the windows partition smaller.  Then I installed linux with grub on the bulk of the disk; grub is the bootloader, it will detect vista and let you boot into it if you choose to do so at the boot screen.  The third thing you want to do, if I understand, is create a partition that is readable and writable by both windows and linux.  The best bet there is a FAT32 partition (File Allocation Table, a slightly older but good technology.)

It used to be under XP you could resize the partition you were on from some system utility, that may still be the case and you should look for that before doing anything drastic.

The thing is, though, I theoretically might need windows for work but in fact I boot into it about once a month.

Either way, make sure you have backups before mucking around with this stuff ;)

---

### Post by Raptor45 on 2008-01-08
The process is actually pretty simple; there is no need to reinstall vista. You can use the gparted live CD to shrink your vista partition (this can take some time if the data is spread out) and then partition the resulting space however you like.

I recommend having space for the Vista and Ubuntu operating systems as you said (the two 50 GB partitions, NTFS and EXT3 respectively). Keep in mind that Ubuntu doesn't need nearly that much space, a 10GB will do just fine leaving more room for your documents and such.

For the rest of the space, you can set this up as "home" partition. During the ubuntu install, just set the mount point to /home, and all your settings and files will go there by default under Linux. Having a separate home partition also makes it VERY easy to reinstall the operating system without having to worry about losing files or settings. This could be either EXT3 or FAT32 depending on your preference, as there is an installable driver for EXT3 which works in both XP and Vista.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by bumanie on 2008-01-08
I believe that gparted does not work well with vista and that the preferred method is to first shrink your vista with the in-built vista partition manager. Then you can use the gparted or the live ubuntu cd to set up the rest of the drive. Before you shrink the vista partition it is a good idea to backup any valuable data. It is also suggested to defrag before changing the partition size.

---

### Post by erfahren on 2008-01-08
how did you go about shrinking the Vista partition the first time? The reason I ask is because it was my understanding that niether the Ubuntu installer or GParted will work to resize Vista partitions becuase it uses a different (newer) NTFS - maybe I'm wrong about that. (EDIT: bumanie pointed that out as I was writing this)

Anyway, I did want to say that you most likely have a recovery partition of some kind at the beginning of the disk - it will be a primary partition

you can only have 4 primary partitions or 3 primaries and one extended

if you set up a seperate partition for swap than you could *now* already have four

in short, while you're going about this, you may want to go ahead and set the remaining space you want to have as extended - then it would be easier to divide up in the furure if you wanted to.

(Sounds complicated?) - it's really not - after you get the unalloted (free) space you first create an extended partition out of it and the create a logical within it.


a screenshot of my partitions is attached for reference - I have:

1) my Acer (Vista) recovery partition
2) the Vista partition
3) a FAT32 storage partition (I can access from both Linux and Windows)

4) the extended partition which includes the *logical* partitions:
 - 5) my Ubuntu root ( / )
 - 6) my Ubuntu /home
 - 7) swap
 - 8) my Xubuntu root
 - 9) my Xubuntu /home
 -10) another swap (which I really don't need)

for more on partitioning see: "Help on partitioning" - [http://www.users.bigpond.net.au/hermanzone/p17.htm](http://www.users.bigpond.net.au/hermanzone/p17.htm)

---

### Post by Raptor45 on 2008-01-08
Originally, even though I had heard of some difficulties, I just used the built in Ubuntu partitioner to shrink Vista, and I didn't have any issues. I can make no guarantees whether it will be the same for you.

---


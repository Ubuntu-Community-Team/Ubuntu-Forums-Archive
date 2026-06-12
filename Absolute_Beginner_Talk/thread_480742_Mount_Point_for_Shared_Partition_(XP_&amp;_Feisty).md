---
title: "Mount Point for Shared Partition (XP &amp; Feisty)"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Brian96 on 2007-06-21
I know there are dozens and dozens of threads about partitioning for dual boot, but I am having trouble finding a concise answer to a specific question.

I am running XP and Feisty on a 250-ish GB harddrive (so partitioning is not really a problem). I originally followed psychocats.net's guide on partitioning and settled on 3 main partitions: XP:NTFS, /home:ext3, and /:ext3 (swap implied).

I keep music, pictures, document files, etc., on /home that I share between OSes (including shared profiles for Firefox and T-bird). I ran into some permissions issues and got myself into a bind ([http://ubuntuforums.org/showthread.php?p=2886773#post2886773](http://ubuntuforums.org/showthread.php?p=2886773#post2886773)). So I'm not sold on using /home for my shared files.

What I've considered doing when I (inevitably, it seems) reinstall Ubuntu is this:
XP:NTFS
shared data:ext3
/home:ext3
/:Ext3

My questions are these:
1. What mount point should I use for the second partition? I've seen /data and /media. Bear in mind that the files will be frequently used in each OS, so the permissions need to very fluid (hopefully I won't have to change any permissions to accommodate this).
2. What is a recommended size for /home? If pretty much ALL my files are in the shared data folder, how much room will I need to comfortably house /home?
3. What is the current recommendations for / to house Feisty? (I'm also thinking about leaving some space untouched so I can try fresh installs of other distros.)
4. What kind of issues have folks run into with sharing files between OSes? What is the safest way to avoid these?

Any other advice is also welcome.

--Thanks.

---

### Post by haricharan on 2007-06-21
the safest method to share files is to make that partition as fat...that way u wud be able to see the partition in both the OS without any additional efforts.
I am not sure abt where u have to mount that partition exactly.....
My personal experience...I have NTFS-3G installed..that way i can mount the NTFS partitions in Ubuntu with read/write permissions and in Windows i have installed an application called Ext2 IFS [http://www.fs-driver.org/](http://www.fs-driver.org/) that enables u to read the ext2 and ext3 partitions..it pretty much works for me....

---

### Post by Brian96 on 2007-06-21
> **haricharan said:**
> the safest method to share files is to make that partition as fat...that way u wud be able to see the partition in both the OS without any additional efforts.
I am not sure abt where u have to mount that partition exactly.....
My personal experience...I have NTFS-3G installed..that way i can mount the NTFS partitions in Ubuntu with read/write permissions and in Windows i have installed an application called Ext2 IFS [http://www.fs-driver.org/](http://www.fs-driver.org/) that enables u to read the ext2 and ext3 partitions..it pretty much works for me....

Yes, I too have been using NTFS-3G and ext2ifs and have had no trouble with read/write stuff, unless you count the permissions stuff I mentioned. Hopefully the permissions troubles can be avoided with a different mount point for the shared partition.

I think what happened before is that by having my shared folders on the partition that mounted at /home, changing permissions to make them fully accessible for everything I wanted to do had a negative effect on stuff that is "supposed" to be in /home.

Basically, I want to have a separate /home partition--just in case--but also have a shared partition for all the files I use so that I can leave /home pretty much in its default state.

--Thanks again.

---

### Post by Inxsible on 2007-06-21
This is my setup
C: NTFS -- 25 GB ( Vista wouldnt let me shrink below 25GB :( )
D: NTFS - Windows Data -- 15GB
/ : EXT3 -- 9 GB
/home : EXT3 -- 20GB
/mnt/Shared: EXT3  -- 80GB

I use the /mnt/"WHATEVER" to mount my internal drives. /media i use for my external drives. I think it keeps it clean that way. Its just a personal preference. In fact I had my shared drive mounted at /shared previously, but then I changed it to /mnt/Shared.

I have given you the sizes of each partition to get an idea, you can certainly have different sizes depending on your needs

Hope that helps

Oh and I use ntfs-3g and ext2ifs without any problems between Ubuntu and Vista

---

### Post by Brian96 on 2007-06-21
> **Inxsible said:**
> This is my setup
C: NTFS -- 25 GB ( Vista wouldnt let me shrink below 25GB :( )
D: NTFS - Windows Data -- 15GB
/ : EXT3 -- 9 GB
/home : EXT3 -- 20GB
/mnt/Shared: EXT3  -- 80GB

I use the /mnt/"WHATEVER" to mount my internal drives. /media i use for my external drives. I think it keeps it clean that way. Its just a personal preference. In fact I had my shared drive mounted at /shared previously, but then I changed it to /mnt/Shared.

I have given you the sizes of each partition to get an idea, you can certainly have different sizes depending on your needs

Hope that helps

Oh and I use ntfs-3g and ext2ifs without any problems between Ubuntu and Vista

Thanks! Is there any advantage to /mnt/shared over /shared?

---

### Post by Inxsible on 2007-06-22
> **Brian96 said:**
> Thanks! Is there any advantage to /mnt/shared over /shared?

No "advantage" except for the fact that to me it looks cleaner that all my internal drives are mounted under /mnt and all my externals under /media. That way I dont have to play around with permissions for other folders / drives. I simply give myself full permissions for all folders under /mnt and /media

---


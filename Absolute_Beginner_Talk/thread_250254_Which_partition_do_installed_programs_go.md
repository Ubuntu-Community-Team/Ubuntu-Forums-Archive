---
title: "Which partition do installed programs go?"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by gannina on 2006-09-03
Hi, I am a new linux user. I'm just trying to figure out which linux partition installed programs go to. I'm also not exactly sure what the /home directory is supposed to store, and how big to make it. Any help is appreciated, thanks.

---

### Post by meng on 2006-09-03
The /home directory stores documents and configuration settings for individual users. Think of it as the Linux equivalent of Windows' "Documents and Settings". As for where in the filesystem programs are installed, it is variable, sometimes in /usr/local, /usr/local/games, /opt, and these may not be in separate partitions, it just depends how many partitions you created and for which mountpoints.

---

### Post by Gerr on 2006-09-03
Most new linux users don't need to worry that much about the size of the partition or where programs will be installed.

A good rule of thumb is as follows:

make /boot about 100M; setup a partition that is 2x the physical RAM for swap (I tend to max this out at 2G even if I have more physical memory); use the rest for / (which will include /home).

This way, you can get up and running without many initial headaches or confusion. Why make a /home partition? Is there a specific reason you might want to do this? 

The answer to that question typically comes on a personal level. Some people might make a /home partition to enforce quotas or to utilize special filesystems or filesystem traits (like notification of file changes--beagle likes this). Others might make a home partition for breaking the disk out into individual backup points or for meeting their RAID requirements. 

You're filesystem use milage may vary and you won't really know how much space you use until you start using the system. Don't sweat the small stuff, yet. After you're up and running, you can use "du -shx" to get the count of files in your directories.

---

### Post by gannina on 2006-09-03
I have a 34GB hard drive I want to dual boot with. How big do you recommend I make the /home partition? When I install Ubuntu people only recommend 3 partitions, a linux root, /home, and a swap. Do I have to manually create /usr, /bin, etc? Or are those created automatically by Ubuntu? Also, do those other directories go on the root partition? I'm trying to figure out how much space each needs.

---

### Post by gannina on 2006-09-03
So I guess application files and saved files can go somewhere on the linux root partition, and I don't really need to bother with a /home directory. Thanks for the help.

---

### Post by zappafrank on 2006-09-03
You only need one partition to run linux, and that will be the root partition. Any directories the system needs will be created in there. (an additional swap partition is also recommended)

However, you may want to customize things. A seperate /home partition is of good use, as you can just re-mount it after you reinstalled your system, or even after you changed distributions, you can even share it between different distributions you have installed at the same time. 

Don't bother with the /boot partition, it's not so important anymore nowadays, except if you use special filesystems.

---

### Post by Omnios on 2006-09-03
> **gannina said:**
> I have a 34GB hard drive I want to dual boot with. How big do you recommend I make the /home partition? When I install Ubuntu people only recommend 3 partitions, a linux root, /home, and a swap. Do I have to manually create /usr, /bin, etc? Or are those created automatically by Ubuntu? Also, do those other directories go on the root partition? I'm trying to figure out how much space each needs.


 One inportant question you might ask your self is how small you can shrink your windows drive and still have it useable and room to grow. A very popular topic is poeple keeping a big win partition and then later on asking how to shrink it even smaller. My XP partition whent from 50gigs down to about 30 as I have a 9gig game on it.

---


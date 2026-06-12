---
title: "Must have partitions"
date: 2012-05-30
forum: Any Other OS
---

### Post by tech291083 on 2012-05-30
Hi,
 
I often try different Linux distros (Debian based, RPM based and so on). But I am still to understand as to which partitions one must have to install a particular distro? I want to know this as I often create partitions manually using GParted Live CD.
 
Should I always create a /boot partition to install Grub there?
Is it always necessary to have a /home partition?
If I do not have a /home partition will the system work?
Is it ok to not create a separate /boot partition and instead install Grub to / partition?
 
 
Thanks

---

### Post by Megaptera on 2012-05-30
I follow this guide and find it works fine [http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/](http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/)

seperate /home not essential but is useful for reinstalls as all settings, docs, pics, tunes etc still there (along with your backup of contents of /home on seperate external storage media of course!:p )

---

### Post by ratcheer on 2012-05-30
I share the same swap partition between all my installed Linux systems (2-Ubuntu, Sabayon, Arch, and Siduction). So far, this has never caused a problem.

I prefer separate /home partitions, but as has already been said, it is not necessary.

Also, I do use a /boot partition, but that is only because my disk uses GPT partitioning, which allows me to have up to 128 primary partitions. I used MBR partitioning for a long time with no /boot, and that never gave any problems.

Tim

---

### Post by tech291083 on 2012-06-03
> I prefer separate /home partitions, but as has already been said, it is not necessary.

I need to know this, thanks.

---

### Post by ratcheer on 2012-06-03
> **tech291083 said:**
> 
Considering the above situation, if I have a 100 GB hard drive how much space  should I allocate to each of the following partitions? Typically, I would allocate as  follows.
 
swap - 5 GB
/home - 80 GB
/root - 10 GB
/boot - 5 GB

Am I right with my plan here? Thanks.

I would increase / to around 16 GB, though 10 may be adequate. And I see no reason for such a large /boot partition. I think 1 GB would be way too much. Mine is 300 MB.

Tim

---

### Post by LiamOS on 2012-06-04
My partition scheme on my netbook is as follows:

/boot ¦ 300M 
/     ¦ 50G  ¦  For my Lubuntu-based installation.
swap ¦  6.7G 
/    ¦  20G  ¦  For Gentoo
/var  ¦ 10G  ¦  Gentoo
/usr  ¦ 20G  ¦  Gentoo
/home ¦ 143G ¦  Mounted as /home by whichever OS is running.

My partitioning for Gentoo is still a work in progress, and I think in future a small / and slightly larger /var would be a bit better for me.
Also, /boot doesn't need to be big at all, as rat said. On my old box with Gentoo, my /boot is 100M with plenty of room to spare.

---

### Post by anaconda on 2012-06-04
Matter of opinion.

Only partition you need is the root partition "/"

And if you have windows or multiple linuxes on the same machine then a separate /boot partition is a good idea. (So that if you break your linux installation  you can still boot to the other systems.)

You dont need a swap partition. You can create swap files after installation. They are as fast than separate swap partition. If you have many linux installations on the same machine, then swap partition is a good idea, because all of those can use the same swap partition. Saves space.

Personally I prefer not having a separate /home partition. Instead I have a separate HD for all my data. 
I like this better than keeping my data on /home, because there are lots of unnecessary stuff on /home...  config files, cache etc. which I dont want to save when reinstalling everything.

---

### Post by Habitual on 2012-06-04
I set aside 20G for /
2G for /swap
rest for /home

---

### Post by tech291083 on 2012-06-07
I have a simple question. If I have a hard drive with 100 GB of total  space and  want to install a particular distro using the - Use the  entire hard drive space - option during installation and create the  following partitions manually. Although many of you will say that I do  not need to create a particular partition (/home etc.) But I will still  do it because I want to get more comfortable with partition creation.

swap - 5 GB
 /home - 80 GB
 /root - 10 GB
 /boot - 5 GB


Now I want to install so many different packages just out of curiosity.  So how much space do I need to give to /root and /home partitions? I am a  bit confused as to where do all the packages get installed? /root or  /home? Which one should be bigger in size in my case? I am the only user  of the system. No one else is going to use this pc. Please guide me  based on your experience with different distros, thanks a lot.

---

### Post by oldfred on 2012-06-07
Applications are installed in / (root), but settings & all your data are in /home. With a 100GB drive I might use 15GB for /. I normally suggest 10 to 25GB for root depending on space you may want.

Partitioning is personal as only you know how you will use system. I find my own optimal partitioning is not so good a couple of years later as what I am doing has changed.

I do not suggest the separate /boot for most desktops as it is unnecessary. But separate /boot may be required for older systems with a 137GB boot limit set in BIOS, or RAID or LVM which are more common on servers. Newest grub also has drivers for LVM and RAID so separte /boot is not always required now.

I normally install to a 25GB / partition and with /home included use about 7GB with lots of applications. But sometimes like writing a DVD you may want /tmp to store 4GB for the DVD so you often need some working room. 

I am aggressive about moving data outside my /home to my data partitions and have multiple installs, so I keep /home inside /. So I want a data partition that I can mount in all my installs. A separate /home is good if you want to reinstall to the same / partition but preserve all your data & settings.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by tech291083 on 2012-06-08
> **oldfred said:**
> Applications are installed in / (root), but settings & all your data are in /home. 


Thanks a lot, I need to know this well for future.

> With a 100GB drive I might use 15GB for /. I normally suggest 10 to 25GB for root depending on space you may want.
I understand your point of view here.

> Partitioning is personal as only you know how you will use system. Yes, now you get my point. As stated earlier I want to use my pc as an experimental system where I can possibly download all the packages to try them out and and learn something in the process. This might sound crazy, but I just want to make it clear as to what my system is going to be used for. A little bit of programming so I will need all the different IDEs for different languages, editors, games, video editors, and so on. The list is endless to say the least. I am the only one who is going to use this pc/system so I am not much bothered about settings etc. Although it is a valid point.

I am not going to store personal data of any sort on this drive say pics, videos, documents etc. Only I want to install new packages all the time.

I have just purchased a 500 GB hard drive and I will use it to install Ubuntu 12.04 LTS or some other distro. But I will use only one distro at a time and that too will occupy the whole space on the hard drive ie 500 GB. The 100 GB space hard drive mentioned earlier was meant to be an example only, so that I can an idea as to what % should be given to /home and /root.

Please guide me, thanks.

---

### Post by oldfred on 2012-06-09
Unless you have some games that are steam or something, you can install a lot of applications in a 25GB / (root). If drive is larger then I normally suggest 25GB even for 2TB drives. Also better to have the most used software somewhat together on drive but still have working room. An Arch site suggested 25% used and I find my installs use about 7GB including /home and all data in other partitions. I have a lot of applications in my 7GB installs.

When I got my 'new' 650GB drive about 2 years ago I started installing with 25GB root and two 100GB data partitions one NTFS for sharing with XP and the other ext3. But I left some of the drive unallocated and just kept using another 25GB for another install. I can still boot most of the old installs, but will some start reusing. But my newest installs are now on a new SSD which boots very fast.

---


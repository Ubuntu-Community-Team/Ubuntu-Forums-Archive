---
title: "1 More Partitioning question"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by Bigguy2468 on 2006-09-05
During the installation there are 3 options for install. One was to erase the entire drive, not good for me. One was to free space on the existing drives.

If I already have a swap and Linux partition being used for another distro. Will ubuntu erase that distro and use the partitions or create even more separate partitions?

---

### Post by xyz on 2006-09-05
Use FREE SPACE...meaning that it'll determine and use what free space you've got; it won't erase anything as its only concern will be to create a new partition using ONLY your free space and...free space is obviously empty.
Hope this is what you meant!

---

### Post by n00b@linux on 2006-09-05
You *will* need to specify a separate partition upon which to mount (ie. 'install') the root ('/') directory for Ubuntu. The automated installer may suggest using separate partitions to mount other directories eg. /usr, /home, /etc. You don't need to do this. If you delete those options and just leave the '/' option selected for formatting then everything will be mounted on the '/' (ie. root) partition.
 
You can specify your existing swap partition to be the swap partition for your new Ubuntu install.  Doing so won't 'overwrite' anything, as a swap partition is used solely for temporary storage, ie. there won't be anything permanent on the swap partition that your other distro would want to use.

---

### Post by Bigguy2468 on 2006-09-05
OK, so the 3rd option was to manually determine where everything is going to be mounted and this is the method that has always concerned me the most.

When I went to the manual partitioning screen before it showed a graph displaying partitions, type and size on the hard drive. You are suggesting to mount ubuntu on the / root directory. Is that also where the MBR (Master Boot Record) is locate because LILO from Mandriva 2006 is currently there and I need that overwritten so as not to have 2 Bootloaders trying to over ride each other.

---

### Post by Paul133 on 2006-09-05
First off, do you only have one HD? Secondly, what are your partitions now? And thirdly, what OS's do u intend to dual boot, Suse and Ubuntu? I think I can help you; you definitely want to do the 3rd option. And do NOT put the Ubuntu parition over the MBR! That's where GRUB (or LILO) will go. The Ubuntu  root partition will just be a ext2/3 partition.

---

### Post by Bigguy2468 on 2006-09-05
> **Paul133 said:**
> First off, do you only have one HD? Secondly, what are your partitions now? And thirdly, what OS's do u intend to dual boot, Suse and Ubuntu? I think I can help you; you definitely want to do the 3rd option. And do NOT put the Ubuntu parition over the MBR! That's where GRUB (or LILO) will go. The Ubuntu  root partition will just be a ext2/3 partition.

1. Yes, I am only dealing with one HD

2. Right now they are for Windows XP and Mandriva 2006 December Addition

3. Windows XP and ubuntu

If I choose /root to mount ubuntu will I still get the option during the installation process on where to mount GRUB?

Thanks!

---


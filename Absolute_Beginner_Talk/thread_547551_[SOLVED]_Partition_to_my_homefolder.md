---
title: "[SOLVED] Partition to my homefolder"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by brunoskrebs on 2007-09-10
hello,

I am wondering what is the best way to make a partition to use as my home folder? I mean, I am going to use this partition as the home folder for my user in linux and in windows xp as well. Unfortunately I still use the Microsoft OS.

And how does it work the permissions in files when you switch between one OS and other?? Does the windows respect the permission that comes from linux?? Or it just ignore it?

Thank you very much,
Bruno Krebs

---

### Post by mikeyphi on 2007-09-10
If you just need to access your working data in either OS - then there's no special requirements. Windows and Ubuntu can be setup to read/write your personal data when working in either OS.

---

### Post by BrendanM on 2007-09-10
There are basically three ways to do this.

Option 1) Make the home partition with the FAT32 file system. Both Linux and Windows can read FAT32 partitions natively. There are some disadvantages with this option, the biggest drawbacks being a 4 gig file size limit and fragmentation issues.

Option 2) Make the partition NTFS and install NTFS-3G so you can write to the partition from Linux.

Option 3) Make the partition ext3 and install the ext2fs driver in Windows so Windows can read/write the partition. Windows will NOT respect Linux file permissions.

---

### Post by vanadium on 2007-09-10
You should not move your home folder to a windows folder. Instead, create (symbolic) links to your user data directories that are stored on the Windows partition. This way, the data that you see under Windows will appear to be (and effectively be) available in your Linux home folder. 

You won be able to use nautilus to create the links, though. Indeed symbolic links can only be created on volumes that support these. The command you can use is

ln -s <what_to_link> <location_and_name_of_the_link>

For example, if your Windows partition is mounted under /media/win, you could create a link to the directory "c:\Documents And Settings\User\My Documents\Letters" in your home folder with the command

ln -s "/media/win/Documents And Settings/User/My Documents/Letters" ~/Letters

---

### Post by brunoskrebs on 2007-09-10
So the case is that I want a partition that is not on linux not even on windows. But that both access it. In the future I am thinking about installing another distro of linux in my harddisk to learn others distros to. And I will want to access from this other distro my home folder too.

So what do you think it would be better for me to do??

Thanks again.

Bruno Krebs

---

### Post by mlentink on 2007-09-10
See BrendanM, post #3.

I would go for option 2, I have more trust in Ubuntu writing to a native-Windows partition than vice versa....

---

### Post by hyper_ch on 2007-09-10
mlentink:

Actually I have more trust in an OS driver (ext2/3) that works in Windoze than a back-engineered windoze driver that works in Ubuntu

I'd do (3)

---

### Post by brunoskrebs on 2007-09-10
ok, I think I`ll do the ext3 partition as you said.

Thanks for the help of everybody...

---


---
title: "Partitioning and installing Windows"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Shadowfang36 on 2008-03-16
I currently have a 500gb hard drive dedicated solely to Ubuntu. I wanted to know how I would go about partitioning about 50 gigs of space so I could install windows XP. Also, after XP is installed, is there a way to share files between XP and Ubuntu?

---

### Post by wheredidrealitygo on 2008-03-16
Gparted (in the repos) is an awesome partitioning tool, easy to understand and use, it can shrink your ext3 (or ext2) partition of Ubuntu so you can make a new Windows partition.

Ubuntu can natively read/write to fat32, Gutsy comes with ntfs-3g by default so you can read/write to Windows from Ubuntu, and I know there are filesystem drivers for Windows so you can *read* Ubuntu from Windows, but I'm not sure about writing.

---

### Post by handydan918 on 2008-03-16
> **Shadowfang36 said:**
> I currently have a 500gb hard drive dedicated solely to Ubuntu. I wanted to know how I would go about partitioning about 50 gigs of space so I could install windows XP. Also, after XP is installed, is there a way to share files between XP and Ubuntu?

What kind of XP disk do you have? If it is a real XP disk, then you should be able to install it to an existing ntfs partition. If it is a restore disk, you may have a problem. It may just decide to hose your Ubuntu installation. So make sure you have it all backed up, first. 
You can create the ntfs partition with gparted from the live cd.

---

### Post by Shadowfang36 on 2008-03-16
I just tried using GParted and I selected my ext3 and the option to resize partition was locked.

Also, there is a padlock icon next to the partition, does this mean that I dont have access rights to this? If not, how do I identify myself as administrator?

---

### Post by bsharp on 2008-03-16
GParted wont do anything if the drive is mounted, so you need to boot from a live cd and run it.

---

### Post by bluewraith on 2008-03-16
I've not used the version from the repos, but if its command line use "sudo" at the beginning of the command.

Simple way to share files between Ubuntu and Windows would be to create a fat32 partition as a sort of "middle man". You'll have your Ubuntu Partition, your Windows partition, and then your file dump partition. (as well as your swap and pagefile partitions, of course)

---

### Post by jken146 on 2008-03-16
NTFS is a much better file system than FAT32, so use that instead.  Ubuntu can read and write to NTFS, and if you have Ubuntu 7.10 (Gutsy Gibbon) you won't have to do anything to make this work.

[http://fs-driver.org](http://fs-driver.org) has some drivers for reading and writing to ext2/3 in Windows.

As for partitioning, you can't change a partition while it's mounted (in use) so you'll have to use a live CD to make the changes you need.  Be sure that you have enough free space to do the shrinking you want, and if you have important files, back them up first!

After you install Windows, you'll find that you can't boot into Ubuntu.  See here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---


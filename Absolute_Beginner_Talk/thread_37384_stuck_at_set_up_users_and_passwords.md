---
title: "stuck at set up users and passwords"
date: 2005-05-27
forum: Absolute Beginner Talk
---

### Post by pravit on 2005-05-27
Hello,
I'm new to Linux, tried the Ubuntu Live CD and liked it, and decided to set up a dual boot system on one of my other computers to play with. I'm kind of confused as how to set up the partitions. I gave WinXP 1.5GB of space, and I set a 3GB partition for installing Ubuntu into. Then I put the remaining ~25GB as a FAT32 partition, so I can access files from both OSes. I also have a 1GB swap partition. Anyhow, I began installing Ubuntu, and I'm stuck at the part "Set up users and passwords." I type in my username, password, and then it sends me back to make a new username again. I've tried this several times and I'm sure I'm not misspelling my password. What do I do? I found another thread about this, but I don't understand half the stuff there(I'm completely new to Linux). If anyone could walk me through this, I'd really appreciate it.

I went on with the installation, hoping that it created my account somehow, but now it's telling me that I entered nothing for the password and that group "pravit" does not exist...

Here are the threads about this I found. From what I understood I have to start over again and repartition things correctly. Can anyone help me set up my partitions so I can access files from both OSes?
[http://www.ubuntuforums.org/showthread.php?t=16507](http://www.ubuntuforums.org/showthread.php?t=16507)
[http://www.ubuntuforums.org/showthread.php?t=1864](http://www.ubuntuforums.org/showthread.php?t=1864)

EDIT: By the way, does anyone know how I can disable my touchpad and touchpad buttons while using the Live CD? I'm on a laptop right now and I keep accidentally tapping the touchpad and going all over the place.
Pravit

---

### Post by TripHammer on 2005-05-27
Well it seems to be that your /home directory is on that fat32 partitions....so it you may have partitioned the disks but the file directories not being mounted in the right place.

When partitioning you need something like:

/dev/hda1
1.5gb
ntfs
mountpoint: /windows

/dev/hda2
25gb
fat32
mountpoint: /files

/dev/hda3
1gb
swap

/dev/hda4   
3gb
ext3
mountpoint: /

/dev/hda5
100mb
ext3
mountpoint: /boot

Also, since you are dual booting (can be challenging for new users) when it asks you if you want to install gub on the MBR (master boot record) say yes.

---


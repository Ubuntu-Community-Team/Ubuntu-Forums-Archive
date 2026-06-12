---
title: "How are application files organized?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by bdemers on 2008-02-18
I realize that this will have exceptions, but what I'm trying to do is get a good feeling for how files are distributed when an application is installed.  What I am aiming at is using xen to set up linux-only vm's on a machine with 4 18G hard drives, that I really would like to use in a raid 1 fashion(possibly raid 5), thus reducing my storage by half.  I would like to consider a separate storage array for user unique files, such as the home directory.  I would like to consider using a separate container for all common files, files that have absolutely no differences for each user.  This would reduce redundancy and storage space. At this point I question if such an arrangement is practical.  When I view the directory structure, I see what appears to be files for any given app, placed in a variety of areas.  I am sure that a better understanding would demonstrate that the placement of these files is very well thought out, no argument with that at all.  What I'm questioning is what is the impact when I separate these files over a variety of volumes?  Maybe I should consider using logical volume management for all of the storage that isn't on the xen/raid machine, so that I only have to consider a single boundary - that being the vm's os on one side and all of the other files on the other?

If any one has comments that will help me figure out what I can/cannot do, my appreciation to you.

---

### Post by randy78 on 2008-02-18
> **bdemers said:**
> I realize that this will have exceptions, but what I'm trying to do is get a good feeling for how files are distributed when an application is installed.  What I am aiming at is using xen to set up linux-only vm's on a machine with 4 18G hard drives, that I really would like to use in a raid 1 fashion(possibly raid 5), thus reducing my storage by half.  I would like to consider a separate storage array for user unique files, such as the home directory.  I would like to consider using a separate container for all common files, files that have absolutely no differences for each user.  This would reduce redundancy and storage space. At this point I question if such an arrangement is practical.  When I view the directory structure, I see what appears to be files for any given app, placed in a variety of areas.  I am sure that a better understanding would demonstrate that the placement of these files is very well thought out, no argument with that at all.  What I'm questioning is what is the impact when I separate these files over a variety of volumes?  Maybe I should consider using logical volume management for all of the storage that isn't on the xen/raid machine, so that I only have to consider a single boundary - that being the vm's os on one side and all of the other files on the other?

If any one has comments that will help me figure out what I can/cannot do, my appreciation to you.

Check Here: [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

---

### Post by justleen on 2008-02-18
for *nix it doenst matter wether a path is a folder on a drive, a mounted LV / partition / disk.
So, yes, you could use a disk for /usr one for /usr/lib, etc

But, the directory structure on *nix is already made to be as redunant as possible. All user file go into /home, all boot files /boot, application data /usr and /lib, log and cache to /var, settings in /etc and so on  (roughly!)

so if i read your question correctly, yes, there is no problem at all to asign seperate mount so specific folders.

check out[ this guide]("http://tldp.org/HOWTO/html_single/Partition/"), point 4.3...

LVM wil grant you the extra advantage of being able to resize disks, when you run out (or shrink when you realize you got a lot of unused diskspace), but it its not neccesary for what you want...

---


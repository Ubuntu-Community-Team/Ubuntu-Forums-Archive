---
title: "Server vs. Desktop version questions"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by macrogeo on 2006-02-17
I plan to use PHP, MySQL, and Apache to develop and test a website(s).  Will the desktop version suffice?  Is it also OK to install both server and desktop versions on different partitions of a hard drive?  How much disk space is considered useful for the server (say 10 hits per day)?  Thanks!

---

### Post by alamba on 2006-02-17
Unlike windoze, ubuntu's desktop and server version differ only by the default set of applications installed. Desktop version will give you a GUI to boot into (GNOME or KDE). Server version would not.  Having said that, you can install any package in any version and use it, i.e. apache, PHP, MySQL, etc. would work on both. 

I personally don't see the point of installing both in different partitions of a drive. 

I'm not sure how u're equating hits to server HDD space.

A

---

### Post by heimo on 2006-02-17
[quote=macrogeo]I plan to use PHP, MySQL, and Apache to develop and test a website(s).  Will the desktop version suffice?  Is it also OK to install both server and desktop versions on different partitions of a hard drive?  How much disk space is considered useful for the server (say 10 hits per day)?  Thanks![/quote] 
If you're going to develop on the same computer that works as a server, you can install the desktop version and add servers you need. Server install is basicly same as Desktop install, but naturally without desktop. It doesn't even install any servers.

How much space is needed depends on what you're going to do with it - serving .iso files is a bit ;) different from serving small text files. You probably need 2-5GB for the system and rest for /home. If it's decent sized disk, I would probably choose manual partitioning during setup and make 5GB for / partition, 10GB for /var (this is where your website resides) and rest for /home (and one 512MB-1GB partition for swap).

If it's modern computer, it can serve somewhere around 10-200 static html pages a second. Not going to argue about exact numbers (too many variables), but just saying that even if it was a 486sx/25MHz with 8MB memory, you could install Linux (other than Ubuntu) on it and it could handle at least thousands of hits per day.

---

### Post by macrogeo on 2006-02-17
Thanks for your clarifications and insights.  I just attempted but failed (a couple of times) to resize my NTFS partition using hermanzone's excellent Ubuntu Dual Boot Home Page's Ubuntu + NTFS instructions.  I think this is due to some sort of setting(s) in Windows XP Home or the BIOS on my Compaq Presario 2568CL laptop.  Any suggestion?  I am now considering getting and installing it on a USB hard drive.

---


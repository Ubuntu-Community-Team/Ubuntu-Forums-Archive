---
title: "Windows + Kubuntu: Play nice with shared media?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by brettg102 on 2008-02-06
Hello all! I've recently made the jump to Kubuntu on my laptop (love it!), but am hesitant to do so on my desktop. Here's why...maybe you all can assuage my fears.

I am currently running Vista Business Edition on the desktop. I have two hard drives, one for OS + Programs, one for media. Of course, that media hard drive is formatted to run with Windows.

Here is my plan: Dual boot Kubuntu and Vista by partitioning C:/, and keep the media harddrive totally untouched. First of all, can I do this (will Kubuntu touch the media hard drive on install?), and second of all, assuming I can get this install done; will Kubuntu play nice with that media harddrive (meaning, will I be able to access and play all my media as I can currently on Windows), or is it going to go haywire on me for being a Windows Filesystem on the media drive? Alternatively, is Windows going to continue to run and access that media drive as usual.

Losing access to the media makes it a no-deal on the desktop...make me confident to switch.

---

### Post by ubutufan on 2008-02-06
as you said you plan to install kubuntu on one drive. you are not doing anything to the media drive.

kubuntu or ubuntu will be able to deal nicely with media files of any sort.

---

### Post by Liet_Kynes on 2008-02-06
Which version of Kubuntu are you running? I understand Gutsy has read/write NTFS access by default. Which would mean that it would be able to access your media drive and also write to it.

I'm using Feisty and prefer to mount all my ntfs partitions as Read Only. That means that I can access all my media but not change anything on those drives.

When you install on the desktop you might want to unplug the Media harddrive just to avoid accidentally installing anything on it.

---

### Post by brettg102 on 2008-02-06
Thanks for the quick replies guys! Another reason the Linux community is the best!

I'm going to install Gutsy, so that is a nice feature with the NTFS.

I would like to do as you said, and make them read-only on the Kubuntu end...is that as easy as a tickbox check/uncheck or will it involve some chmodding?

---

### Post by Liet_Kynes on 2008-02-06
I put it in my /etc/fstab file

```
sudo vi /etc/fstab
```

Then I add the following line/s depending on your hardrives

[HTML]/dev/sda1       /media/windows  ntfs    user,ro,nls=utf8,umask=0222      0       0[/HTML]

This automatically mounts My ntfs partition as read-only in Ubuntu undee the /media/windows directory

---


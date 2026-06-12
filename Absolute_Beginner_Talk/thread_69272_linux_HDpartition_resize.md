---
title: "linux HD/partition resize"
date: 2005-09-26
forum: Absolute Beginner Talk
---

### Post by cburg on 2005-09-26
I asked this question slightly differently on this forum last week but didn't get a usable answer, so I am going to try again:

I have WinXP (FAT32) on my first HD (20 GB) and Ubuntu 5.04 on the second HD (13 GB). It dual boots to either OS using grub with no problems. Windows doesn't recognize the second (Linux) HD anymore. Is there an easy way for me to tell how much space is left on the Linux HD? If there is enough space left on that HD, can I give some of it back to Windows, and if so, how?  I have tried to research this and it looks like I could also share some FAT32 space on the Linux HD that would make files there accessible to both Windows and Linux.

I have had 5.04 for a few months but haven't done much with it so I could reinstall it if necessary.  I have the ISO disk.  I don't know how to tell if I have a partitioning program (gparted?).  I also don't know how to use it if I do have it or download it if I don't have it.

I have backed up my Windows files from the Windows HD but I really don't want to lose anything there.  I am new to this and I would like to do something easy and successful to help build my confidence.

Thanks in advance - dale

---

### Post by Ampersand on 2005-09-26
You can find out how much disk space you've got on each partition by running 'df' in a terminal. You can get gparted by either using the Synaptic package manager or running 'sudo apt-get install gparted' in a terminal.

---

### Post by NeoSNightmarE on 2005-09-26
And if you want disk space in a easier to read format, you can run 'df -h' in terminal. Breaks it down better.

---

### Post by cburg on 2005-09-27
Thanks for your help.  To df -h I got the following:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1             6.3G  1.5G  4.5G  25% /
tmpfs                 185M     0  185M   0% /dev/shm
/dev                  6.3G  1.5G  4.5G  25% /.dev
none                  5.0M  2.9M  2.2M  57% /dev

I think this means I made the Linux partition 6.3 GB (out of a total of 13GB for this drive) when asked at install, which I vaguely recall doing.

When I tried the apt-get command I got the following:

~$ sudo apt-get install gparted

Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package gparted

There's probably something simple I can do to get the program but as a beginner at this, I am stumped.  BTW, I tried it twice.

Assuming I eventually get gparted, can I use it to make some space available on this HD to backup some of my Windows and Linux files?

Thanks - Dale

---


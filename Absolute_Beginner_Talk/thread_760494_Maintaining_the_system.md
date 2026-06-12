---
title: "Maintaining the system"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Zubatron on 2008-04-20
Now as I have recently come from windows, I was used to doing disk clean up, disk defrag and running virus scans and etc...

Now is there anything similar I should do in Ubuntu? I run 7.10 and I've had it running for a good month or so. So is there anything I should be doing to maintain the system? I always do the system updates. Anything else?

---

### Post by george9233 on 2008-04-20
There is a "Virus Scanner" in the repository, you can find it in "Add/Remove...", but there is much less virus in linux than in windows.

You can search yourself in Synaptic, just press "Search" and choose "Description and Name" in "Look up", and type in the box like "disk defrag".

---

### Post by ELF_O8 on 2008-04-20
The great thing about Linux is there is hardly ever a need
to do those old-fashioned things that you need to do in 
Windows to keep the system running properly.
Linux is much more stable and there are hardly any viruses.

---

### Post by Dr Small on 2008-04-20
Ubuntu is running on an ext3 filesystem, so defragmenting the filesystem is not neccessary like on Windows NTFS. Usually every 20 or 30 boots, fsck will begin to check your filesystem for errors.

Virus scans are un-needed, as Ubuntu is not prone to Windows viruses and there are very few (proof of concept) viruses for Linux in general.

Overall, there is not much you need to do to maintain the system. It does a fairly good job doing it, itself :)

Dr Small

---

### Post by chewearn on 2008-04-20
There is usually no need to do any cleaning up, unless you are in dire need of extra harddisk space.  You can run:
```
sudo apt-get autoclean
```
to clean out old packages.

There is no need to defrag unless you have a fat32 partition lying around.  There is no need to check for virus.
 
You can clean out your browser's cookies and cache.


Mmmm, I wonder if I can suggest Ubuntu to include a program that let's users get busy in Ubuntu.  The program could *pretend* to defrag, scan and clean the harddisk.  :lol:

---

### Post by sayakb on 2008-04-20
The ext3 filesystem does not need defragmenting. Disk check is performed every 21 times (or something like that) you boot into Ubuntu. You don't even need a virus scanner, though you might download Avast antivirus from avast.com or install ClamAV from the repos

EDIT: Seems like Dr Small beat me on that :D

---

### Post by lswest on 2008-04-20
> **george9233 said:**
> There is a "Virus Scanner" in the repository, you can find it in "Add/Remove...", but there is much less virus in linux than in windows.

You can search yourself in Synaptic, just press "Search" and choose "Description and Name" in "Look up", and type in the box like "disk defrag".

About the virus scanner, it only scans for Windows viruses, and is useful if you (frequently) share files with a windows network/computer, so that you don't transmit a virus to those windows computers, otherwise no, none of the programs you mentioned above are required for Linux on ext3 partitions apart from disk checks which get run automatically after a certain number of reboots.

---


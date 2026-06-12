---
title: "Ubuntu and NTFS"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by GeordieJedi on 2008-04-11
Hi all. How is everyone? Well I hope?

Sorry if this is a no brainer, but I could use the help...

I currently dual boot between XP and Ubuntu 7.10
and have a FAT partition on my 2nd internal disk, to share my files between them both.
 
Ive just bought myself a nice shiny 500GB external harddrive. And Id like to use it to
store my data (and also share it with XP - It'd be nice to have 1 place to store all of my
pics, docs, vids, from both OS's). The dirve is all NTFS at the moment,
Ive allocated 100GB to use as the share. So does anyone know what NTFS writing is
like, on a day to day basis? Is it safe for my data?

Any help would be greatfully appreciated.

Cheers

---

### Post by mgranet on 2008-04-11
I have a similar setup (400GB in NTFS for mass storage), and I've never experienced any problems whatsoever. I feel confident keeping my important data on there, without worry of corruption.

---

### Post by Achtung on 2008-04-11
I've used a NTFS external HDD for backups for a couple months and I have not run into an error for the 6 months or so while I was using this setup. 

Install ntfs-3g and ntfs-config if you don't already have them installed to get access to the NTFS drive. 

You could also format the external HDD to Fat32 if you're that worried.

---

### Post by GeordieJedi on 2008-04-11
Thanks very much, Achtung's and mgranet.

Cheers for the advice and the prompt replys.  Its much appreciated.

Take it easy.

---

### Post by indytim on 2008-04-11
You've now got the luxury or going either way.  There is a utility that can be installed on the windows side to allow access to the ext3 mounted drives.  You also have the option on Lx to now read-write to NTFS.

For example, I have a 320G SATA internal with multiple partitions.  In the 5% of the time I'm on Windows, I have my ext3 partitions mounted with my multi-media folders/files.  I freely work the windows apps save to these folders as required.  Obviously, all of these partitions,folders and files are totally accessible on the Lx side.

As I said, there is a feature in Lx that will allow you to read-write to NTFS partitions.  Unfortunately, I'm at work and duty-bound to Windows so i don't have the specific apps etc. for you.  Should be easy to find with a quick search of the forum(s).

My overall recommendation would be to use ext3 as a data storage vs NTFS.  It's more efficient.  FAT32 isn't a good option if you have files that are ~>4G.

IndyTim

---

### Post by stchman on 2008-04-11
> **GeordieJedi said:**
> Hi all. How is everyone? Well I hope?

Sorry if this is a no brainer, but I could use the help...

I currently dual boot between XP and Ubuntu 7.10
and have a FAT partition on my 2nd internal disk, to share my files between them both.
 
Ive just bought myself a nice shiny 500GB external harddrive. And Id like to use it to
store my data (and also share it with XP - It'd be nice to have 1 place to store all of my
pics, docs, vids, from both OS's). The dirve is all NTFS at the moment,
Ive allocated 100GB to use as the share. So does anyone know what NTFS writing is
like, on a day to day basis? Is it safe for my data?

Any help would be greatfully appreciated.

Cheers

I have been using the ntfs-3g package for some time with no problems.

I would recommend using the UUID method in your fstab to mount the external drive with ntfs-3g.  The UUID will make sure the drive is mounted in the correct folder.

---

### Post by GeordieJedi on 2008-04-17
Hi, again. Well things seem to be going well with my new external drive.

I do have a new question however....

My Current set-up = 

Internal HD 1 =

C: 50GB Windows main OS
E: 60GB NTFS (now being used for apps and spare data for XP)

Internal HD 2 =

Part 1 = 50 GB EXT3 - Linux   root
Part 2 = 50 GB EXT3 - Linux  /Home
Part 3 =  2  GB EXT3 - Linux  /swap
Part 4 = 18 GB FAT32 - Shared space for both XP and Linux *

But the problem is, when I boot into Linux. It cant "see" the 4th partition.

When I do my fresh re-install of Linux What do I set the mount point
of the 4th partition? Do i set it as Windows or DOS or not at all?

Thanks for all the help, its appreciated.

---

### Post by logos34 on 2008-04-17
This should help:
[http://www.psychocats.net/ubuntu/mountwindows#fat32](http://www.psychocats.net/ubuntu/mountwindows#fat32)

---

### Post by GeordieJedi on 2008-04-21
Thanks very much. Once again. Very much appreciated.
:-D

---


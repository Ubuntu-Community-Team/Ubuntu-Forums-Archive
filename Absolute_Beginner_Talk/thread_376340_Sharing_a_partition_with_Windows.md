---
title: "Sharing a partition with Windows"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by man-man on 2007-03-04
First off, I don't mean "can I install both on one partition" - that would be silly

Is it possible to have one partition that Ubuntu uses as a /home partition and Windows uses as a separate partition for saving files - both would have their own partition to have the OS and programs installed to, there's an ext3 driver for Windows (or the NTFS drivers for Linux, but I'd prefer to use ext3) and I don't see why they should'nt be able to co-exist

However, when putting it into practice I ran into a few problems.

I started with a blank disk and used the live CD to format it with separate partitions for a Windows install (NTFS) a Ubuntu install (ext3) a home partition/file space (ext3) and a swap partion. Installed Windows first so that at the end of the process I would have grub as the bootloader, installed the ext3 driver, worked fine - was able to set things up so that My Documents and some other stuff (Start Menu, Desktop etc) was stored on the separate partition (named as E drive), no actual documents in there yet, but its set up

Then I installed Ubuntu, made that partition the /home partition, everything seemed to be working fine. Switched back to Windows and everything was not working fine - now it thought that the E drive was unformatted, I used the little utility that came with the ext3 driver to check that it was the ext3 partition that was assigned as E, it is, but Windows still thinks its unformatted.

because everything was kinda messed up and I couldn't be bothered to mess with the registry to set it up in a way I didn't want, I reinstalled Windows, reinstalled my programs and the ext3 driver (still believes it to be an unformatted partition so I removed the drive letter to stop it from asking to format drive E)

Is there any way to make this work, before I repartition to include more space for Windows to save files to?

Oh, and if there is a solution to the above, I may need some advice/links on re-instating Grub (repartitioning would end up with re-installing Ubuntu to get the space in the right places, so if the above *doesn't* work I won't need to worry about Grub)

---

### Post by hardyn on 2007-03-04
i have done something simlar, but not exactly the same, and it works really well for me...

i have the disk divided into 4 partitions:

1 - NTFS
2 - FAT32
3 - EXT3
4 - swap

i use the fat32 partition as my shared partition between ubuntu and windows, works really well for me.  but i did have to find a format utility to format a fat32 partition bigger than 32gb.
i have not enabled EXT3 support inside of windows, i just don't save much stuff to /home.

feisty will bring NTFS write support, which would be even better that what i am currently running.

---

### Post by man-man on 2007-03-04
hmm.. maybe this time I'll wait until both OSs are up and running before I set one up in the shared space..
no, wait.. that won't work unless I install Windows a 3rd time because its already decided that the potentially shared partition is unformatted

Maybe if I scrub the whole disk and start again, but with the linux install first so that the home directory is in place before I introduce Windows to it, then re-instate Grub at the end :-k

---

### Post by hardyn on 2007-03-04
i installed windows, installed ubuntu then went back and formatted the second partition from windows using a little utility; but i don't see why you coudnt format using ubuntu.

---

### Post by Mr. C. on 2007-03-04
> **man-man said:**
> Is it possible to have one partition that Ubuntu uses as a /home partition and Windows uses as a separate partition for saving files - both would have their own partition to have the OS and programs installed to, there's an ext3 driver for Windows (or the NTFS drivers for Linux, but I'd prefer to use ext3) and I don't see why they should'nt be able to co-exist


What real-world problem are you trying to solve?

You don't want to go this path- it is fraught with peril.

Maintain separate native file systems for each OS.  If you must share data across boots, create a FAT partition to store data.  

> **man-man said:**
> 
However, when putting it into practice I ran into a few problems.


As I said, don't go this route.

MrC

---

### Post by man-man on 2007-03-05
I'm trying to solve the problem that I have a lot of files (documents, pictures, music, videos - the full set) that I might want to access from either OS without having to duplicate them all and keep them on 2 separate partitions or keep remembering to move them back and forward

Whilst a FAT partition would do the job of being accessible by both, the limitations on volume size and file size would both cause me some problems (its a 320gb disk and I have several large files.

Since this disk doesn't yet contain any data its not a big issue to keep reformatting parts of it, I just want to know if what I'm trying to do is possible, or whether there's something inherent to putting home on a partition that makes Windows see an unformatted volume

Hardyn, I'll try doing stuff in that order

---

### Post by man-man on 2007-03-05
One other related thing, is it possible to install Ubuntu initially onto one partition then later tell it to move one directory (home) to another partition

Plus, I just noticed that the ext3 driver I'm using/planning to use says it is for x86 processors only, will this exclude 64bit (x86-64) processors, or do they still count as being x86?

---

### Post by Mr. C. on 2007-03-05
> **man-man said:**
> I'm trying to solve the problem that I have a lot of files (documents, pictures, music, videos - the full set) that I might want to access from either OS without having to duplicate them all and keep them on 2 separate partitions or keep remembering to move them back and forward

Whilst a FAT partition would do the job of being accessible by both, the limitations on volume size and file size would both cause me some problems (its a 320gb disk and I have several large files.

Since this disk doesn't yet contain any data its not a big issue to keep reformatting parts of it, I just want to know if what I'm trying to do is possible, or whether there's something inherent to putting home on a partition that makes Windows see an unformatted volume


This is what file servers are for!

---

### Post by Mr. C. on 2007-03-05
> **man-man said:**
> One other related thing, is it possible to install Ubuntu initially onto one partition then later tell it to move one directory (home) to another partition

Plus, I just noticed that the ext3 driver I'm using/planning to use says it is for x86 processors only, will this exclude 64bit (x86-64) processors, or do they still count as being x86?[/QUOTE]

You can move the home directory as you desire.

If it is going to a new disk, move the contents of /home to the new disk, be sure you are not running as any of those users, and mount your new file system ontop of the now empty, not in use /home.

For the same disk, you can simply rename /home or move it, and create a symlink.  It all depends on what you are trying to do.

> **man-man said:**
> 
Plus, I just noticed that the ext3 driver I'm using/planning to use says it is for x86 processors only, will this exclude 64bit (x86-64) processors, or do they still count as being x86?

Please ask your new questions in a separate post so that others will more easily find the information, and this thread doesn't digress to some other topic.

---

### Post by man-man on 2007-03-05
Perhaps it is, but perhaps I don't have a file server and don't want to get one because of the extra cost it would incur

I can see you're trying to help by suggesting alternative ways around the problem, but I really would prefer if I could get it working the way I described (yes, many problems are present in doing so, I will probably eventually succumb to this and do something more sensible, but let me get there in my own time :wink:)

---

### Post by Mr. C. on 2007-03-05
> **man-man said:**
> Perhaps it is, but perhaps I don't have a file server and don't want to get one because of the extra cost it would incur

I can see you're trying to help by suggesting alternative ways around the problem, but I really would prefer if I could get it working the way I described (yes, many problems are present in doing so, I will probably eventually succumb to this and do something more sensible, but let me get there in my own time :wink:)

I've presumed your goal of "get it working" means more than just seeing the bits on both OS's.  I've presumed you actually want to do something useful with the data, and do not want your file systems corrupted across reboots into the alternative system.

You have already experienced the problems that prevent this from working accurately and reliably - I'm personally not interested in helping someone go down a dead-end; it is my preference to help impart knowledge and understanding.  Since you have not asked me "why is this a bad approach?" and have asked how do I keep going, you're on your own here.

Good luck,
MrC

---

### Post by man-man on 2007-03-05
Can I now ask why its a bad approach?
The part where you mentioned corrupting due to reboots made me suddenly interested in anything you have to impart

---

### Post by Mr. C. on 2007-03-05
> **man-man said:**
> Can I now ask why its a bad approach?
The part where you mentioned corrupting due to reboots made me suddenly interested in anything you have to impart

Very wise decision!  :-)

In a nut shell, file systems are *very* difficult to design, develop and implement properly.  File systems almost universally require native operating system support and semantics to operate as designed.  Experts have been trying to provide support for NTFS into the Unix/Linux world for *years* and have not succeed fully.  Simple concepts such as just writing a file are at best still unreliable.  Microsoft was unable to successfully create and deploy their new file system for Vista.  ReiserFS has been developed for years, and years, as have several other well-known Unix/Linux file systems.  Millions of man years have been spent making file systems work on the native OS.

Various version of *nix FAT and FAT32 file system have been around for ages, yet there are still compatibility problems across reboots from basic parition map differences, to difficult-to-detect bugs that occur when trying to emulate one OS in another.  And FAT/FAT32 are, by today's standards, almost trivial.

Consider things like permissions, ACLs, time stamps, symbolic links, hard links, INODEs, pathnames, pathname lengths and limitations, allowable filename characters (a file named \ or : is perfectly legal in *nix, but not Windows), file locking, sparse files, etc. these are all part of the file system or OS, or other layers, and most of these are not available or have the same fidelity or semantcs in other operating systems such as Windows.   There is no 1-1 mapping of many facilities.  The Mac OS had something called File IDs, which was a unique ID, for the life of the file system, that allowed finding a file no matter what its name.  The ext2/3 file systems have no such feature or ability, and trying to emulate the Mac OS file system required changing part of the OS at the lowest layers of the A/UX (unix on a mac) kernel, and required an external daemon program to attempt only partial fidelity and support.  And the Mac OS file system had resource and data forks for a file - ext has none of those things, so they had to be emulated, with only partial success.  Similar problems occur taking ext2/3 to other non-Unixy platforms.

At a higher level, there is no /etc/passwd, /etc/group, so from where do UID/GIDs come from when you're using your Windows ext3 file system?  What time stamps are placed on the files?  What permissions will the files be given?  How do Windows permission translate onto Unix permissions?  File system quotas?  Ext3's journaling, IOCTL differences?

The Samba project has worked for years on trying to overcome these limitations, as has the Cygwin project.  Many feature are just not available or reliable.

Anyway, these are only part of the problems.  I hope you've gained a little understanding from this.

Let us know what you find, and best of luck!
MrC

---

### Post by man-man on 2007-03-05
In the space of time since I last posted, I decided it wasn't worth all the hassle and started setting it up so that each OS had its own space to put files in the language it likes, plus a partition in some variation of FAT to move stuff (I found out that the file size limit was higher than I thought so only about 1 file would exceed it, and that wouldn't ever need to be used in Ubuntu)

Enjoy your correctness, hopefully I will enjoy this computer just as much when I finally get the thing working right :)

---


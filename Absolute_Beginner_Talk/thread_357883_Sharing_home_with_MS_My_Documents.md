---
title: "Sharing /home with MS My Documents"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Fahuadai on 2007-02-10
Hello,


I've already installed Windows and I am about to install kubuntu on my laptop and dual boot MS. I am keeping MS as i have need for a windows OS as i have a university unit that is about developing software on Windows.

I am wanting to share my documents between kubuntu and windows. So that i can access and edit all my music, pictures, etc without having two copies. (only have 80Gb hdd).

Currently i have 20Gb assigned to my Windows OS.  I'm wanting then to have 1Gb swap space, 10Gb for root kubuntu and the rest as a partition for /home and My Documents on Windows.

I think I'll need to format this last partition in ntfs so windows can access it, is this correct?

Also could someone confirm that i've got the partitions roughly 

I'm still quite new to linux, so my apolagies if i'm totally on the wrong path.  I've searched the forums and the user documentation but am still not 100% sure.

If there's documentation that i've missed please direct me to it.

Thanks all in advance.

---

### Post by meng on 2007-02-10
What I would do is make your /home partition ext3 filesystem (the default choice) and install fs-driver ([www.fs-driver.org](www.fs-driver.org)) on Windows, so that it will recognize your /home partition as a "drive", e.g. E:

Then make E:/fahudai (or whatever your username is!) the equivalent of My Documents in Windows.

---

### Post by meborc on 2007-02-10
what i would suggest is that you leave 20g for windows... 10-15g for linux (including /home) a little for swap and the rest in FAT32...

FAT because linux still has some problems writing in ntfs (although big progress has been made in the recent times)... you could even use ext3 - a linux file system as there is an eccellent patch for windows to read/write into it... just search google for "windows ext3 patch"

if you make a separate partition for /home and my documents, then it will be in linux file format anyways (i have no experience in making a /home into ntfs... i'm not sure the partition manager allows this option)

hope you make it all work :) cheers

---

### Post by Fahuadai on 2007-02-10
Thanks a lot guys. 

All installed and working now. 

I attach a screenshot for your viewing pleasure.

---


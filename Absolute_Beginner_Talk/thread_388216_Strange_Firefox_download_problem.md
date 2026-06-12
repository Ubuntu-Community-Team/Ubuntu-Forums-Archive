---
title: "Strange Firefox download problem"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Peti29 on 2007-03-19
Hi!

I've encountered a strange problem these days: I wanted to download some subtitles (via Firefox) and they all ended up 0 bytes long on my mounted FAT32 partition. However when I specified my Home directory as destination they were all OK. (After that I managed to move the files to the FAT32 partition without problem).
Anyone got a clue?

---

### Post by justleen on 2007-03-19
> **Peti29 said:**
> Hi!

I've encountered a strange problem these days: I wanted to download some subtitles (via Firefox) and they all ended up 0 bytes long on my mounted FAT32 partition. However when I specified my Home directory as destination they were all OK. (After that I managed to move the files to the FAT32 partition without problem).
Anyone got a clue?


and other downloads to the partition?
Can you create any files at all at that specific location?

---

### Post by Peti29 on 2007-03-20
- Your avatar picture downloaded without problem

- I tried to create a new empty document with right-click => success
- Then opened it via "Display content" (double click) => success
- Typed some characters and tried to save => error message: "Could not create a backup file while saving *[my test file]*"
- Chose "Save anyway" => success

Then I tried it through the Terminal (very limited knowledge)
- **touch 123.txt** => success (123.txt created)
- **echo test > 123.txt** => success

I have no idea what "ln" does but I always see it in various howtos when backing up e.g. xorg.conf so I thought it's like copy...

- **ln 123.txt 456.txt** => error: "ln: creating hard link `456.txt' to `123.txt': Operation not permitted"

... then again maybe it's not copy.

-  **cp 123.txt 456.txt** => success

Hope this brings you closer to the solution as I still don't have any idea...

---

### Post by Campingman on 2007-03-20
Hi Peti29
Not much help really but I had this exact problem with my first install of Ubuntu.  I had mounted the partition manually after install by modifying the Fstab and Firefox would not write anything to it (it would load the file title and that was it).  I could do the same as you, download to desktop and move to partition.  
I had to reinstall Ubuntu and on install it found my FAT32 partition mounted it automatically and placed it on the desk top.  Firefox now downloads to it no problem.  One of the many Ubuntu challenges!

---

### Post by Campingman on 2007-03-21
My mistake, just downloaded a Tar.gz file and got the same problem again, left with a text file and no content.  Download to desktop and all fine.
Very Odd?

---

### Post by Peti29 on 2007-03-21
I learned _[here]("http://www.ubuntuforums.org/showthread.php?t=287342&highlight=firefox+FAT32")_ that it's a reported bug: [https://launchpad.net/ubuntu/+source/firefox/+bug/65164]("https://launchpad.net/ubuntu/+source/firefox/+bug/65164")
Still no solution though.

---


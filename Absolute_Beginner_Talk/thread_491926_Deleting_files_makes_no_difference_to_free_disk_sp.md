---
title: "Deleting files makes no difference to free disk space?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by cknight on 2007-07-04
Right, so I ran out of disk space on my /home directory today.  Using df in the console showed 0 bytes available in my /home directory.  So I started deleting some files.  First stop was about 7-8 MB worth of JPG images.  Looking at df in the console after doing this still showed 0 bytes available.  Deleted about 30MB worth of mp3 files.  Still df is showing 0 bytes available.  So finally,  I pulled out all the stops and deleted a 735MB avi file.  Finally, df shows lots of free space.  

My question is why the first attempts didn't free up any space?  If it helps, /home is a relatively small partition with only about 2-3 GB space.

---

### Post by renzokuken on 2007-07-04
sometimes you have to empty the trash after deleting files to see the space free up.

---

### Post by blastus on 2007-07-04
LOL. They are in the trash can. That threw me off too when I first started using Linux. After a while, I wondered why I had no space left on one drive. Anyway I discovered that there were a few hundred GB in the trash can ;)

In Nautilus you can bypass the trash can when you delete files by pressing Shift + Delete. I believe the trash can is treated like a FIFO queue based on file time stamp, Linux will automatically delete older files from the trash can to regain space if necessary.

---

### Post by diatribe on 2007-07-04
why would it throw you off? its the same principle as the recycling bin in windows

---

### Post by blastus on 2007-07-04
> **diatribe said:**
> why would it throw you off? its the same principle as the recycling bin in windows

Because the default size of the recycle bin in Windows is set to 10% of the drive space, not the entire drive like in Linux.

---

### Post by Atomic Dog on 2007-07-04
I did the same thing when I first started using Ubuntu :o

---


---
title: "whats taking up the space"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by seekyrr on 2006-01-01
Installed 5.10 default, apache, gnump3d and nmap on a 20 gig drive.  There are about 300mb of music too.

Believe there is 800mb swap file too.

It says now I have 0k free.  I removed 100mb of music...but then an hr later its at 0k free again.

Is there a way to see what is filling up the hd?

Seek

---

### Post by mazelado on 2006-01-02
You could try looking around the system with du.

du -hs ~

Replace the '~' with whichever directory you want to know the size of.

---

### Post by seekyrr on 2006-01-02
EDIT

Decided to reboot and now I can not log in..Says GDM cant write to my authorization file due to lack of disk space.

Wondering if I had some kind of virus eating up the disk space?


thanks for the command tip.  Looking around at the diff folders now.

For a test I emptied 50 mb, then kept hitting refresh in file manger.

10 seconds later back to 0 free space.

Ill keep looking , but if anyone has any idea on logs or something that would eat space that fast id appreciate it.

Seek

---

### Post by ape on 2006-01-02
You aren't running Beagle are you?  I saw the same type of issue when I was testing out Beagle (HUGE log files generated...)

---

### Post by seekyrr on 2006-01-02
Found a 16GIG log from gnump3d!!

Had to delete it.  Im going to have to find out how to stop error loging.  The app seemed to work well, so I dont know why it was making that log??

Thanks

Seek

---


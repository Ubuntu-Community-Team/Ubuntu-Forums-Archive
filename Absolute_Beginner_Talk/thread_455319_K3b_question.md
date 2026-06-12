---
title: "K3b question?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Artistar on 2007-05-26
Hi,

I just want to know, is it possible to burn things from Windows (NTFS) partitions, using K3b? i can't see any of these files, only those from Linux partition....

Thanx.

---

### Post by Kobalt on 2007-05-26
Yes you can do that.
In order to see your Windows partition, go to Places > Computer. From there you should see you floppy drive, your CD/DVD drive and your System files. There should also be something else named *disk* (maybe somethin else, nevermind) : double click on it, and you should see your windows files now.

---

### Post by rillip on 2007-05-26
Linux can read ntfs, but you have to install ntfsprogs to write.  There's en entry in the wiki at:

[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

Or an indepth howto at 

[http://ubuntuforums.org/showthread.php?t=142481](http://ubuntuforums.org/showthread.php?t=142481)

The latter also has information on how to mount the ntfs partitions for read only mode natively.

---

### Post by Artistar on 2007-05-27
i can see them using file managers, but cannot see or burn files using K3b. In K3b i can only see and burn files from my LInux partition, but i wanna burn those from Windows partitions. See the thing is, i have dual boot and gigabytes of files on NTFS partitions. Now, it's not best solution for me always to copy files from my NTFS partitions to my Linux partition every time i wanna burn something....
i also have all those NTFS support programs installed....

---

### Post by indytim on 2007-05-27
Assuming you have mounted your NTFS partition, you should find your files under
Root->Media-><your mounted partition>.

You will find this navigation path in the upper left hand corner of most k3b options.

Good Luck,

IndyTim

---

### Post by Artistar on 2007-05-27
> **indytim said:**
> Assuming you have mounted your NTFS partition, you should find your files under
Root->Media-><your mounted partition>.

You will find this navigation path in the upper left hand corner of most k3b options.

Good Luck,

oh, there they are! one more "problem" solved..... :D

thank you.

---


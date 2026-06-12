---
title: "Size of Ubuntu partition when making new home partition"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by dndrich on 2007-10-20
Ubuntupals:

I plan to upgrade to Gutsy soon.  Before I do this, I figure now is the time to go ahead and make a home partition, because I never did do that.  I have a root partition, and swap, and that is it.  Now, I went to the psychocats website, and the instructions look straight forward enough that I think I could do it.  Trouble is, I am not sure how big to leave the root partition.  See, it instructs you to make a backup, and it looks like the backup stays on root?  If so, then when I try to shrink the partition to make room for the new home partition, will it not let me make the partition too small?  And once I've done it, and the new home is working well, and I delete the backup, won't the root partition now have a bunch of wasted space?  What is the best way to do this?  I figure I have about 15 gigs of stuff, plus the operating system.

---

### Post by dcstar on 2007-10-20
> **dndrich said:**
> Ubuntupals:

I plan to upgrade to Gutsy soon.  Before I do this, I figure now is the time to go ahead and make a home partition, because I never did do that.  I have a root partition, and swap, and that is it.  Now, I went to the psychocats website, and the instructions look straight forward enough that I think I could do it.  Trouble is, I am not sure how big to leave the root partition.


~6GB for a root partition should be more than sufficient - but that can depend on how many downloaded packages you leave in your system cache etc.

---

### Post by dndrich on 2007-10-20
Yes, I want to end up with a partition that size, but with the psychocat instructions, I make a backup.  The backup is in root?  If so, I cannot make the partition that small to begin with.  Here is the link to the instructions.  Am I reading this right?

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by R.Bucky on 2007-10-20
Um yeah, I just installed Gutsy from scratch - again with separate partitions. I made the root partition 15GB with a swap of 2 GB and /home of 200GB. It works great. Although, I had to reinstall twice because I placed the /home partition in the root. OOPS!

---

### Post by dndrich on 2007-10-20
Yes, but this does not answer my original question!

---

### Post by R.Bucky on 2007-10-20
ok, so the backup should not be on the /root partition as that would be the location of the messed up OS. Use the LiveCD install partition editor. Questions?

---

### Post by dndrich on 2007-10-20
No, No...

There is nothing wrong with the current OS.  I just simply want to move the home folder to it's own partition.  That partition does not exist.  Then in the future when I want to do a clean install for some reason, the home partition is not touched.

---

### Post by dcstar on 2007-10-20
> **dndrich said:**
> Yes, I want to end up with a partition that size, but with the psychocat instructions, I make a backup.  The backup is in root?  If so, I cannot make the partition that small to begin with.  Here is the link to the instructions.  Am I reading this right?

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Make your new Home partition (assuming you have disk space), and just copy all of your current /home files to it as per the instructions.

If you copy all of your /home files over to the new partition - then effectively the old /home directory will be the "backup" - just leave them there, or (preferably) rename it to something like "/home-old" and create a new "/home" directory.

Once you are satisfied that your new /home partition mounts correctly and works correctly, then you can delete the old one and recover the disk space it uses.

If you subsequently install a new version of Ubuntu, all of your user files and desktop settings will be preserved in the untouched /home partition - you can even install multiple versions of Ubuntu and boot them using the same /home data (but beware of differing Gnome versions........)

---


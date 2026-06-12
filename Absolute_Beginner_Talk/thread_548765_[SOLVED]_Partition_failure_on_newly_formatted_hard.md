---
title: "[SOLVED] Partition failure on newly formatted hard drive"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by sqrlking on 2007-09-11
I had an 100GB hard drive laying around I thought I'd install ubuntu on.  I hooked it up to my computer (Athlon 64X2 4600+, 1GB, 250GB, Vista Premium) formatted it, and rebooted to begin the installation.  I directed the cd to install on my newly formatted hard drive (guided, use full disk), and it said it would make two partitions, partition 1, and partition 5 for swap, but when it started installing i received an error stating that the "partition failed".  I thought that partition 5 sounded strange, and maybe there were partitions on the formatted drive i didn't know about, but windows doesn't show any partitions on the drive at all, and it doesn't give me the "remove partition" option when i right click on the drive.

I've searched the forums, but honestly, I don't beleive I understand enough to follow most of the threads, and they don't seem to pertain to exactly this.  Any suggestions?

Thanks!

---

### Post by skymera on 2007-09-11
better off foing manually :)

swap = 2x your RAM
home = whatever
root = whatever

format again, to make sure theres nothing left.
reinstall :D

---

### Post by sqrlking on 2007-09-11
swap = 2x your RAM
home = whatever
root = whatever

3 seperate partitions?  should home & root be equal, or it really doesn't matter? & i can do this during the installation, right?

sorry, i've never really needed to partition anything

---

### Post by aspen_dv on 2007-09-11
yes, manually could be done as (with 100GB drive)
Swap =  2048 MB 
/boot = 100 MB
root (or /) = fill up the rest.
You can also put home in seperate partition just in case later on in life you need to reinstall. This won't mess up the files you saved in /home

---

### Post by sqrlking on 2007-09-11
Awesome, thanks, hopefully this'll work.

---

### Post by az on 2007-09-11
Your troubles are not because of the partitioning scheme.  The all-on-one-partition scheme is the default and is the most sensible.  You don't need a separate home and you certainly don't need a separate boot partition.

Windows doesn't show any partitions on the drive because windows ignores linux by default.

You possibly started off with a corrupt partition table and would need to clear the partition table before you try to reinstall linux.  You can use fdisk from the live cd to do that.  From the command line, run

sudo fdisk and then use the "o" command to write a blank partition table.

Other possible causes are hardware failure, or simply that your cd is not intact.  In that case, it may have tried to install but failed without really being related to partitioning.  Did you run the integrity-check?

---

### Post by sqrlking on 2007-09-11
I created the 3 partitions, and ubuntu is up & running, but the partitions are 5, 6 & 7.  Should i re-format & reinstall?  or will i be ok as is?

---

### Post by Snoopyowns on 2007-09-11
I can't see that using 5,6 & 7  will harm you, however, that's definitely something you'll want to remember.

---


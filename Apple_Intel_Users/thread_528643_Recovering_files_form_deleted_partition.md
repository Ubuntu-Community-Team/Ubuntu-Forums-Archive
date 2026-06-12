---
title: "Recovering files form deleted partition?"
date: 2007-08-18
forum: Apple Intel Users
---

### Post by markqvist on 2007-08-18
Because of a rather unfortunate series of events, I have now ended up in a kinda sad situation. I have a Macbook, which I dual-booted between OS X and Ubuntu, but unfortunately I messed up the OS X partition and had to reinstall. Much frustration and agony later, I found myself with all the partitions deleted, including the Ubuntu one. Don't ask why.

The problem is that I had some pretty important photos from my girlfriends graduation on the linux partition (which was ext2). Ouch... Can i recover those files? Physically, the linux partition was in the end of the drive, so with a little luck, the files should still be there. But how should i go about recovering them, now that the actual partition has been destroyed? What tools could I use? I have a functioning OS X partition on the computer right now. Is it possible to boot it into FireWire target disk mode, and then recover the files from another computer, running Ubuntu live for instance?

Any help at all will be much appreciated. Thanks in advance.

/Mark

---

### Post by Nebby on 2007-08-18
It should be simple enough to get the files back, as when you delete a partition (or anything else for that matter) it's just the index that changed, and the actual body of it is left untouched until it's overwritten. I'm sure there'll be plenty of programs to do it on the internet.

[http://e2undel.sourceforge.net/recovery-howto.html](http://e2undel.sourceforge.net/recovery-howto.html)

---

### Post by markqvist on 2007-08-18
Thanks for the reply. Tried e2undel, which seems to be a great program, but my problem is that the entire partition is gone. It seems e2undel can only recover files if the partition is still there, which it isn't. I tried it, but it gives me an error in the likes of "/dev/sda: bad magic number on superblock". I interpreted this as meaning it won't operate on anything else than a real ext2 partition. As i vaguely mentioned, my entire hard drive is now a single HFS+ partition, but only the first 10 to 15 gigabytes are used.

---

### Post by tenjin1 on 2008-02-27
Don't mean to hijack this thread but...

I have a ext3 hard drive with deleted patiton with important files on it I need to recover. I have tried partimage, rsync, ddrescue, etc with no luck because these programs seem to require the partion already there and errors out, which seems to be what the OP is dealing with too.

Is there any other linux programs that will recover files from deleted partitions? I would like to find a solution before I shell out allot of $$$ to some recovery company.

---


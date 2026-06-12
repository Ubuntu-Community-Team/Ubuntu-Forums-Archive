---
title: "help with GNU ddrescue"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-03-06
I've read the info, the man, and everything I can get out of Google, but I'm afraid I've still have questions.

The available information is about replicating one drive's contents to a new drive or partition. I just want to copy directories, which ddrescue supposedly does, but I lack examples and thus syntax. 

To keep it interesting, the source drive is also on another machine. :)

So, I need the syntax advice for copying directories with a logfile'd GNU ddrescue across my LAN.

Source drive is FAT32 on a Windows machine. Target for those contents is anywhere on a much larger  FAT32 drive on Ubuntu. Target drive is not empty. The LAN works; I can see the source drive via Network Servers on Ubuntu.

Bonus questions:

1) I'm guessing that because I'm not replicating drive to drive, I won't be able to run CHKDSK to repair the file system. But that's okay right now -- I just want to get as many of the still-good files as I can with a few passes of ddrescue. That will work, right? 

2) Does the warning about only running ddrescue on unmounted drives still apply when copying directories? (How would that even work if it does?)

---

### Post by compiledkernel on 2007-03-06
having worked in the DR world, I can say Ive never heard of ddrescue actually working against or across the network. I always did it from drive to drive. 

You might do better to use ssh file transfer -- 

[http://www.die.net/doc/linux/man/man1/scp.1.html](http://www.die.net/doc/linux/man/man1/scp.1.html)

---

### Post by ofb on 2007-03-06
compiledkernel,

If there's no network way, I'll put both drives in the Ubuntu box then.

If I read scp correctly, that's just like cp. I want ddrescue for the error-skipping, interruptibility, and multiple passes.

So the rest of the questions remain. Any experience running ddrescue on directories?

---

### Post by compiledkernel on 2007-03-06
That I have know ddrescue only works on block devices > an .img file. Such is also the case with ddrescue's distant cousin recoverdm.

---

### Post by ofb on 2007-03-06
Well, zark. I was sure I saw mention of copying directories, but I can't find that now. 

"one file or block device"

---

### Post by ofb on 2007-03-06
I've just done a lot more reading ... is there really no command for copying directories that will auto-skip bad files?

Seems cp is missing the option, and the dd derivatives only do single files or block devices.

Note that I'd agree a ddrescue img is the best way to proceed. I'd just like to get whatever is still readable off the drive tonight, and deal with the full rescue at a better time. 

Hence I looked for the method to recursive copy while skipping errors, and now i'm intrigued that there doesn't seem to be one.

---

### Post by ofb on 2007-03-07
To answer my own question: Use a GUI...

In Thunar at least, you can select 'skip errors' during a copy.

---


---
title: "How do I find my hdd?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by sapu on 2007-12-20
I'm quite new to ubuntu, and hard-drives are labeled as hda2 and such
I was told they are in the /dev/ folder.

I was unable to find anything.

Also, I'm on the LiveCD following [this]("http://ubuntuforums.org/showthread.php?t=422523") guide, trying to repair my system.

So at the "sudo mount /dev/?d?? /mnt/repair" part, I can't figure out what to put for my question marks.

Side note: I installed ubuntu on to the full hdd, not partitioned.


So which is my hdd, and how do I find it?

---

### Post by taurus on 2007-12-20
Open a terminal and see what's device is your harddrive from the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
```

---

### Post by PeterJS on 2007-12-20
> **sapu said:**
> 
So at the "sudo mount /dev/?d?? /mnt/repair" part, I can't figure out what to put for my question marks.

So which is my hdd, and how do I find it?

The first question mark will be an s or an h. S for SATA and h for IDE (derives from hard drive back in the day before SATA). The second one will be a letter a through z, a being the first physical disk, c usually being the first physical CDROM, and all of the other letters are the remainder of the physical and cd drives in the order the BIOS sees them, so in you're case it will probably be an a. And the last question mark is the partition number, it will probably be the first partition, with swap as the second.

---

### Post by MrFSL on 2007-12-20
My two cents:

```
cat /proc/partitions
```

---


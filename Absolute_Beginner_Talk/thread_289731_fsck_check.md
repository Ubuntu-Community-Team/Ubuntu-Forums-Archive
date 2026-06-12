---
title: "fsck check"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-10-31
every time i boot edgy, it takes a lot of time because it performs a fsck check and filesystems check for every hard drive. it's annoying. can someone tell me how to get rid of this?

---

### Post by pbaehr on 2006-10-31
It should only do this every 20th (I *think* the number is 20) time the discs are mounted.

Are you shutting the system down properly?

If you shut down with a hard power-off the system may be trying to ensure you haven't screwed up anything on the discs because they weren't unmounted before they lost power.

---

### Post by bswilson on 2006-10-31
> **pbaehr said:**
> It should only do this every 20th (I *think* the number is 20) time the discs are mounted.

FYI, it is **every 30** mounts.

---

### Post by xyz on 2006-10-31
Run ```
sudo tune2fs -c 0 -i 0
``` to disable interval checks.

But here is a quote from the "paranoid" man page:

[b]It is strongly recommended that either -c (mount-count-depen&#8208;
dent) or -i (time-dependent) checking be enabled to force peri&#8208;
odic full e2fsck(8) checking of the filesystem. Failure to do
so may lead to filesystem corruption due to bad disks, cables,
memory, or kernel bugs to go unnoticed until they cause data
loss or corruption.[/b]

Also:
```
sudo tune2fs -c 50 /dev/hdx@
```
will allow you to decide when it runs fsck; in this example, it will at the 50th reboot. Adjust the number to your need. I've never tried to set it to 0.

---

### Post by bsussman on 2006-10-31
Checking on a regular basis is a very good thing.

```
sudo dumpe2fs /dev/whatever
```

will tell you what the setting is now.

It is kind of a good idea to know what a value is before changing it.

---

### Post by pbaehr on 2006-10-31
> **bswilson said:**
> FYI, it is **every 30** mounts.

Ah, thanks. I can never remember that number.

---

### Post by mendingo84 on 2006-10-31
this is the output of "sudo dumpe2fs /dev/whatever"
> sudo dumpe2fs /dev/whatever

---

### Post by pbaehr on 2006-10-31
Technically that's just the input. I think you may have slipped when you copy/pasted. ;)

Can you confirm that you're shutting down properly when you turn off the computer?

---

### Post by mendingo84 on 2006-11-01
yep, sorry for the error. the output of sudo dumpe2fs /dev/whatever is: > dumpe2fs 1.39 (29-May-2006)
dumpe2fs: No such file or directory while trying to open /dev/whatever
Couldn't find valid filesystem superblock.

---

### Post by xyz on 2006-11-01
> **mendingo84 said:**
> yep, sorry for the error. the output of sudo dumpe2fs /dev/whatever is:
I don't understand this.
You didn't really run
```
sudo dumpe2fs /dev/whatever
```
I mean not with "whatever"?

---

### Post by mendingo84 on 2006-11-01
yeah...i seem not the paste what matters :)
this is the output that i think is relevant: 
> 
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          91bbd05f-9866-4c82-a737-328cd85bc1e4
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal filetype needs_recovery sparse_super
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              2420096
Block count:              4833556
Reserved block count:     241677
Free blocks:              4228914
Free inodes:              2327091
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16352
Inode blocks per group:   511
Last mount time:          Wed Nov  1 11:50:30 2006
Last write time:          Wed Nov  1 11:50:30 2006
Mount count:              13
Maximum mount count:      30
Last checked:             Thu Jan  1 02:00:00 1970
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
First orphan inode:       1553465
Journal backup:           inode blocks
Journal size:             128M


---

### Post by xyz on 2006-11-01
Could you please tell me what you exactly typed (or pasted) as a command line?
Thank you.

---

### Post by mendingo84 on 2006-11-01
yes. it was
sudo dumpe2fs /dev/hda2
hda2 is an ext3 partition where edgy is installed

---

### Post by mendingo84 on 2006-11-01
i think this is not the major problem. i have another fat32 parition which is also checked at every boot and if i type this " sudo dumpe2fs /dev/hda5" i get this 
> 
dumpe2fs 1.39 (29-May-2006)
dumpe2fs: Bad magic number in super-block while trying to open /dev/hda5
Couldn't find valid filesystem superblock


thing is checking hda5 is what takes a hole lot time!

---


---
title: "Partitioning...."
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by ElEdwards on 2007-08-06
Well, after going all Linux, I find I have to go back to a dual boot with XP (for reasons I won't go into) so here's what I'm thinking about....

I have two HDDs in my system:
HDD#1 80 Gig
HDD#2 40 Gig

Here's the partitioning I'm considering:
```
HDD#1
- 1 /ntfs (Windows C:\) 20 Gig
- 2 /ntfs (Windows D:\) 20 Gig
- 3 /boot   1 Gig
- 4 /      19 Gig
- 5 /opt   10 Gig
- 6 /var   10 Gig

HDD#2
- 1 /home  38 Gig
- 2 /swap   2 Gig
```

Thoughts?  Suggestions?  Changes?

I appreciate your input :)

---

### Post by Aspra on 2007-08-06
Im totally new at this and i could be wrong but I suggest you go with an OS on both hard drives, linux on one and windows on the other. Iv read that you plug just one hard drive in -install the OS on it, windows first usually. Unplug that one then plug the other one and install Linux on that one. but don't take my word for it.

Im having some trouble my self, with partitioning my single 80 gig drive to dual boot

---

### Post by sep1318 on 2007-08-06
Looks pretty good, though I'm a bit wary of having your root and swap on different drives. But then again, I only have one physical drive to deal with, so I don't know. Why do you need two win partitions?

---

### Post by bodhi.zazen on 2007-08-06
> **ElEdwards said:**
> Well, after going all Linux, I find I have to go back to a dual boot with XP (for reasons I won't go into) so here's what I'm thinking about....

I have two HDDs in my system:
HDD#1 80 Gig
HDD#2 40 Gig

Here's the partitioning I'm considering:
```
HDD#1
- 1 /ntfs (Windows C:\) 20 Gig
- 2 /ntfs (Windows D:\) 20 Gig
- 3 /boot   1 Gig
- 4 /      19 Gig
- 5 /opt   10 Gig
- 6 /var   10 Gig

HDD#2
- 1 /home  38 Gig
- 2 /swap   2 Gig
```

Thoughts?  Suggestions?  Changes?

I appreciate your input :)

Wow, that is way complicated ...

You do not need all that much space in /opt or /var or /swap for that matter ...

You *could :

```
HDD#1
- 1 /ntfs (Windows C:\) 20 Gig
- 2 /ntfs (Windows D:\) 20 Gig
- 3 /boot   512 Mb
- 4 /      10 Gig
- 5 /home  40 Gig

HDD#2
- 1 /mnt/data  39 Gig
- 2 /swap   1 Gig
```

The /mnt/data partition can be shared with windows if it is FAT, NTFS, ext2, or ext3 (I would not use ext2)

Note: I hope I got the Gb correct ....

---


---
title: "30th reboot forced root check"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-04-05
I guess this is to make sure the kernal is still intact, but my message was not sounding perfect it said "5.9% Non contigious" What's that mean and is it bad?

---

### Post by chantra on 2006-04-05
I just checked that the root filesystem is fine. 5.9% sound quite a lot, but don't worry much about it.
Linux filesystems usually just defrag themself any time you copy new file.
Starts getting worried if next time it is more than those 5.9% and it just keep increasing :s

---

### Post by wolfee on 2006-04-05
Thanx!! I'm new to Ubuntu so I don't know what to expect. I havent had one crash or freeze yet!!!

---

### Post by AndrewCaul on 2006-04-05
So how can you perform this check manually so it doesn't have to force it?

---

### Post by carlosqueso on 2006-04-05
you can't while the file system you want to check is mounted (AFAIK), well you can but it can cause damage.  It's alright if it forces it, because it checks before it mounts the disk and will fix any errors it finds.  If you really want to check, use a live cd and run fsck on the partition that contains your root filesystem.

---

### Post by chantra on 2006-04-05
yep, the partition has to be unmounted, so either use another linux system or use a livecd

---

### Post by Herman on 2006-04-05
[CENTER][LEFT]I agree with the other posters, and you can also do:

```
sudo touch /forcefsck
```[/LEFT]
   [/CENTER]
    [LEFT][COLOR=#000000][FONT=Arial] 
Then, restart your computer and watch carefully while the computer is rebooting for the 
>  * checking the root file system
 
'|==================...                                                                                                                                                                          /'  [/FONT][/COLOR][/LEFT]

---

### Post by dcstar on 2006-04-05
[QUOTE=chantra]I just checked that the root filesystem is fine. 5.9% sound quite a lot, but don't worry much about it.
Linux filesystems usually just defrag themself any time you copy new file.
Starts getting worried if next time it is more than those 5.9% and it just keep increasing :s[/QUOTE]
There is nothing whatsoever to "worry" about if it is 5.9% or even 10.9%, the ext2 filesystem is designed to perform more than adequately with those amounts of non-contiguous files.

The only performance issue will arrise if you run out of sufficient disk space on a filesystem that prevents the OS from efficiently allocating files in contiguous blocks.

People should leave their Windows/DOS concerns where they belong, in that world.

---


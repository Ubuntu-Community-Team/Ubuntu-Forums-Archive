---
title: "Finding my second hard drive..."
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by pirata on 2007-01-04
As a complete linux novice, and not much more experienced windows user to be honest, I may have done a foolish thing in just jumping in with both feet and installing ubuntu... but this is what I've done! I have a 20Gb hard drive in my system, which was running windows xp, and a 120Gb hdd on which I was storing all my data (office files, music, video etc). When I installed ubuntu (v.4.10) I selected to erase and install on the windows disk, but now I can't seem to locate the disk with all my data on it. I have searched the forums for similar issues, but can't find anything specifically relevant, and I am going to go out and get myself a book or two on ubuntu and linux in general as I've realised it's a bit more complicated than I thought, but if anyone can give me any advice (in really simple idiot language!) in the mean time, it'd be much appreciated... Cheers:D

---

### Post by CroEragon on 2007-01-04
First of all, did you mount your second hard?
If you didn't , read [this.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows")
If it is ntfs partition (most likely) and you need read/write access then read [this.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")
Beware, it is beta program, so might cause problems. But it works perfectly for me.
And you should know that Ubuntu cant write ntfs filesystem without help of program called ntfs-3g. Second link show how to install it.

---

### Post by gilbertr on 2007-01-04
You'll first need to check your current situation.
Within an ubuntu system console, type the following command : fdisk -l
(That's a small l for _L_ist)

This will show you your attached drives and partitions.
Check whether these reflect what you would normally expect to see.

It would be worth posting the output back here.

---


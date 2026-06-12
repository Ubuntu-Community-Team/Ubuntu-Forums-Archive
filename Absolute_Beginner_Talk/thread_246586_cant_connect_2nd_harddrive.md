---
title: "cant connect 2nd harddrive"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by sinisterfuzzy on 2006-08-29
i plugged in another harddrive that i had on my other comp (windows) and it gives me a weird error message: it says: 
Unable to mount the selected volume.
error: device /dev/hdb1 is not removable
error: could not execute pmount


[IMG]http://i23.photobucket.com/albums/b378/sinisterfuzzy/Screenshot2.png[/IMG]

---

### Post by xpod on 2006-08-29
I too plugged in an extra harddrive from an older pc recently which was detected fine by the separate xp and ubunto installs on their separate drives.

I mounted the drive in question temporarily via "discs" by creating a mount point in the "mnt" folder.This was only temporary as i had`nt made the approriate entries in my fstab etc but upon rebooting i did`nt just NOT have a mounted disc i also did`nt have the two operating systems that i started out with......Vanished into the darkness

Anyway...just basically to say "remember and back up" if you have important stuff.... unless like me you aint fussy either way and can have a laugh at a complete system failure followed by the days of potential torture as you try figure out what you`ve done......lol
 
Good luck.......and have fun

One does not need to use a "formatting" application to wipe clean their drives....be careful ppl:twisted: .

---

### Post by dannyboy79 on 2006-08-29
I believe xpod's situation is very rare!!!! if you want to be able to view what is on your fat32 hard drive, you need to mount it using special mount instructions. I am at work and can't google right now because my lunch is almost over, but just go to gogle and type in "mount windows partition" and you'll find your answer! I simply added lines to my fstab file and my ntfs and my fat32 paritions and hard drives get mounted automatically upon boot. I can give you a copy of my fstab later if you'd like, send me a PM if you'd be interested in that.

---

### Post by xpod on 2006-08-29
I think it was very rare as i had plugged drives in previously to the same installs without too much problem...NOTHING like my recent fun and games.

Sorry if my post created any "worry".As dannyboy79 says mine was a rare occurance but i just thought my two bobs worth regarding "keeping safe" would`nt do no harm.

---

### Post by confused57 on 2006-08-29
Maybe this will help you:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

I tried the following link, but had trouble getting it to work:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---


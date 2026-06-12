---
title: "partitioning help for dual boot on dell"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-15
I have a dell 700m, win xp pro is installed and i want to keep it there for the time being.  I do not have a windows cd, they didnt send one, just the restore option partioned in the hard drive.  I put my live cd in and opened up gparted, I saw 3 partitions:
dev/hda1     fat 16        4 MB  :confused: 
dev/hda2     ntfs          72 Gb
dev/hda3     fat 32       4 Gb
I need to know if they are intertwined at all, or if i can delete the two fat partitions, and shrink the htfs partition, (without damaging the current windows setup) and leave the extra unallocated so i can make my / bootable, /home, and swap for ubuntu install.  I am hesitant to blast anything away without having a win cd to restore, ( I called them and told them to send me one but it will be a week) Please help me not make a mistake, thank you!

---

### Post by aysiu on 2006-04-15
This is a pretty good guide:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

But I would play around with the live CD a bit longer until you get your restore CDs.

---

### Post by Scunizi on 2006-04-15
Caution... One of your partitions might have the windows RESTORE files on it.  If those files are duplicated on your CD you'll be ok but if not.... well .. you run a risk.  I know some Gateways have the entire restore system on a partition.  Although it's fast, on boot up you can see you'll have an option to restore by pushing F1 or something to that effect.

---

### Post by x5452 on 2006-04-15
yeah I know that I have the restore on this, I have used it once, (ctrl-f11) but it will just restore to its original out of box state, i dont believe it goes through setting up the windows partition manually.  If I save that one, remove the fat16, 4 megabyte one, and shrink the 70gig ntfs to like 15 gig, all should be well right? Or am I missing something?  I dont, obviously, really understand how much power the system restore has, or whatever...to alter partitions if it is chosen?

---

### Post by x5452 on 2006-04-15
ok heres an easier question that I dont know why I cant figure out.  Im trying to copy all my files off windows just in case, i have a dvd burner, and dvd hold what, like 4 gig compared to 700meg.  so why cant i burn a data dvd?  nero tells me to put a cd-r in, if i right click my file and send to be copied it says an error occured?  ive burned dvd movies so i know it works...any ideas?  Note: I have never burned data to a dvd before, is it even possible?

---

### Post by mrchrisblau on 2006-04-15
[QUOTE=x5452]ok heres an easier question that I dont know why I cant figure out.  Im trying to copy all my files off windows just in case, i have a dvd burner, and dvd hold what, like 4 gig compared to 700meg.  so why cant i burn a data dvd?  nero tells me to put a cd-r in, if i right click my file and send to be copied it says an error occured?  ive burned dvd movies so i know it works...any ideas?  Note: I have never burned data to a dvd before, is it even possible?[/QUOTE]

Burning data to a DVD should be possible. Perhaps Nero does not support DVD writing? I use it for CD-Rs all the time, but never for DVDs.

---


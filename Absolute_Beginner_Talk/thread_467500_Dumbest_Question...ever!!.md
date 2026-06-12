---
title: "Dumbest Question...ever!!"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Irmis on 2007-06-07
I've been looking high and low. Couldn't fine it on Gnome or my new pretty KDE (I'm sure there's a word for them but I dunno what it is) anyway, where are the system tools like Scandisk and Defrag?

---

### Post by FleetAdmiral74 on 2007-06-07
Well scan disk is actually a comand...cant remember it rightnow. Does it auto every 27 bootups though.

and if you used ext3, no need to defrag. dont think you could if you tried anyway, its != ntfs  :)

---

### Post by Tyke91 on 2007-06-07
Ubuntu doesnt fragment files untill you get really close to filling your disk, so there is no defrag ( i think)

your disk will be checked automatically if something is corrupt.

---

### Post by hardyn on 2007-06-07
> **FleetAdmiral74 said:**
> Well scan disk is actually a comand...cant remember it rightnow. Does it auto every 27 bootups though.

and if you used ext3, no need to defrag. dont think you could if you tried anyway, its != ntfs  :)

fsck

but the disk to be checked cannot be mounted!

---

### Post by homergreg on 2007-06-07
fsck is the file system check utility, and it is automatically done every 27 or so mounts. don't run it manually on a mounted filesystem or you may end up with some nasty problems.  

The only dumb question is the one unasked, or the ones I usually come up with!

(edit: I am getting pretty good at putting up a redundant answer right after somebody else!!)

---

### Post by Alterax on 2007-06-07
fsck (File System ChecK) is the command that you would invoke to check and repair a disk's filesystem (Like ScanDisk).   It's run from the terminal as sudo fsck /dev/hda1 (for partition 1 of the first hard disk; should be run separately for each partition of your hard drive except swap, which doesn't need it)

 But before you use it, there's some considerations.  It's very unwise to use it on a mounted disk partition, so if you want to do it manually, it's best to boot up with an Ubuntu or Knoppix LiveCD and then run it after making sure that the disk wasn't mounted.  That'll prevent data loss.

If you want to defrag it, it's better to  just wait.  After a certain number of mounts, Ubuntu does an automatic filesystem check and repair.

--Alterax

P.S.  Not a dumb question at all.  Most of my coworkers draw a blank if I even so much as mention a filesystem.

---

### Post by dmizer on 2007-06-07
if you want to force a check disk just run this command:
```
sudo shutdown -rF now
```
this command will reboot your computer and start the fsck command on restart before the system is mounted.  this command checks the integrity of the disk and it's file system.  however, as has already been noted, this happens automatically ever 30 reboots anyway, so unless you think you actually have a problem on your disk, you shouldn't be concerned about manually enabling this task.

there is no need to defragment an ext3 formatted (ubuntu default) drive.

---


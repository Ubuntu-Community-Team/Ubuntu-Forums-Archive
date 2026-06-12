---
title: "Ubuntu can't see my Windows partition"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Perrry on 2008-01-01
Hey folks.  I've poked around the forums and haven't really found an answer to my problem.  I've been running Gutsy on my Inspiron 1501 since the beta came out.  It seems that half the time, when i boot, my Windows partition is mounted on the desktop, The other half, the partition is completely invisible.  I mean it's not on the desktop, not in the Places>Computer menu... nowhere.

Has this happened to anyone else?

---

### Post by Borbus on 2008-01-01
Is it an NTFS partition?

Sometimes if Windoes doesn't shut down properly (maybe this is the same with ntfs-3g too) it leaves the NTFS partition "locked" and by default mount will not mount a locked partition.

Open a terminal and type sudo gedit /etc/fstab

Look in there for your NTFS partition, here's an example:

# /dev/sdd1
UUID=AE208DFA408FC6D5 /media/sdd1     ntfs    defaults,umask=007,gid=46 0       1

Note the first line, in this case it is /dev/sdd1.

Now type into a terminal sudo mount /dev/sdd1
It will either mount or will have an error. If the error is that it is locked then you can force mount it like this: sudo mount /dev/sdd1 -o force

---

### Post by Majorix on 2008-01-01
It's most likely a problem with it auto mounting.

A fix I can think of is to edit your /etc/fstab to add a line telling Ubuntu to always mount your partition.

It goes like this:
```
gksudo gedit /etc/fstab
```
With it open, do this:
```
ls -l /dev/disk/by-uuid/
```
And copy the output. Then create a line in that file, like this:
```
UUID=UUIDYouGotFromTheLastCommand /MountLocation_MakeSureItExists ntfs-3g defaults 0 0
```
Save & close the file.

When you logout and log back in now, it should automatically mount that partition.

You can always try this if not:
```
sudo mount -a
```
If it complains about unclean shutdown, add an "-o force" at the end, without the quotes, like this:
```
sudo mount -a -o force
```
You can also add this to your System > Prefs > Session Management program, as a new entry, but like I said you won't need it if it automatically mounts.

Hope it helps.

---


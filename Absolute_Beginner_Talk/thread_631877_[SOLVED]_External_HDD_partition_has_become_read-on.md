---
title: "[SOLVED] External HDD partition has become read-only for no apparent reason"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by seanfitz64 on 2007-12-04
I am about to upgrade from Feisty to Gutsy. Before I do so I need to back-up my data to my external HDD. However, the partition I usually save my backups to has just become read-only for no apparent reason.

The external HDD is connected via USB. It has three partitions:

[LIST]
[*]EXTERNAL A
[*]EXTERNAL B
[*]EXTERNAL C
[/LIST]

Both A and C are still working fine. They are completely read-write. But I can't delete from, or write files to B.

I've already tried to sort this out on IRC, but we were stumped.

This is what we discovered...

When I run 'mount' in a terminal I get:

```
/dev/sdb1 on /media/EXTERNAL A type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sdb2 on /media/EXTERNAL B type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sdb3 on /media/EXTERNAL C type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
```

... so you can see B is supposed to be RW, and it has the exact same parameters as A & C.

If I run 'sudo touch "/media/EXTERNAL B/test"' I get:

```
touch: cannot touch `/media/EXTERNAL B/test': Read-only file system
```

I've tried changing the permissions for B in Nautilus, but there is nothing to change, as the perms are the same as the other two partitions.

Around that time - so I'm not sure if it's the cause or a result - I deleted a lot of files from the EXTERNAL B partition. Now, whenever the external drive is plugged in those deleted files show up in my local Gnome Garbage Bin. I can't delete them. When I try to empty the Garbage Bin a dialogue pops up which says: 

[INDENT]Preparing to Delete files[/INDENT]

...but it hangs. When I cancel it I get the following error message:

[INDENT]Error while deleting.
"/media/EXT...s.sbd/SMF" cannot be deleted because it is on a read-only disk.[/INDENT]

What I hope to achieve is:

a) Being able to write to EXTERNAL B again (and delete files). In other words - change it from read-only back to read-write.
b) Delete the files in the .Trash-Sean folder on EXTERNAL B, either manually or via the Gnome Garbage Bin.

I am a relative Linux newbie, so please don't assume any knowledge. :-)

---

### Post by frodon on 2007-12-05
First check the system log (system > log viewer, open syslog and message) to see if there's some errors once you mounted your external drive. If not it's surely just a wrong mount command issue.

---

### Post by psusi on 2007-12-05
sudo umount /dev/sdb2
sudo fsck -f /dev/sdb2

---

### Post by phen on 2007-12-05
a file system check (fsck) would be my guess, too. I had the same problem: the system sets disks to read only, when it thinks that the drive does not work properly.

for me, my hd really didn't work properly when it happened, hope for you the system is wrong with its thoughts this time :-)...

---

### Post by seanfitz64 on 2007-12-05
Thanks for the responses.

I checked the syslog as suggested by **frodon** and every time I try and do something with that partition I get a spray of these messages:

```
Dec  6 04:25:19 SEANSLAPTOP kernel: [17694.615000] FAT: Filesystem panic (dev sdb2)
Dec  6 04:25:19 SEANSLAPTOP kernel: [17694.615000]     fat_get_cluster: invalid cluster chain (i_pos 0)
```

I have no idea what they mean though. (Please remember guys - total newbie here... you will have to explain everything.)

I tried 'sudo umount /dev/sdb2' and 'sudo fsck -f /dev/sdb2' at the command line as suggested by **psusi** and the output was:

```
fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
```

I was then able to create and delete files and folders. However, the minute I tried to empty the Garbage Bin or delete files manually from the .Trash-Sean folder I hit problems.

Sometimes I can delete files, sometimes as soon as I click on them they revert back to read-only (the little folder icon in Nautilus turns into a lock.)

By continuously unmounting and remounting the partition I have been able to delete many of the files and folders in .Trash-Sean, but I have hit some stubborn ones that won't delete and revert to read-only as soon as I touch them (I'm starting to hate that little lock icon!)

Obviously mounting and remounting the partition every time I want to delete something from the  .Trash-Sean folder is not very sustainable either!

Thanks guys. Although I don't fully understand what is going on we seem to be making progress. Please persist!

---

### Post by asmiller-ke6seh on 2007-12-05
On which volume is this trash located? Maybe you need to FSCK that volume, too?

---

### Post by seanfitz64 on 2007-12-05
**asmiller-ke6seh**: a .Trash-Sean folder is created on each of the 3 partitions on the external HDD.They each contain deleted items from their own partition only. I have no clue if anything similar is created on the C: drive.

---

### Post by psusi on 2007-12-05
If you dual boot windows, then you might try asking it to chkdsk /r that drive, since it's fat.

---

### Post by seanfitz64 on 2007-12-05
**psusi:** How do I do that? I tried running 'chkdsk /r /dev/sda1' but received the following:

```
bash: chkdsk: command not found
```

---

### Post by seanfitz64 on 2007-12-05
Hehe... ok... chkdsk is a Windows command. 

I was reminded of this because, coincidentally, in the middle of all of this I needed to resize my partitions. On the first boot after resizing Windows detected something had changed and ran chkdsk for me! That partition is fine.

I am still having problems deleting files from the EXTERNAL B partition of my HDD and having it keep returning to read-only.

---

### Post by psusi on 2007-12-05
Force a chkdsk /r to check for bad sectors, and check your logs for error messages.

---

### Post by frodon on 2007-12-06
Ok, i already had problems with FAT32 partitions and such errors don't necessarily mean your disk is damaged.
In some rare case when your computer crash or have an unexpected behaviour linux vfat drivers may be buggy and when you are in this case running a check & repair under windows won't help.

First thing for you to check is to plug your disk while on windows and see if it works well (according to your previous post it seems to work under windows).

To repair such a vfat driver mess the command to use is "dosfsck", do a "man dosfsck" to know how it works, anyway i think something like "sudo dosfsck - a /dev/sdb1" with your partitions unmounted obviously should do it.

When it arrived to me i repaired the mess without losing any data.

---

### Post by seanfitz64 on 2007-12-06
**frodon**: Success! Thank you!

I ran dosfsck -a /dev/sdb2 and this is what I got:

```
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Orphaned long file name part "77oore.sbd"
  Auto-deleting.
/.Trash-sean/.mozilla-thunderbird/hccti88d.default/;077ail/mail.iinet.net.au/;070riends etc..sbd
  Contains a free cluster (1496955). Assuming EOF.
/.Trash-sean/.mozilla-thunderbird/hccti88d.default/;077ail/mail.iinet.net.au/;070url.sbd
  Contains a free cluster (1496973). Assuming EOF.
/.Trash-sean/.mozilla-thunderbird/hccti88d.default/;077ail/mail.iinet.net.au/;072ealth.sbd
  Contains a free cluster (1497277). Assuming EOF.
/.Trash-sean/.mozilla-thunderbird/hccti88d.default/;077ail/mail.iinet.net.au/;073nbox.sbd
  Contains a free cluster (1503122). Assuming EOF.
/.Trash-sean/.mozilla-thunderbird/hccti88d.default/;077ail/mail.iinet.net.au/;074unk.sbd
  Contains a free cluster (1503134). Assuming EOF.
/.Trash-sean/.mozilla-thunderbird/hccti88d.default/;077ail/mail.iinet.net.au/;076earning;084imes.sbd
  Contains a free cluster (1503370). Assuming EOF.
/.Trash-sean/.mozilla-thunderbird/hccti88d.default/;077ail/mail.iinet.net.au/;077eetomatic.sbd
  Contains a free cluster (1503537). Assuming EOF.
/.Trash-sean/.mozilla-thunderbird/hccti88d.default/;077ail/mail.iinet.net.au/;070riends & ;070amily.sbd/;075ristine.sbd
  Contains a free cluster (1496827). Assuming EOF.
/.Trash-sean/.mozilla-thunderbird/hccti88d.default/;077ail/mail.iinet.net.au/;070riends & ;070amily.sbd/;077e.sbd
  Contains a free cluster (1496943). Assuming EOF.
/.Trash-sean/.mozilla-thunderbird/hccti88d.default/;077ail/mail.iinet.net.au/;070riends & ;070amily.sbd/;084ula.sbd
  Contains a free cluster (1496953). Assuming EOF.
/.Trash-sean/rdiff-backup-data/increments/.mozilla-thunderbird/hccti88d.default/;077ail/mail.iinet.net.au/;070riends etc..sbd
  Contains a free cluster (1496956). Assuming EOF.
/.Trash-sean/rdiff-backup-data/increments/.mozilla-thunderbird/hccti88d.default/;077ail/mail.iinet.net.au/;072ealth.sbd
  Contains a free cluster (1497278). Assuming EOF.
Reclaimed 719 unused clusters (11780096 bytes) in 1 chain.
Free cluster summary wrong (379358 vs. really 379343)
  Auto-correcting.
Performing changes.
/dev/sdb2: 119868 files, 1667441/2046784 clusters
```

So it appears the problem was related to orphaned long filenames and some bad cluster information. After these files were deleted I was able to go into the /.Trash-Sean/ folder and manually delete the rest of the stubborn files. It took a while, as I had to burrow down to actual files, as trying to delete higher-level folders kept triggering the partition back into read-only mode, so I had to unmount and mount several times, but I got there eventually!

But now the trash is empty and I can create and delete files and folders and empty the trash without triggering the partition back into read-only mode.

I will now mark this thread as solved. Thanks heaps for everyone's help!

---


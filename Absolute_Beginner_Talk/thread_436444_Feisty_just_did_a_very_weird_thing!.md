---
title: "Feisty just did a very weird thing!"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by drowner on 2007-05-07
Hey guys

I just upgraded to feisty, and it did something odd.

I previously had the following things mounted:

My windows NTFS partition mounted as /xp - thats ok
An external USB drive, mounted as /media/EXTERNAL200 - This has strangely been remounted as /media/EXTERNAL200_ whilst the /media/EXTERNAL200 is still there, but its empty

Much the same, a shared FAT32 partition mounted as /shared - is now empty, but it has reappeared as /media/disk .... this has also appeared on the desktop

Im not sure why this happened! It never happened with any previous upgrades.

Any thoughts on what happened? And how do I remount them, and clean up the previous mounts?

Cheers

---

### Post by drowner on 2007-05-07
Ok

Here's the ouput of **fdisk -l**
Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1946    15631213+   7  HPFS/NTFS
/dev/sda2            3108        3648     4345582+   5  Extended
/dev/sda3            1947        3107     9325732+  83  Linux
/dev/sda5            3163        3648     3903795    b  W95 FAT32
/dev/sda6            3108        3161      433692   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders


[B]
and my etc/fstab:[/B]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=91abedcc-d196-46b6-8260-ad8d179817bb / ext3 defaults,errors=remount-ro 0 1
/dev/hda5	/shared		vfat	umask=000	0	0
# /dev/hda1 -- converted during upgrade to edgy
UUID=60F42A23F429FC42 /xp ntfs nls=utf8,umask=0222 0 0
# /dev/hda6 -- converted during upgrade to edgy
UUID=41cae735-f7b4-4de0-a508-a0af35eb8f19 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/mmcblk0 /media/sdcard auto noauto,rw,user,exec,sync 0 0

---

### Post by drowner on 2007-05-07
Any thoughts guys?

Its starting to confuse me

Particularly as everything that was a hda is now an sda.... despite this, it still mounts the windows partition OK.

confused.

---

### Post by jerrylamos on 2007-05-07
See if you can write a launchpad bug on this.  The scrambled confusion on what partitions are what are a direct result of some boot code changes they decided to make.

Cheers, Jerry

---

### Post by drowner on 2007-05-07
I will do that

But could anyone help me with my questions, particularly:

1. getting my shared hda5 (?sda5) to mount as /shared at startup

2. Removing the EXTERNAL200, and making the EXTERNAL200_ become that

3. Possibly explaining why everything that was a hda is now an sda, and despite this, why my windows partition still mounts fine, and why everything still runs ok?

---

### Post by drowner on 2007-05-07
(should have stuck with dapper LOL)

---

### Post by drowner on 2007-05-07
Ok, now its getting REALLY weird
I was unable to read and write to the External USB drive, so i ejected it. It asked me for a password to do this, and then it let me

So i plugged it back in

and it didnt mount automatically (which it normally does)

Getting very strange indeed.

ANY help would be GREATLY appreciated, ta.

---

### Post by bobplano on 2007-05-07
you could mount them yourself, but i don't think that has the persistence you want. anyway
```
sudo mount -a
```will tell you the name of the things you want to mount and
```
sudo mount *partition* */place/to/mount*
``` i think is the correct command for mounting

---

### Post by drowner on 2007-05-07
hmmm

sudo mount -a
[mntent]: warning: no final newline at the end of /etc/fstab
mount: special device /dev/hda5 does not exist

---

### Post by Nythain on 2007-05-07
hd changed to sd due to the new kernel, for simplicity sake for some reason or another it now treats all hdd as sd's no big deal

as for your fstab and mounting issues, why dont you just recreate your fstab, and use the /dev/whatever instead of the uuid... thats another thing that changed with the new kernel for simplicity sake... not sure if there is a negative impact of using /dev/ now instead of the uuid, but its worth a shot, everything else in your fstab (mount points, options, filesystems etc.) looks correct, so im assuming all of your problems are now stemming from the conversion of hd to sd and /dev/ to uuid.

the only other option i could think of would be re-install, but im not a kernel, device, or fstab expert, anyone else have any suggestions

---

### Post by drowner on 2007-05-08
Unrelated update:

I decided to unmount everything and rewrite fstab, which i thought would work

Then I couldnt unmount my External USB drive... but i understand this is a known bug, and i applied the necessary workaround.

If you guys dont mind helping my education, what I *think* has happened here is

Feisty turns hda-sda, fair enough
And the uses the UUID code to update your fstab

Obviously for me, it got the right UUID for my XP partition but not my shared drive. Is that correct?

And can i rewrite my fstab like /dev/sda5 /shared ? Or do I need to work out the UUID things?

Regards.

---

### Post by Nythain on 2007-05-08
lets search shall we...

a much helpfull and very informative thread with similar topic that should answer all your questions
[http://ubuntuforums.org/showthread.php?t=434766&highlight=using+%2Fdev+in+feisty+fstab]("http://ubuntuforums.org/showthread.php?t=434766&highlight=using+%2Fdev+in+feisty+fstab")

in case you are lazy and dont want to read it, aparently YES, you can rewrite your fstab using /dev instead of the uuid... so give it a try

---

### Post by drowner on 2007-05-08
sorry, take my word for it... i WAS searching (obviously not very effectively)

---

### Post by Nythain on 2007-05-08
dude, im sorry... i wasnt meaning to sound rude... i was trying to be fun and playfull... i was typing that all while i was opening up another tab and starting my search... i really really really didnt mean to sound like a prick...

i hope that thread helped though :)

---

### Post by drowner on 2007-05-08
Ok fixed.

Just changed hda5 to sda5, and it worked a treat

I still dont REALLY know why feisty couldnt pick it up at upgrade, but i guess it doesnt matter

thanks for the help

---


---
title: "Help cloning hard drive"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Nessa on 2007-09-24
I'm running the livecd... 

```
dd if=/dev/hda of=/dev/hdb bs=4096 conv=notrunc,noerror
```

^Gives me a message: dd: opening `/dev/hda': Permission denied

Help please... I need to copy EVERYTHING to a new/larger drive...

---

### Post by justleen on 2007-09-24
try a sudo dd?

---

### Post by justleen on 2007-09-24
ohw, duh!

you must supply a number aswel!

/dev/hda1 for example!

you can never use a whole "drive"  you must supply argument as to what partition.
```
dd if=/dev/hda1 of=/dev/hdb1 bs=4096 conv=notrunc,noerror 
```

---

### Post by Nessa on 2007-09-24
```
sudo dd if=/dev/hda of=/dev/hdb bs=4096 conv=notrunc,noerror

```

I didn't get an error. Now it's on that blinking cursor thing. Based on System Monitor, the cpu and memory are doing something. Do I just wait?

---

### Post by justleen on 2007-09-24
yep, just wait..


(did you check the size of hdb1?)

you can open a new terminal, and type "top"  it will tell you wether dd is working or not

in yet antoher new terminal, type "watch vmstat -d"  for the disk activity

---

### Post by Nessa on 2007-09-24
Wheeee! It's moving, it's moving! *crosses fingers* I really hope this works...

---

### Post by psusi on 2007-09-24
Are hda and hdb the exact same drive make and model?  If not then you don't want to use dd.  Heck, there really is no reason to use dd even if they are.  It will be faster to just format the new drive, mount both the old and the new, and cp -a all of the files over.  You don't even need a livecd; you can just do it from recovery mode.

---

### Post by Nessa on 2007-09-24
No they're not. Read up. The new drive is bigger like I mentioned. Does cp -a copies files and partitions?

---

### Post by justleen on 2007-09-24
the make and model have ab-so-lu-ty nothing to do with dd...

How bout me creating a dd image piped trough vdump onto a tape drive??
or me tranfsering a created boot image to a floppy/usb/cd? 

cp -a is not the same, since it will not do a bit by bit transfer..

and as far as the live cd is concernd, for neither cp or dd do you need to enter rescue mode or the live cd.. its perfectly ok to just mount the drive, and copy/dd to the new drive from a "live" system. (yes, al the the stuff  /proc might complain... but it works nevertheless)



true, in this he could have copied, but dd does the trick just as well..

---

### Post by Nessa on 2007-09-24
I'm running Ubuntu from the new drive set to master. I see the unallocated space since this IS a bigger drive. I edited my .conkyrc to add "-1" to /media/disk so it would show the proper free space in the ext3 storage partition. The rest remain allocated. Will make some changes later. 

Is this good enough? What else do I need to test before I wipe out my old drive?

---

### Post by Nessa on 2007-09-24
Just double checking the new drive now. But the job is done. 

You guys are awesome! Thanks justleen! =D>

---

### Post by psusi on 2007-09-24
> **Nessa said:**
> No they're not. Read up. The new drive is bigger like I mentioned. Does cp -a copies files and partitions?

cp -a copies files.  You partition the new drive and format it, then copy the files over.  Other than that, all you have to do is install grub to the new drive and the whole system is migrated.  Using dd the way you did leaves the additional space on the new drive unpartitioned.  

> **justleen said:**
> the make and model have ab-so-lu-ty nothing to do with dd...


I didn't say they did; I said if they aren't then you shouldn't use dd for this purpose.  
> **justleen said:**
> 
cp -a is not the same, since it will not do a bit by bit transfer..


Of course they are not the same - that's why I suggested using the latter instead of the former.  If they were the same it wouldn't matter now would it?  

> **justleen said:**
> and as far as the live cd is concernd, for neither cp or dd do you need to enter rescue mode or the live cd.. its perfectly ok to just mount the drive, and copy/dd to the new drive from a "live" system. (yes, al the the stuff  /proc might complain... but it works nevertheless)


You do NOT want to dd from a filesystem that is mounted read-write or you will get a damaged filesystem.  This is why you want to use rescue mode if you boot from the hard disk.  And when copying files, you want to add the -x flag to cp so you only copy the files on the root partition, and not things in /proc, /tmp, /dev, etc, which don't actually exist on disk and should not be put on the new disk.  

> **justleen said:**
> 
true, in this he could have copied, but dd does the trick just as well..

Not really since it leaves the additional space on the new disk unpartitioned.  It also takes a lot longer since it copies EVERYTHING, including the free space.

---

### Post by Nessa on 2007-09-24
I don't mind the unallocated space since I haven't decided what to do with it yet. Most probably for Gutsy.

Thanks psusi. :)

---

### Post by Nessa on 2007-09-24
Now I'm trying to clone a drive in ntfs format but I get this...

```
dd: reading `/dev/hda': Input/output error
687004+0 records in
687004+0 records out
2813968384 bytes (2.8 GB) copied, 155.045 seconds, 18.1 MB/s
dd: reading `/dev/hda': Input/output error
687004+0 records in
687004+0 records out
2813968384 bytes (2.8 GB) copied, 155.081 seconds, 18.1 MB/s
dd: reading `/dev/hda': Input/output error
687004+0 records in
687004+0 records out
2813968384 bytes (2.8 GB) copied, 157.987 seconds, 17.8 MB/s

```

Is "dd" only for ext3?

---

### Post by julian67 on 2007-09-24
I use Clonezilla-live for this kind of thing, it's fast (much faster than dd), has full ntfs support and always works.

---

### Post by Nessa on 2007-09-24
what is that?

---

### Post by julian67 on 2007-09-24
Free disk cloning tool, can do everything :)

[http://clonezilla.sourceforge.net/]("http://clonezilla.sourceforge.net/")

[http://clonezilla.sourceforge.net/clonezilla-live/]("http://clonezilla.sourceforge.net/clonezilla-live/")

> Features of Clonezilla

    * Free (GPL) Software.
    * Filesystem supported: ext2, ext3, reiserfs, xfs, jfs of GNU/Linux, and FAT, NTFS of MS Windows. Therefore you can clone GNU/Linux or MS windows. For other file system, Clonezilla uses dd to dump the whole partition.
    * LVM2 (LVM version 1 is not) under GNU/Linux is supported.
    * Multicast is supported in PXEBoot Clonezilla, which is suitalbe for massively clone. You can also remotely use it to save or restore a bunch of computers if PXE and Wake-on-LAN are supported in your clients.
    * Based on Partimage, ntfsclone and dd to clone partition. However, clonezilla, containing some other programs, can save and restore not only partitions, but also a whole disk.
    * If file system is supported (ext2, ext3, reiserfs, xfs, jfs, fat, ntfs), only used blocks in harddisk are saved and restored. This increase the clone efficiency. For unsupported file system, sector-to-sector copy is done by dd in Clonezilla.
    * By using another free software drbl-winroll, which is also developed by us, the hostname, group, and SID of cloned MS windows machine can be automatically changed.
    * A single machine clone system without installation, Clonezilla live, is also available. 

It can do all kinds of things but also it's perfect for a simple cloning. It only copies used sectors so this alone makes it massively faster than dd. The docs look a little intimidating, best to download the (small) iso and try it out as well as read the docs. Maybe use it on virtual machine drives first so you feel comfortable with it. Previously I used dd or  Acronis True Image (or Norton Ghost on Windows machines) but Clonezilla Live is better than all of them and free in every sense.

---

### Post by Nessa on 2007-09-24
I used parted. Blah. The files are there but it won't boot. Keeps asking for a floppy. Will try another way.

---

### Post by ramjet_1953 on 2007-09-24
Ghost for Linux (G4L) will do a local clone of a HDD.

It makes an exact copy, including GRUB, so that all you have to do is plug the new drive in and go.

It is an iso that you burn to a CDROM and then you boot your system from this.

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

Don't forget that this is an iso image, so burn it slowly, no faster than 4 X.

Regards,
Roger 8)

---

### Post by julian67 on 2007-09-25
I remember trying G4L about a year ago and not liking it at all. It copies drives/partitions using dd.....bllaaaagh!  This is *incredibly* slow and wastes a lot of time. If you clone to a local disk (i.e. SATA, IDE, USB, Firewire) then it has no advantage over simple dd command from the shell. Any tool based on partimage is going to be quicker every time and I believe Clonezilla  can do everything that G4L can do but with greater speed and it has the benefit of better documentation. I think dd based tools were a reasonable choice when partimage didn't have full ntfs read/write support but now that is fixed surely they are redundant?

But anyway if someone wants to use G4L there is a pretty good guide that tries to work around the poor hardware detection (another less than appealing feature!) : [Cloning Hard drives using G4L and Knoppix]("http://bhavesh.freeshell.org/cloninghd.html")

Clonezilla every time for me :)

---

### Post by psusi on 2007-09-25
Looks like your disk is damaged.  Boot into windows and run a chkdsk /f /r and reboot and let it run.

---

### Post by Nessa on 2007-09-25
Nope, the drive is perfectly fine. :)

Just to summarize...

```
sudo dd if=/dev/hda of=/dev/hdb bs=4096 conv=notrunc,noerror
```

Using the Ubuntu LiveCD. This dd command was perfect for what I needed. I was able to clone my 80GB Hitachi Linux drive onto my new 160GB Seagate drive. The rest of the space is unallocated. Cool by me. :)

I ran into problems with it when trying to clone my 40GB XP (dying) drive onto the 80GB Hitachi drive. I don't understand why. Maybe because the drive is dying or maybe because it's NTFS? I thought it was a windows problem so I looked for a windows solution. The 15-day Trial of Acronis True Image did the trick. I did use the Ubuntu LiveCD to split the 80GB into to ~equal partitions.

Problem is solved! Thank you guys! I love this community!=D>:biggrin:

---

### Post by psusi on 2007-09-26
I thought you said you got errors while running dd?  That means the disk is damaged or there is some sort of problem communicating with it.

---

### Post by chrome307 on 2007-09-26
```


sudo dd if=/dev/hda of=/dev/hdb bs=4096 conv=notrunc,noerror


```

Could I use this to copy just a single partition to another drive ?

eg 

**hda1 to hdb1 **


ie



sudo dd if=/dev/**hda1** of=/dev/**hdb1** bs=4096 conv=notrunc,noerror

---

### Post by Nessa on 2007-09-26
I received errors only when I used the dd command on the ntfs drive. I did diagnostics tests on the drive and it was fine.

80GB Hitachi (w/ Ubuntu) > dd > 160GB Seagate (empty) - no problems at all
40GB Maxtor (dying w/ XP) > input/output errors using dd so I used Acronis > 80GB Hitachi - ok

I've only been using Ubuntu for a few months so if I'm wrong please correct me. But from what I've read, YES you can use dd to copy a single partition to another drive.

---

### Post by chrome307 on 2007-09-26
Thanks for letting me know and also the advice but the HDD's as well :)

---

### Post by psusi on 2007-09-26
Both partitions need to be exactly the same size.  If the destination is smaller, the copy will fail because you will run out of space.  If it is larger, the extra space will be wasted.  

Also the process can be rather slow since even the free space is copied, and any fragmentation present in the source filesystem is preserved.  For these reasons it is often better to just format a new filesystem on the new partition, then copy all the files over with cp -a.

---


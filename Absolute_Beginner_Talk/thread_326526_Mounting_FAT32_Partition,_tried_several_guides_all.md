---
title: "Mounting FAT32 Partition, tried several guides all failed"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by ReapeX on 2006-12-27
I tried several guides to mount a FAT32 partition on Edgy Eft.
I would like to see the fat32 partition in my places menu.

One set of commands I tried is:
sudo mkdir /media/hda2
sudo mount /dev/hda2 /media/hda2

The information about the drive from fstab is as follows:
# /dev/hda2
UUID=431D-24DD  /shareddata     vfat    defaults,utf8,umask=007,gid=46 0       1

I added the following data to end of the fstab file:

/dev/hda2 /data vfat iocharset=utf8,umask=000 0 0

However, I still cannot see the drive...is the fact that it says shareddata a problem?


Thanks in Advance

---

### Post by Zimmer on 2006-12-27
> **ReapeX said:**
> I tried several guides to mount a FAT32 partition on Edgy Eft.
I would like to see the fat32 partition in my places menu.

One set of commands I tried is:
sudo mkdir /media/hda2
sudo mount /dev/hda2 /media/hda2

The information about the drive from fstab is as follows:
# /dev/hda2
UUID=431D-24DD  /shareddata     vfat    defaults,utf8,umask=007,gid=46 0       1




Thanks in Advance
is that the exact entry in your fstab file ?, if so the # is commenting the line out so your share is not being mounted at boot. What does Administration >Disks tell you from the partition tab? is your vfat partition really hda2? What does that give for its Access path?

The command to mount your vfat partition in fstab should be something more like
/dev/hda2 /shareddata vfat iocharset=utf8,umask=000 0 0

Assuming the partition is dev/hda2   and you have created a directory  /shareddata  as the mount point.

check out 
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
for more detail

---

### Post by Frank Golden on 2006-12-27
> **ReapeX said:**
> I tried several guides to mount a FAT32 partition on Edgy Eft.
I would like to see the fat32 partition in my places menu.

One set of commands I tried is:
sudo mkdir /media/hda2
sudo mount /dev/hda2 /media/hda2

The information about the drive from fstab is as follows:
# /dev/hda2
UUID=431D-24DD  /shareddata     vfat    defaults,utf8,umask=007,gid=46 0       1

I added the following data to end of the fstab file:

/dev/hda2 /data vfat iocharset=utf8,umask=000 0 0

However, I still cannot see the drive...is the fact that it says shareddata a problem?


Thanks in Advance
One error I can see is the fstab entry should be 
/dev/hda2       /media/hda2     vfat    iocharset=utf8,umask=000    0       0

after adding the correct entry 
mount -a
should mount your Fat32 partition and give you a desktop icon.

---

### Post by ReapeX on 2006-12-29
> **Zimmer said:**
> is that the exact entry in your fstab file ?
[/B]Yes, my new entry is:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=5db61eba-3e7b-40b8-a285-6d0651cb9dc2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=4bf2c555-fca5-442f-a459-739b4ae96dee /home           ext3    defaults        0       2

/dev/hda2 UUID=431D-24DD  /shareddata     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=287450CC74509DFE /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=bc730911-ba9f-469c-a6ad-785c30231f0a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hda2 /data vfat iocharset=utf8,umask=000 0 0

[B]What does Administration >Disks tell you from the partition tab? 
[/B]Oddly, that menu option isn't listed in my Edgy Eft....

**Is your vfat partition really hda2?**
As far as I know, yes.

** What does that give for its Access path?**
Do you mean mount point?


Psycho Path is a great site, I have been using it before I started posting on the forums.

---

### Post by ReapeX on 2006-12-29
Zimmeran's solution didn't work but Frank Golden's did (I guess I need to more about whatever the  unmask command does)

But thank you Zimmeran and Frank Golden you saved me hours of extra troubleshooting.

Now all I have to do is figure out why Edgy Eft doesn't have a Disk option in System->Administration

---

### Post by ReapeX on 2006-12-29
[double post, ignore]  .

---

### Post by Zimmer on 2006-12-29
> **ReapeX said:**
> 

Now all I have to do is figure out why Edgy Eft doesn't have a Disk option in System->Administration
Have you tried enabling it via the Alacarte Menu Editor  ?

:)

---

### Post by ReapeX on 2006-12-29
never even heard of that but I'll look into just as soon as I fix my NEW problem.

As soon as I edit my fstab file to mount my NTFS partition my wireless connection changed to wired in networking.

See the following thread:
[http://www.ubuntuforums.org/showthread.php?p=1945311#post1945311](http://www.ubuntuforums.org/showthread.php?p=1945311#post1945311)

Mounting the FAT32 Partition was easy, fixing my wireless connection has turned into an entirely different ball game o_o.

Without wireless I can't even look up the Alcarate menu editor

---

### Post by Zimmer on 2006-12-29
> **ReapeX said:**
> never even heard of that but I'll look into just as soon as I fix my NEW problem.

As soon as I edit my fstab file to mount my NTFS partition my wireless connection changed to wired in networking.

See the following thread:
[http://www.ubuntuforums.org/showthread.php?p=1945311#post1945311](http://www.ubuntuforums.org/showthread.php?p=1945311#post1945311)

Mounting the FAT32 Partition was easy, fixing my wireless connection has turned into an entirely different ball game o_o.

Without wireless I can't even look up the Alcarate menu editor

? it is in accessories.....

---

### Post by Frank Golden on 2006-12-29
> **ReapeX said:**
> Zimmeran's solution didn't work but Frank Golden's did (I guess I need to more about whatever the  unmask command does)

But thank you Zimmeran and Frank Golden you saved me hours of extra troubleshooting.

Now all I have to do is figure out why Edgy Eft doesn't have a Disk option in System->Administration
Zimmer's didn't work because fstab was trying to mount to a nonexistenant mount point.
You had created a /media/hda2 mount point earlier. My fstab entry merely pointed to that mount point. If you had had a /shareddata mount point that is where the volume would be mounted. It would not end up on the desktop however. That is what the /media folder is special for, a volume mounted on a mount point there shows up as an icon on the desktop.
All the rest of the entry including the umask was correct. BTW your welcome.

---

### Post by ReapeX on 2006-12-31
Ah thanks, I sorta guessed that about the mount point after it started working.

But thank you!

I may have to reload Ubuntu on Monday though, the problems with the OS keep multypling see above link.

---


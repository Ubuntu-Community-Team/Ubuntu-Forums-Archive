---
title: "folder permissions on my windows partition"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by chevriley on 2008-04-16
i have ubuntu running on a partition of my HDD with XP running in the other partition and an external NTFS HDD. im worried about how easy it is to delete windows system files and my important documents as ubuntu doesn't treat them any differently to anything else. i wanna be able to access them in ubuntu without having to be extra extra careful.

folder permissions is what i wanna figure out, i spose. the properties dialog says im not 'root' so i can't alter them. i'd like to set 5 or 6 folders (incl subfolders) to read only in linux, unless i choose to remove read-only status again,

if i do alter them, i presume it won't affect how they are interpreted by windows, yeah?

P.S. im not getting a popup when i delete files from here either, as my preferences specify.... are they being moved to trash? where is trash because its not in the orange trash box for files from theNTFS folders.

thanx.

---

### Post by chevriley on 2008-04-16
P.P.S. please talk to as you would a complete moron. i know there are a couple of other threads on roughly this matter, but they went way over my head.

---

### Post by bodhi.zazen on 2008-04-16
NTFS does not support Unix ownership or permissions. The ownership and permissions of the files aer set at the time of mounting a ntfs partition as a part of the mount process, ie the mount porcess prepairs the file system (parition) for use.

You can only change ownership and permissions by re-mounting the ntfs partition.

You set these things with options in the mount command or fstab.

sudo mount /dev/sdxy /media/windows -o uid=1000,gid=100,umask=007

uid = user ID # . To see your uid use the command id or look in /etc/passwd
gid = group ID

umask sets permissions.

Or an entry in fstab

/dev/sdxy /media/windows ntfs-3g uid=1000,gid=100,umask=007 0 0

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

[Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by chevriley on 2008-04-16
oky, thanks for the help anyway.

---


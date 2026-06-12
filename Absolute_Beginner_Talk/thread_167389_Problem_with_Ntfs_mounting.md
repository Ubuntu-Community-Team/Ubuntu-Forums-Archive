---
title: "Problem with Ntfs mounting"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Nudgesome on 2006-04-28
Heyas, I'm new to Linux.. as i had only installed it yesterday
i'm having problems with mounting my ntfs partition, ive followed many guides and when i enter
```
sudo mount -a 
```

it says
```
wrong fs type, bad option, bad superblock on /dev/hda2,
missing codepage or other error
in some cases useful info is found in syslog - try
dmesg | tail or so 
```

Help please

---

### Post by jazzmuzik on 2006-04-28
Post the contents of /etc/fstab.

Try this:

more /etc/fstab

---

### Post by Nudgesome on 2006-04-28
okay

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2       /mnt/ntfs1      ntfs    defaults,ro,unmask=0222     0       0

---

### Post by jazzmuzik on 2006-04-28
The word "unmask" is incorrect. It should be "umask".

I've mounted an ntfs drive in Linux only once in my life and that was about a month ago. I studied the threads in this forum to achieve it. As I recall I had to install a package or two and the software only allowed read only on the ntfs drive. Write was considered unstable still.

Have you read this thread?

[http://www.ubuntuforums.org/showthread.php?t=142481](http://www.ubuntuforums.org/showthread.php?t=142481)

Does /mnt exist on your system? Dumb question I know, but sometimes the simplest things... Does /mnt/ntfs1 exist?

Are you coming from the RedHat world? /mnt is a Redhat/Fedora convention. Ubuntu mounts drives at /media.

---

### Post by yager on 2006-04-28
[QUOTE=jazzmuzik] Ubuntu mounts drives at /media.[/QUOTE]

I successfully mounted my Windows partitions under a directory I created at /Windows/C and /Windows/D.

As sudo, I created the directory /windows first and then made the directory C and D inside Windows.

Next I had to set the permissions on both to make sure that everyone could read and execute from C and D BEFORE I mounted /dev/hda1 and /dev/hdb1 to the directories.

Then I setup my FStab file to mount both partitions at those locations.

---

### Post by Nudgesome on 2006-04-29
Thanks for that guide Jazzmusik
It's all up and running now... and to answer your question the only reason i used /mnt was because my friend was trying to help me and since he was a Redhat user he was telling me to direct the mount there

---

### Post by jazzmuzik on 2006-04-29
There's no problem mounting from /mnt. It just might make it more cohesive to use /media.

---


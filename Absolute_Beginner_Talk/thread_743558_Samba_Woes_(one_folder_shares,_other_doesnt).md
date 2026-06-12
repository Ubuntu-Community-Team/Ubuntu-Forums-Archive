---
title: "Samba Woes (one folder shares, other doesnt)"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by mdk7 on 2008-04-02
Ok, weird problem here.  

Attached screenshot probably shows it best.  Folder on the left shares fine, folder on the right has been making me tear my hair out. 

Even as root I can't change the permissions from "plugdev" for group or change the permissions for "other" (they change back right away).

Also, it's worth noting that the folder on the left is connected via external hard drive whereas the one on the right is an internal drive partition (I'm trying to share the entire partition if that matters...so /media/sda2 basically)

Any ideas?

Edit:  Here's the end of the samba.conf

[Music]
path = /media/sdb1/Music
available = yes
browsable = yes
public = yes
writable = no

[Guitar]
path = /media/sda1
available = yes
browsable = yes
public = yes
writable = no

---

### Post by Iowan on 2008-04-02
You didn't include (or I missed) the definition for the /media/sda2 share. Have you tried the **chown** command from a terminal?

---

### Post by mdk7 on 2008-04-02
Sorry the second one there is actually sda2 it's just listed wrong.  I removed it and readded it as:

[sda2]
path = /media/sda2
available = yes
browsable = yes
public = yes
writable = no

Tried chown, didn't work:
```

mike@mike-desktop:/media$ sudo chown root:root /media/sda2
mike@mike-desktop:/media$ ls -l

drwxrwx--- 1 root plugdev 16384 2008-03-31 01:45 sda2


```

---

### Post by superprash2003 on 2008-04-02
your sda2 properties is set to NONE for OTHERS.. you might want to try changing that

---

### Post by mdk7 on 2008-04-03
Actually after some digging I figured it out.  It involved changing the umount parameter in fstab.  I think (but am not positive) that this issue arose because internal drives must be 'owned' by the root and belong to plugdev group.

Anyway I resolved it following the advice [here]("http://ubuntuforums.org/archive/index.php/t-1684.html").  Hopefully it helps out other people who encounter this issue.

> Ok, this is an old thread, but I thought I'd post and tell anyone else how to do this.

you must edit your /etc/samba/smb.conf
For some reason, when you share an ntfs drive throught the ubuntu gui, the path to the share doesn't get set in the smb.conf correctly. So, you need to edit you smb.conf manually. Mine looks like this:

[Video]
path = "/media/hdc1/Shared Files/Video"
available = yes
browseable = yes
public = yes
writable = yes

Where my shared directory called "Video" is located on an NTFS drive in a sub dir "Shared Files/Video"

Then, you need to edit you /etc/fstab so that the dir is browsable. Setting umask to 001 didn't work for me, but 0222 did. Mine looks like this:

/dev/hdc1 /media/hdc1 ntfs defaults,nls=utf8,umask=0222,gid=46 0 1

Now, when I connect to the computer through smb shares, the "Video" directory points straight to my ntfs directory.

... anyway, I hope that helps someone.

You can read more about [umask]("http://en.wikipedia.org/wiki/Umask") on Wikipedia to figure out the rationale behind it.

Also if anyone can succinctly explain why this problem occurred or can point me to a resource about it please do.  

It seems weird that this wouldn't be more of an issue for people sharing through Samba...I'm thinking it might be something I'm doing incorrectly (although I doubt most people need to share an entire drive/partition like that).

---

### Post by Xiong Chiamiov on 2008-04-03
I seem to remember having some weird options (including umask) when the drive I was sharing was FAT, but then it went away when I reformatted it to ext3.  But then again, sometime in that process I got rid of Samba and went straight NFS since I switched all our computers to Linux.

---

### Post by joshrobinson on 2008-04-03
> **Xiong Chiamiov said:**
> I seem to remember having some weird options (including umask) when the drive I was sharing was FAT, but then it went away when I reformatted it to ext3.  But then again, sometime in that process I got rid of Samba and went straight NFS since I switched all our computers to Linux.

vfat  defaults,umask=0000 0 0

:-P i have a linux fileserver with a fat32 drive on it, thats the fstab command i use for that drive to get the permissions right

---

### Post by Xiong Chiamiov on 2008-04-03
> **joshrobinson said:**
> vfat  defaults,umask=0000 0 0

:-P i have a linux fileserver with a fat32 drive on it, thats the fstab command i use for that drive to get the permissions right

Yeah, I installed Windows on my fileserver first, then dual-booted, then just Kubuntu, then finally Xubuntu.  And after all that I installed Kubuntu on both my computer and my roomie's.  The only reason I reformatted the hdd from fat was that I ran into problems with the filesize limit (4gigs or something).

---

### Post by joshrobinson on 2008-04-03
> **Xiong Chiamiov said:**
> Yeah, I installed Windows on my fileserver first, then dual-booted, then just Kubuntu, then finally Xubuntu.  And after all that I installed Kubuntu on both my computer and my roomie's.  The only reason I reformatted the hdd from fat was that I ran into problems with the filesize limit (4gigs or something).

yup 4gigs, i have multiple drives in the fileserver, so anything over 4gig i just put on one of the other drives, its a 300gig and its almost full,  i would reformat it but its just too time consuming to back all that data up and then copy it back to the drive

---

### Post by mdk7 on 2008-04-03
Weird thing is that this is an NTFS formatted drive, not FAT.  You think it's still the same issue?  I would use an all Linux setup but my local network has some XP machines on it.

---

### Post by joshrobinson on 2008-04-03
> **mdk7 said:**
> Weird thing is that this is an NTFS formatted drive, not FAT.  You think it's still the same issue?  I would use an all Linux setup but my local network has some XP machines on it.

you just had some permissions problems, it happens all the time, i only posted my fat32 fstab line because Xiong Chiamiov was talking weird umask commands

---


---
title: "Need a little help with the mv command"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by LordExcelsior on 2006-11-15
I just switched to linux all together last night.  I'm finding it different, but I am working my way through it.

I don't know many commands in the terminal which is why I have I have a question for you all.  I backed up my firefox bookmarks onto an External HDD before I switched, now I wish to replace the default FF bookmarks file with mine.

I am using a Seagate External HDD which my computer refers to as "SEA_DISK"
this is the code that I use after using the "su" command.

```
mv SEA_DISK/bookmarks.html etc/firefox/profile/bookmarks.html
```

and this is the error I get

```
mv: cannot stat `SEA_GATE/bookmarks.html': No such file or directory
root@Ikari:/home/gene# 
```

I assume I am not putting in the correct path for the HDD, but I am unsure that the path would be in linux.

Thanks for the help!

---

### Post by po0f on 2006-11-15
LordExcelsior,

Are you sure the disk is mounted?  Please post the output of:
```
$ mount
```
(The dollar sign represents your prompt, it's not part of the command.)

[EDIT]

Also, how many hard drives does this system have?

---

### Post by ThrobbingBrain66 on 2006-11-15
If your hard drive is mounted within nautilus, you'll find it under /media or /mnt in the file system

use that path when you are trying to copy the bookmarks, instead of just SEA_GATE

---

### Post by LordExcelsior on 2006-11-15
Oh dear, I should have said it was a USB drive.  Sorry!!! :(

---

### Post by cwaldbieser on 2006-11-15
> **LordExcelsior said:**
> I just switched to linux all together last night.  I'm finding it different, but I am working my way through it.

I don't know many commands in the terminal which is why I have I have a question for you all.  I backed up my firefox bookmarks onto a HDD before I switched, now I wish to replace the default FF bookmarks file with mine.

I am using a Seagate HDD which my computer refers to as "SEA_DISK"
this is the code that I use after using the "su" command.

```
mv SEA_DISK/bookmarks.html etc/firefox/profile/bookmarks.html
```

and this is the error I get

```
mv: cannot stat `SEA_GATE/bookmarks.html': No such file or directory
root@Ikari:/home/gene# 
```

I assume I am not putting in the correct path for the HDD, but I am unsure that the path would be in linux.

Thanks for the help!

The drive must be mounted before you can access the filesystem on it.  To see what filesystems are mounted, issue this command:
```

$ mount

```

You will see output that shows devices (e.g. /dev/hdb1) to mount points in your filesystem.  For example, a SCSI drive mounted as your root file system might look like:
```

/dev/sda2 on / type ext3 (rw,errors=remount-ro)

```

So if your seagate drive is mounted, the mount point will show up there.  If it is something like "/mnt/SEA_GATE", that means that you can list the directory contents with
```

$ ls /mnt/SEA_GATE

```
The case is important.  

If it is not mounted, you will need to first mount it somewhere.  Was the drive originally for Windows?  Do you know if it is a FAT32 or NTFS file system, or is it something else?

---

### Post by Redache on 2006-11-15
EDIT: Irrelevant, I took a while typing it and it now seems it's a USB drive.

---

### Post by LordExcelsior on 2006-11-15
> **Redache said:**
> EDIT: Irrelevant, I took a while typing it and it now seems it's a USB drive.

Yeah, sorry, I forgot to mention that.

---

### Post by taurus on 2006-11-15
Open a terminal and paste this output here!

```
df -h
```

---

### Post by szf on 2006-11-15
> **LordExcelsior said:**
> ```
mv SEA_DISK/bookmarks.html etc/firefox/profile/bookmarks.html
```

Whether SEA_DISK mounted in /media or /mnt - don't forget the leading slash on the CLI. Alternately, Nautilus will help flatten out the learning curve.

Otherwise, something like:

```

$ mv /media/SEA_DRIVE/bookmarks.html $HOME/.mozilla/firefox/<something random>.default/

```

Where <something random> is really truly something random (i.e. dtr90un8 (assuming you've run ffox at least once)).

---

### Post by LordExcelsior on 2006-11-15
> **taurus said:**
> Open a terminal and paste this output here!

```
df -h
```


```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             270G  2.3G  254G   1% /
varrun               1014M   80K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb             10M  144K  9.9M   2% /proc/bus/usb
udev                   10M  144K  9.9M   2% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   18M  997M   2% /lib/modules/2.6.17-10-generic/volatile
/dev/sda1             150G   39G  111G  26% /media/SEA_DISC
```

EDIT: OK, never mind, that dident work.

---

### Post by LordExcelsior on 2006-11-16
I'm still having trouble.  I found out that the file is located at:

media/SEA_DISC/bookmarks.html

but I am still getting the same error message.

I can transfer the files by clicking and dragging no problem, the only reason why I am using the terminal is because I need root abilities because of some permission thing to edit files.

---

### Post by po0f on 2006-11-16
LordExcelsior,

Have you tried:
```
$ sudo mv **/**media/SEA_DISC/bookmarks.html ~
```

You might not be able to tell, but that slash in front is bold.  I didn't see anywhere in the thread where you tried that.  Also, you could just copy it as a regular user instead of moving it:
```
$ cp /media/SEA_DISC/bookmarks.html ~
```

---


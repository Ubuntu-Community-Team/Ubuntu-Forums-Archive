---
title: "How can I access my floppy"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by rizzyc on 2006-01-15
I have a floppy I need to access with important documents such as resumes and  stuff. I can not access the 1.44 floppy. The error message i get is

[B]Warning: device /dev/fd0 is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount[/B]

---

### Post by cwaldbieser on 2006-01-15
[QUOTE=rizzyc]I have a floppy I need to access with important documents such as resumes and  stuff. I can not access the 1.44 floppy. The error message i get is

[B]Warning: device /dev/fd0 is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount[/B][/QUOTE]
Edit your /etc/fstab file (e.g. "sudo gedit /etc/fstab").  Find the line that looks similar to this:
```

/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

```

and comment it out like this:
```

#/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

```

Not sure if you will need to restart something to see the results, but the "pmount" command doesn't like to interfere with mount points that are entered in /etc/fstab (presumably for use with "mount").  "pmount" is the command used by normal users to mount their USB drives, etc.

---

### Post by patrick295767 on 2006-01-15
```
sudo mount /dev/fd0 /media/floppy0
```
  
or 
```
sudo mkdir /mnt/fd0
sudo mount /dev/fd0 /mnt/fd0
```

---

### Post by Sef on 2006-01-15
I> I found this other post which tells how to automount the floppy drive. That post is listed at the bottom of the page.

This other post of mine tells how I got my floppy drive to automatically boot:


Quote:
There is a bug in Breezy, so often the floppies won't automount. To get them to automount, go to this site:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/)

1) Download pmount_0.9.6-1~breezy1_i386.deb

2) Install --> sudo dpkg -i pmount_0.9.6-1~breezy1_i386.deb

3) enter password

4) After it finishes installing, your floppy should mount and umount automatically.

I found that bug and fix from this thread: [http://ubuntuforums.org/showthread.php?t=93139&page=2](http://ubuntuforums.org/showthread.php?t=93139&page=2)

Note: I got it on the first time, but since then I have not be able to get it automatically get my floppy to automount.  (Have reinstalled my os a few times.)

---

### Post by patrick295767 on 2006-01-15
```
apt-get -f -y install rox-filer
```
  
If ur /etc/fstab is correct, u'll un-/mount very very easily ur floppy disk !
  
```
xterm
rox /mnt/fd0 &
```

 Greetz

---

### Post by rizzyc on 2006-01-15
[QUOTE=cwaldbieser]Edit your /etc/fstab file (e.g. "sudo gedit /etc/fstab").  Find the line that looks similar to this:
```

/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

```

and comment it out like this:
```

#/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

```

Not sure if you will need to restart something to see the results, but the "pmount" command doesn't like to interfere with mount points that are entered in /etc/fstab (presumably for use with "mount").  "pmount" is the command used by normal users to mount their USB drives, etc.[/QUOTE]

Wow lots or responds on this one, thanks this one was the simplest solution and it works. Thanks

---


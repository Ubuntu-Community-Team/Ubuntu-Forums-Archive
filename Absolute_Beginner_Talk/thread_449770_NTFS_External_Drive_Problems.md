---
title: "NTFS External Drive Problems"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by dantes on 2007-05-20
Alright, to start it off im a newbie but im going to try my best to describe the problem.

The external drive is mounted okay as ntfs-g3. In ntfs i couldnt write(it was read only).
Well the problem is that if i decide to, lets say, unrar a file. Sometimes it will just go black and retstart on me. Is this common?

---

### Post by dantes on 2007-05-20
I thought it might be gnome but im using enlightenment now and its still doing it. Its not only when using unrar, but when im watching a file through VLC even.

Does anyone have ANY clue?

---

### Post by taurus on 2007-05-20
Do you mount it by hand, from a terminal, or do you mount it through /etc/fstab?

---

### Post by dantes on 2007-05-20
> **taurus said:**
> Do you mount it by hand, from a terminal, or do you mount it through /etc/fstab?

When using gnome, i let gnome do it.
When using enlightenment i do it by terminal

---

### Post by taurus on 2007-05-20
And when you mount it from a terminal, what is the command that you use?

---

### Post by dantes on 2007-05-20
> **taurus said:**
> And when you mount it from a terminal, what is the command that you use?

sudo mount -t ntfs-3g /dev/sde1 /media/SEA_DISK/

---

### Post by taurus on 2007-05-20
And can you save a file to /media/SEA_Disk right now?

What's the output of this command?

```
ls -la /media
```

---

### Post by dantes on 2007-05-20
miles@tzu:~$ ls -la /media
total 200
drwxr-xr-x  5 root root   4096 2007-05-20 17:40 .
drwxr-xr-x 21 root root   4096 2007-05-19 11:57 ..
lrwxrwxrwx  1 root root      6 2007-05-18 19:19 cdrom -> cdrom0
drwxr-xr-x  2 root root   4096 2007-05-18 19:19 cdrom0
drwxr-xr-x  2 root root   4096 2007-05-20 14:03 disk
-rw-r--r--  1 root root      0 2007-05-20 17:40 .hal-mtab
--wxr-x---  1 root root      0 2007-04-15 06:56 .hal-mtab-lock
drwxrwxrwx  1 root root 188416 2007-05-20 18:13 SEA_DISK

oh and yes i can write. if i mount it just using ntfs its read only. but with ntfs-3g its r/w.

---

### Post by taurus on 2007-05-20
Can you just copy a random file to /media/SEA_DISK now?  Would it let you write to it?

p.s.  But of course.  NTFS driver is for read-only so if you want to write to it, you must use ntfs-3g driver.

---

### Post by dantes on 2007-05-20
> **taurus said:**
> Can you just copy a random file to /media/SEA_DISK now?  Would it let you write to it?

p.s.  But of course.  NTFS driver is for read-only so if you want to write to it, you must use ntfs-3g driver.

miles@tzu:/media/SEA_DISK$ cd ~

miles@tzu:~$ ls
Desktop    movies              repo_key.asc    TransGaming_Drive
Examples  lang    overall_footer.tpl  repo_key.asc.1

miles@tzu:~$ mv repo_key.asc /media/SEA_DISK/

miles@tzu:~$ ls
Desktop   movies              repo_key.asc.1
Examples  lang    overall_footer.tpl  TransGaming_Drive

yeah it worked

---

### Post by taurus on 2007-05-20
Now that you have just moved repo_key.asc to /media/SEA_DISK, see if it's there.

```
ls -la /media/SEA_DISK
```

---

### Post by dantes on 2007-05-20
yeah it showed up

---


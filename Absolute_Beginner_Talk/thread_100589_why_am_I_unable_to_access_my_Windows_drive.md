---
title: "why am I unable to access my Windows drive?"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by wr0x2 on 2005-12-07
When I first installed breezy, I mounted my windows drive (/dev/sda1) under /media/windows. Everything worked fine and I could access everything under the drive. Now, I can only get into the drive as root. Somehow, I guess the permissions got corrupted. When I try to chmod 644 the directory as root (it's NTFS, and read only) I get an comment about it being a read only fs and I'm still unable to access the drive once I leave the root shell.

I'm sure this is an easy fix, but it's annoying. In case it's needed, here's my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/windows  ntfs    ro,user         0       0

```

---

### Post by Joe_CoT on 2005-12-07
[Q: How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only?](http://ubuntuguide.org/#automountntfs)

---

### Post by wr0x2 on 2005-12-07
That guide didn't help me, but it looks similar to the reference I used to mount my windows drive in the first place. also, chown returns the same error chmod does.

Note that I said my drive USED to be accessable.

---

### Post by Joe_CoT on 2005-12-07
> That guide didn't help me, but it looks similar to the reference I used to mount my windows drive in the first place

o rly? have you tried changing the line to this:
```
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```

then do
```
mount -a
```
and tell me if it works or not.

---

### Post by aysiu on 2005-12-07
Do exactly as I tell you in exactly the order I tell. Do not deviate from these instructions.

```
sudo umount /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Replace this line: ```
/dev/sda1       /media/windows  ntfs    ro,user         0       0
``` with this line ```
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222         0       0
``` Save (Control-X), confirm (y), and exit (Enter). Then ```
sudo mount -a
```

---

### Post by Justus on 2005-12-08
Now I'm really confused, because it's sounding now like NTFS *can* be mounted (and written to) under Ubuntu. But I thought it can't be. Sorry for all the noobish questions, but I am, after all, a noob;)

---

### Post by aysiu on 2005-12-08
[QUOTE=Justus]Now I'm really confused, because it's sounding now like NTFS *can* be mounted (and written to) under Ubuntu. But I thought it can't be.[/QUOTE] It can be mounted and read from but not written to.

---

### Post by Ahrel on 2005-12-11
Finally stumbled across a thread with some info on this!  And yes, it works, I can read my NTFS drives without accessing them as root/superuser -- no I can not write to them (nor do I really care about that).  Thanks for the link...I know I should have read it, but that guide is large -- should jsut search in there everytime I am wondering about something (if I can find the right words for it).

Everything is so simple if you know what commands to use :p.  Now I can ditch that right-click "open as root" script.

Just confirming for the skeptical.

---

### Post by Gray. on 2005-12-11
I followed your instructions aysiu but when I ```
sudo mount -a
``` I get ```
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

``` BUT, when I ```
sudo mount /dev/hda1 /media/windows
``` it works. What gives?

---

### Post by Ahrel on 2005-12-11
Did you happen to copy and paste the lines?

When I mount I just type: sudo mount /media/hda1

I don't know much of anything about these commands, but it sounds like maybe in your fstab you have one that says /media/windows, where it should say /dev/hda1.

Paste your fstab here so I (and others that know more about it :p) can look at it.

---


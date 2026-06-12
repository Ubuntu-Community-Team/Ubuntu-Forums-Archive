---
title: "Filesystem type..."
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by PBeck929 on 2006-08-01
ok everybody, so I just installed Xubuntu and I'm trying to accomplish the simple task of mounting a cd, but I keep get the message saying, "please specify filesystem type".


root@PBeck:~# mount -t auto /dev/hda /mnt/cdrom
mount: you must specify the filesystem type


can somebody please help me figure this out...  my two hard disk drives are Sata so that's why my CD/DVD burner is labeled "hda"...

---

### Post by kazuya on 2006-08-01
When you pop in the CD, I imagine it should just yield an option to open it. Are you using dapper? 

Make sure, the CD is not in use by another application as well. This may be far fetched.

---

### Post by dbw on 2006-08-01
There is a utility called gnome-volume-manager which should automount for you, if you use gnome or a gnome-derivative desktop enviroment.  I am not sure what KDE uses.  If you do not have this, run:
 ```
sudo apt-get update
sudo apt-get install gnome-volume-manager

```
Or use aptitude instead of apt-get.  If you (really want)/ (are forced) to use the command-line command, I have two suggestions:
1.  cds tend to be type iso9660
2.  your cd drive SHOULD be in /etc/fstab, so you SHOULD be able to run simply: ```
mount /media/cdrom0
```

by the way, my /etc/fstab entry looks like this:
```
/dev/hdg        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
check out the man pages for fstab, mount, and pmount if that entry looks funny to you.

good luck!

---

### Post by PBeck929 on 2006-08-01
I'm actually using Xubuntu, and I use Xfce as my environment... don't know if that matters, but is there anything in the synaptic package app that helps scan and diagnose hardware?  I mean obviously the OS "saw" my cd because I installed it, but ever since then, it says something about a blocked device or something to that effect...

---

### Post by professor_chaos on 2006-08-01
there is a disk manager called "disks-admin"
from the terminal type ```
disks-admin
```
It won't let you mount it from there, but you can atleast see its properties.

---

### Post by PBeck929 on 2006-08-01
yep, I've been there plenty of times, but it doesn't tell me anything... it says under "device"... "/dev/hda", but I still have absolutely no idea how to mount and how to unblock it?

---

### Post by tehnad on 2006-08-02
I am a little confused about what is going on here.  If you are mounting the cdrom then why are you mounting /dev/hda?  Shouldn't the mount command be  mount /dev/cdrom /mnt/cdrom ?  Just asking in case I am not understanding what is really going on and there is an opportunity to learn something new.

update> type: man mount  to get a good description of how to solve your issue.

---

### Post by PBeck929 on 2006-08-02
I did that and it sill says, "wrong fs, blocked device..."

It keeps popping up that I'm not using the proper filesystem...

---


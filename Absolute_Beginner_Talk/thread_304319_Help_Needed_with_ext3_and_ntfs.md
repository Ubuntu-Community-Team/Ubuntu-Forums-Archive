---
title: "Help Needed with ext3 and ntfs"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by kiyometane on 2006-11-21
Hello i got 2 questions ,

1) How do i delete a restricted file. I'm trying to delete a file i created in root( /root/"backupstuff")

2)How do i make edgy see my windows hardrive so that i can access it
Thanks in advance

---

### Post by taurus on 2006-11-21
1.  Open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo rm /root/backupstuff
```
2.  [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by kiyometane on 2006-11-21
The link you gave me was not that helpfull, it was not meant for edgy users.
And the guy have one hardrive with both os.
but i have 2 separate hhds, on with edgy the other with xp
Is there another was i could it?

---

### Post by taurus on 2006-11-21
Are you talking about mounting your XP?  I guess I just have to show you by hand how to mount it then!!!  What is the output of this command from a terminal then?

```
sudo fdisk -l
```
p.s.  Just so you know.  You just replace /dev/hda1 with whatever your XP is on!!!

---

### Post by eriefisher on 2006-11-21
The how-to on aysiu site is right on the money. You just have to insert you own information where needed. 1,2 or 10 harddrives, it does not matter. What matters is the the location on the drive and mount point.

---

### Post by kiyometane on 2006-11-21
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19209   154296261   83  Linux
/dev/sdb2           19210       20023     6538455    5  Extended
/dev/sdb5           19210       20023     6538423+  82  Linux swap / Solaris
kyo@kyo-desktop:~$

---

### Post by taurus on 2006-11-21
So, you want to mount your /dev/sda1 on /media/windows.  Open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo cp /etc/fstab  /etc/fstab.bak <-- make a back up copy in case you need to use it later...
gksudo gedit /etc/fstab
```
Now, scroll all the way to the end and add this line.

```
/dev/sda1   /media/windows   ntfs   nls=utf8,umask=0222   0   0
```
Save it and from the terminal, create a mount point and mount it.

```
sudo mkdir /media/windows
sudo mount -a
df -h <-- you should see your /dev/sda1 mounted on /media/windows
```

---

### Post by kiyometane on 2006-11-21
thanks here is the output 

kyo@kyo-desktop:~$ gksudo gedit /etc/fstab
(gedit:10785): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
kyo@kyo-desktop:~$ sudo mkdir /media/windows


mkdir: cannot create directory `/media/windows': File exists
kyo@kyo-desktop:~$ sudo mount -a
kyo@kyo-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             145G  3.1G  135G   3% /
varrun                1.5G  164K  1.5G   1% /var/run
procbususb             10M  132K  9.9M   2% /proc/bus/usb
udev                   10M  132K  9.9M   2% /dev
/dev/sda1              75G   62G   13G  83% /media/windows
kyo@kyo-desktop:~$

---

### Post by kiyometane on 2006-11-21
Thanks man
it worked, ur a genius, It has 2 weeks i was looking into forums to solve the issue.

---

### Post by taurus on 2006-11-21
> **kiyometane said:**
> Thanks man
it worked, ur a genius, It has 2 weeks i was looking into forums to solve the issue.
Actually, I am not a genius.  I just have a little experience with this kind of stuff!  ;) 

Now that your problem is solved, have fun.

---


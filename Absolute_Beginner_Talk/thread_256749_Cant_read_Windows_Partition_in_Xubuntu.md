---
title: "Cant read Windows Partition in Xubuntu"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Irish J on 2006-09-13
After using KDE for a while i decided to switch to Xfce (apt-get install xubuntu-desktop).

Now I cant view my windows partition.  Using the disk manager program in System -> Disks I can point hda1 to mount at /home/j/Windows, but when I try to view it in Thunar nothing shows up.  When I try and load my playlist in xmms it says "not accessable".  I'm thinking it's a CHMOD issue?  How can i rectify?  Should i edit /etc/fstab?

sudo mount returns:

```

j@parkhead:~$ sudo mount
/dev/hdd1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/hda1 on /home/j/Windows type ntfs (rw)

```

Help!

---

### Post by Najand on 2006-09-13
Hmm, it has been already mounted...  Although home directory is not a very suitable place to mount a device/file, I don't think there is a problem with that... Can you cd to it inside a terminal?

---

### Post by Najand on 2006-09-13
PS. I am not sure about XFCE, but in gnome only partitions that have been mounted in:
"/media"
can be seen in Nautilus. I am not sure, but a while ago I read something similar about XFCE too. Is it possible to try it and make a directory like Windows in /media and then change the mount point to /media/Windows?

---

### Post by aysiu on 2006-09-13
Try pasting in these terminal commands: ```
sudo umount /dev/hda1
mkdir /home/j/Windows
``` If it says /home/j/Windows already exists, that's okay--we're just making sure it *does* exist ```
sudo nano -B /etc/fstab
``` Add this line at the end: ```
/dev/hda1 /home/j/Windows ntfs nls=utf8,umask=0222 0 0
``` Save (Control-X, Y, Enter) ```
sudo mount -a
```

**Edit** If your /etc/fstab already has a line about /dev/hda1, you need to delete (Control-K) that line before you add in the new line I gave you.

---

### Post by Irish J on 2006-09-13
Thanks, i'll try that now.

---

### Post by Irish J on 2006-09-13
I combined both of your pieces of advice, i followed Aysiu's commands, but i mounted hda1 in /media/Windows as per Najand's tip about the possiblity that the file manager mightnt recognize a mount outside /media.

That nano editor is GREAT, will use that from now on.

Could you elaborate on this line: nls=utf8,umask=0222 0 0, please?

It worked perfectly, but i'd love to know WHY it worked!

Thanks.

---

### Post by aysiu on 2006-09-13
I don't rightly know all the details, but I know the nls=utf8 has something to do with character encoding and that umask=0222 gives read-only permissions to everyone.

---


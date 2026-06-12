---
title: "Windows thru Linux"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by qwazert on 2006-03-01
I setup my box to be a dual boot system, using GRUB in the MBR to select which OS to load.
How do I make it so that I can "see" my FAT32 partition (and Win98 files) while in Linux?

---

### Post by Ramses de Norre on 2006-03-01
sudo gedit /etc/fstab
add a line similar to ```
/dev/hda1       /mnt/windowsk  vfat iocharset=utf8,umask=000 0 0

```
With the appropriate partition number (sudo fdisk -l might help) and mount point (needs to be made first)
then sudo mount -a

---

### Post by dvarsam on 2006-03-01
Read the Article#: 137737

Tutorial &#8211; How to "Mount" / "Unmount" Partitions

Good Luck.

---

### Post by qwazert on 2006-03-01
So will I have to do this EVERY time I start LINUX?

---

### Post by jimrz on 2006-03-01
NO...see **_[COLOR="Sienna"][[COLOR="Sienna"]this[/COLOR]]("http://www.ubuntuguide.org/#automountntfs")[/COLOR]_** and be sure to scroll down to where it explains how to have the drive(s) auto-mount each time you spin'er up.

---

### Post by qwazert on 2006-03-02
Thanks...That worked!

---

### Post by meborc on 2006-03-02
read also this: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

it has good instructions how to manage your dual-boot box...

herman - you'r the man :mrgreen:

---

### Post by qwazert on 2006-03-02
I just installed the KDE and the WINDOZE partition is not visible. Is there a file I need to edit to make it so?

---

### Post by qwazert on 2006-03-02
*bump*

---

### Post by jimrz on 2006-03-05
not visible where? and can you still see it from Gnome?

---

### Post by hitmankb on 2006-03-06
Ok, so I have a 200 gig primary HD that had ubuntu and WinXP Pro installed on two 100 gig partitions... I also have a 320 gig secondary HD thats been formatted in fat32...

This is my first time with an installed version of Linux, all Ive ever used were live CD's..

My question is how would I mount the secondary HD?? All of the tutorials show how to mount a partition on the primary HD... I know I this is a silly question but I just want to understand what Im doing and looking at some of these tutorials is pretty much like looking at greek to me:( ...

Thanks for any help!!

Would I do the following but change hda1 to hda2?

"sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000"

---

### Post by ntense on 2006-03-06
im having a problem that somewhat relates to this thread as well... ive done the tut on how to mount the ntfs partitions and my windows partiton is mounting fine... what im having problems doing is accessing the partition... what do i have to do to be able to open it up in konquror and play my Music and access my pictures? this might be a stupid question but im still relativly new to linux myself. im not trying to hijack the thread either i just figured since my problem kind of related to the subject matter that i would seek answers here.

---

### Post by mlind on 2006-03-06
```

sudo fdisk -l

```

shows you the partitions. For example, I've got windows partition (NTFS) which is displayed as
```

/dev/hda5               2       14029   112679878+   7  HPFS/NTFS

```


I'll create a mount point (/media/E) and try to mount it manually first
```

sudo mount /dev/hda5 /media/E -t ntfs

```

it worked okay, so I'll add it to /etc/fstab

```

/dev/hda5       /media/E        ntfs    ro,auto,nls=utf8,umask=0222     0      0

```

Now it will mount automatically (auto) on boot and allow users without root privileges
to access this drive (umask=0222). See *man mount* for more options

When partition is defined on *fstab* It can be mounted/umounted using 
only mount point descriptor. So, for now on mounting this drive type only
```

sudo mount /media/E

```

---


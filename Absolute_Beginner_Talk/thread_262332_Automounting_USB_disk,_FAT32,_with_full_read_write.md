---
title: "Automounting USB disk, FAT32, with full read write permissions for any users"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by spock84 on 2006-09-21
I've searched the forum, but I couldn't figure it out because I'm stupid.

I've added this line to fstab:

"/dev/sdb1 /media/sdb1 vfat nls=utf8,umask=0000 0 0"

But the drive isn't mounted, I think, at least it doesn't show up in nautilus. What did I do wrong?

I realize I could mount it manually each time I log in, but that's kind of annoying.

Any help is appreciated. ;)

---

### Post by spock84 on 2006-09-21
Also, when I mount it manually, root stands as owner and I have no write permission. How do I fix that?

I tried changing the owner of /media/sdb1 to my own user, but it didn't work. For a second I stood as owner, but this seems to have been reverted for some reason.

---

### Post by Omnios on 2006-09-21
there is a in depth fstab article in my signature. 

 Personally I use 
```

/dev/hda2       /media/documents     vfat    rw,users,gid=users,umask=000,       0       0

```

 /dev/hda2               = is the partition I want mounted
/media/documents    = is the mount point where the partition is mounted, you need to make shure you have the mount file where you mount it. example I added a documents directory in mount to mount it to. I also use documents as the mount stuff on the desktop and menu shows it as documents.
vfat  is the type of formated file system.
the other stuff deals with ownership and permisons etc

---

### Post by spock84 on 2006-09-21
That didn't work either. :(

It doesn't show up automatically and when I mount it manually (sudo mount /dev/sdb1 /mnt/external) I don't have any write permissions. I can read from it just fine, but that's not enough ;)

---

### Post by spock84 on 2006-09-21
I figured out I can mount manually and just use 'gksudo nautilus' to copy files and stuff for now, but I'd love to have a more permanent solution.

---

### Post by spock84 on 2006-09-21
Doesn't anyone know?

---

### Post by bodhi.zazen on 2006-09-21
/dev/hda2  /media/documents  vfat user,auto  0  0

---

### Post by spock84 on 2006-09-21
That one worked! Thanks! :D :D :D :D

---

### Post by bodhi.zazen on 2006-09-21
KISS- Keep It Simple Stupid

---

### Post by spock84 on 2006-09-21
However..

When I'm trying the same thing with another disk, it doesn't work!

What am I missing here? What could I be doing wrong? Seemingly the system picks up my changes in fstab, as it mounts the drive where I tell it to, but it doesn't show up as a drive, even if I mount it manually, and I can't write to the folder it's mounted in. What's going on?

---

### Post by spock84 on 2006-09-21
This doesn't make any sense to me. :confused:

---

### Post by james_san on 2006-09-21
Well I think we should be finding out why it is not auto-mounting for you. When I plug in a USB disk, it mounts under my username, with read/write permissions, and then pops it up on the desktop.

What version of (K)Ubuntu are you using?

Try deleting that line from fstab altogether, then reboot and plug it in again.

In a terminal, type "ps ax", and then look down the list to find out if a progarm called "gnome-volume-manager" is running. From memory, that is responsible for auto-mounting removable drives.

What happens when you put a CD in? Does it auto-mount the CD and pop it up for you? If it does, then I see no reason why it shouldn't mount USB drives as well.

Have you made any major changes to your system since you installed Ubuntu? Did USB drives ever work for you?

Sorry about all the questions... :) Hope I can help tho.

I may have misunderstood your post though. If it IS mounting, but you cannot access it from other users, then those users need to be added to the "plugdev" group or something. Have a look in System Preferences->Users

---

### Post by spock84 on 2006-09-22
No, this other drive is a SATA drive. In fstab I've put it as:

/dev/sda1       /media/sda1	vfat    user,auto 0 0

This mounts it, but the owner and group is root, as opposed to the USB drive I mounted the same way, where my user is both owner and group.

---

### Post by spock84 on 2006-09-22
"/dev/sda1       /mnt/satadisk	vfat    auto,users,rw,exec,umask=000 0 0" seems to have worked.

Owner and group is still root, but I can write to the disk now.

---

### Post by xyz on 2006-09-22
I have an external usbdisk divided into 4 partitions. I ran:
```
sudo chown yourusername:groupename /media/usbdisk
sudo chown yourusername:groupename /media/usbdisk-1
...and so on...
```
Is it what you mean? I'm not sure.

---

### Post by spock84 on 2006-09-22
I've tried changing the ownership of the mounting directories in /media/ that way, but they're always reverted to root for some reason. Why is that?

I've found a solution to both the USB and the SATA drive now though (see my previous post).

---

### Post by xyz on 2006-09-22
I just remembered I ran these commands to change permissions when I was using Ubuntu Live CD. I'm not sure it makes a difference; all I know is that I have all the permissions I need doing it that way.
While on Live CD, I also downloaded GParted to partition the usbdisk.
Let me know...

---


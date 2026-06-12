---
title: "Permissions"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Vandorius on 2007-03-28
How do i change permissions. I mounted my second drive on /home/vandorius/NTFS now i can not open it it says not enough permissions. How can i change that?

---

### Post by rune_kg on 2007-03-28
How about this:

```
cd /home/vandorius
sudo umount NTFS 
sudo chown vandorius:vandorius NTFS
sudo chmod -R 777 NTFS
```

And then remounting.

Rune

---

### Post by Vandorius on 2007-03-28
Nope it doesnt help. Note that i mount it GUI way in system, disk management...

If anyone has a solution how to read my second disk go ahead. I dont wanna go to a friend to copy contents to DVD and then bring it on this comp. I bet Linux can do that for me.

---

### Post by george29 on 2007-03-28
post up your /etc/fstab file for us to look at, 

also you could try opening nautilus as root... in  a terminal type

```
 gksudo nautilus 
```

then navigate to your mounted drive in the nautilus window that opened.
right click on the icon for your second hard drive and select permissions
change the owner and group to your username - you should then have access.

sorry if the instructions aren't too great - i'm at work on an XP machine so writing this off the top of my head.

---

### Post by Vandorius on 2007-03-28
Thanks for the reply. I tried your sollution and it worked except that i typed: gksudo konqeror. I am copying files to this disk right now. But i got an error in terminal:

```
gksudo nautilus
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
vandorius@vandorius-comp:~$ gksudo konqueror
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
konqueror: WARNING: Can't open /root/.kde/share/apps/konqueror/bookmarks.xml
kdecore (KProcess): WARNING: _attachPty() 11
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kio (KIOConnection): ERROR: Could not write data
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
IO error opening ICE Connection!

```

What does this say?

---

### Post by george29 on 2007-03-28
i've got no idea... what that means. i'm guessing that it's something to do with X windows 

if you are able to copy files to and fro, mount and unmount the drive as a normal user (ie not using nautilus or konqueror with root permissions) then i wouldn't worry about it.

---

### Post by mlapaglia on 2007-03-28
do you have the right program installed that lets linux deal with NTFS partitions? i forget what it's called but i know you can't read the partition unless it is installed.

---

### Post by george29 on 2007-03-28
ubuntu should be able to read ntfs out of the box - if you want to write to an NTFS partition then you need to install ntfs-3g driver.

---


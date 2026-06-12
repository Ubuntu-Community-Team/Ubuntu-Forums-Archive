---
title: "Unable to mount NTFS partition on KDE"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by cuervo_jones_85 on 2007-06-26
Hello my friends
i have a 16 GB Windows NTFS partition and it was mounted by default on Gnome.. on KDE however it doesn't mount by default and i am unable to mount it sucessfully.

Is there any tutorial that can teach me how to do this?

Thank you!:D

---

### Post by Sonofmoog on 2007-06-26
If NTFS-3G is installed, you should be able to run (sudo) ntfs-config and mount them.  From then on they should be mounted read-write ..

---

### Post by cuervo_jones_85 on 2007-06-26
it didn't mount and showed me the followiing 

sudo ntfs-config
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

---

### Post by cuervo_jones_85 on 2007-06-26
i really need to mount this partition is the onyl thing stopping me from going 100% ubuntu:KS

---

### Post by Sonofmoog on 2007-06-27
I'm sorry, but I've reached the limits of my ability to help.  If the system mounts in GNOME, then that suggests there's nothing wrong with the filesystem.  I do not know why you cannot mount it in KDE ..

---


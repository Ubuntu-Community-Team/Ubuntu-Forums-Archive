---
title: "Deleting old ubuntu versions/kernels"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by A$h X on 2007-12-12
I've just updated to gutsy from feisty, and was wondering if the old version was still on my system? Could i delete any unused versions/kernels from my system to save space? And how much space do they actually take up?

---

### Post by Flyingjester on 2007-12-12
I believe when  you update (assuming through the update manager) it just updates packages, and installs new packages, therefore.. nothing really hanging on obselete on your system.

---

### Post by A$h X on 2007-12-12
What about the old kernels shown in grub? Wonder how much space they are taking up?

---

### Post by Flyingjester on 2007-12-12
around 200mb.. you hurting for space that bad?

---

### Post by dstew on 2007-12-12
You can remove old kernels using Synaptic.

---

### Post by stchman on 2007-12-12
> **A$h X said:**
> What about the old kernels shown in grub? Wonder how much space they are taking up?

Each kernel takes up about 170MB.  Remove them using synaptic.

---

### Post by A$h X on 2007-12-12
> **stchman said:**
> Each kernel takes up about 170MB.  Remove them using synaptic.

Thank you stchman. 170mb is a lot bigger than 2mb ;-) I've got gutsy on a 10gb partition (and XP on another 10gb partition) so I try and keep as much free space on the system partitions as possible.

---

### Post by disturbedite on 2007-12-12
> **dstew said:**
> You can remove old kernels using Synaptic.
i was gonna say that, but you beat me to it...

---

### Post by stchman on 2007-12-13
> **A$h X said:**
> Thank you stchman. 170mb is a lot bigger than 2mb ;-) I've got gutsy on a 10gb partition (and XP on another 10gb partition) so I try and keep as much free space on the system partitions as possible.

The kernel itself is actually pretty small, but the source for the kernel is included as well and that takes up gobs of space.

10GB is pretty small for Ubuntu or XP.  I would consider a larger hdd.

---

### Post by A$h X on 2007-12-13
> **stchman said:**
> The kernel itself is actually pretty small, but the source for the kernel is included as well and that takes up gobs of space.

10GB is pretty small for Ubuntu or XP.  I would consider a larger hdd.
I thought 10gb for ubuntu, 10gb for XP, and 90gb as a shared data partition would be okay? Both system partitions have around 5gb of free space each, so i assume they will be able to fit all necessary updates?

---

### Post by stchman on 2007-12-13
> **A$h X said:**
> I thought 10gb for ubuntu, 10gb for XP, and 90gb as a shared data partition would be okay? Both system partitions have around 5gb of free space each, so i assume they will be able to fit all necessary updates?

My misunderstanding.  I thought that you had a 20GB hdd,  I would still give XP more room.  On my dual boot machines I give XP around 20GB.  10GB is OK for Ubuntu.

---

### Post by jasonrandolph on 2007-12-13
This is a little off-topic, but if you remove an old kernel via Synaptic, will it no longer show up in Grub?  Not that I pay much attention, but the list already takes up half my screen.  A few more upgrades and the screen will be full!

---

### Post by stchman on 2007-12-13
> **jasonrandolph said:**
> This is a little off-topic, but if you remove an old kernel via Synaptic, will it no longer show up in Grub?  Not that I pay much attention, but the list already takes up half my screen.  A few more upgrades and the screen will be full!

Yes, removing the kernels via synaptic will remove the GRUB entries.

---

### Post by skyjacker on 2007-12-13
I did a "clean " install of Kubuntu 7.10, and still have 2 other versions of ubuntu on my machine. Do I have synaptic in kubuntu? How do I find the versions to delete?

---


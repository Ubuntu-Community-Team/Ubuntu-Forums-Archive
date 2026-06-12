---
title: "Mounting Permissions Issues"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by CosmicSlop on 2008-02-24
I just revisited Linux for the first time in 5 years and liked what I saw/see in Ubuntu. I'm have a major problem getting to "work" though.

I have a couple of drives in my machine and those drive have partitions; here are my questions;

1 - How do I see/edit which drives are mounted during startup. How does Ubuntu decide which drive to mount or not? It mounts some but not all.

2 - How do I get access to read and/or write to drives that are owned by "root" or "unknown"?

3 - How do I share these now accessible  drive and folders with a Vmware XP session?

Not being able to access files and drives is forcing me to constantly boot into XP to things done. 

Thanks.

---

### Post by LaRoza on 2008-02-24
> **CosmicSlop said:**
> 
1 - How do I see/edit which drives are mounted during startup. How does Ubuntu decide which drive to mount or not? It mounts some but not all.

2 - How do I get access to read and/or write to drives that are owned by "root" or "unknown"?

3 - How do I share these now accessible  drive and folders with a Vmware XP session?

Not being able to access files and drives is forcing me to constantly boot into XP to things done. 


0. The mounting permissions and settings are in /etc/fstab. [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

1. You can change the permissions, or for a more dangerous route, you can run nautilus as root. (Press Alt + F2 and type "gksudo nautilus")

2. Don't know much ab VMWare, sorry. Someone else will have to give you that.

---

### Post by superprash2003 on 2008-02-24
there are two ways you can share files with a vmware xp OS...
1)you can create a small network there.. install samba in your ubuntu and set right your vmware network settings(bridged mode i think).. then you can access your files from xp by typing \\(ubuntu computer name or ip) in windows explorer.. guide to install samba is available here - [http://ubuntuguide.org](http://ubuntuguide.org)

2)i am not quite sure about this but i think its possible.. there is a way to add an external device or drive in vmware settings.. look for add device or hardware and try mounting it!!

---

### Post by kooolrock on 2008-02-24
> **LaRoza said:**
> 0. The mounting permissions and settings are in /etc/fstab. [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

1. You can change the permissions, or for a more dangerous route, you can run nautilus as root. (Press Alt + F2 and type "gksudo nautilus")

2. Don't know much ab VMWare, sorry. Someone else will have to give you that.
[COLOR="DarkRed"]LaRoza ROCKSSSSSSSSSSSS!!![/COLOR] She is **one of the best problem solvers** in this forum.

---

### Post by Martje_001 on 2008-02-24
Why don't you use VirtualBox instead of VMware? Virtualbox works (IMO) better then VMware on Linux.

---

### Post by CosmicSlop on 2008-02-24
> **LaRoza said:**
> 0. The mounting permissions and settings are in /etc/fstab. [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

1. You can change the permissions, or for a more dangerous route, you can run nautilus as root. (Press Alt + F2 and type "gksudo nautilus")

2. Don't know much ab VMWare, sorry. Someone else will have to give you that.

Thanks LaRoza - this'll git me going in the right direction.

---

### Post by CosmicSlop on 2008-02-24
> **superprash2003 said:**
> there are two ways you can share files with a vmware xp OS...
1)you can create a small network there.. install samba in your ubuntu and set right your vmware network settings(bridged mode i think).. then you can access your files from xp by typing \\(ubuntu computer name or ip) in windows explorer.. guide to install samba is available here - [http://ubuntuguide.org](http://ubuntuguide.org)

2)i am not quite sure about this but i think its possible.. there is a way to add an external device or drive in vmware settings.. look for add device or hardware and try mounting it!!

What do you mean by "CREATE a small network"?

Thanks

---

### Post by Martje_001 on 2008-02-24
I think he means, you install SAMBA and configure it. Then you setup a 'brigded' network in VMWare, so you can acces the Linux hard disk via Windows.

---


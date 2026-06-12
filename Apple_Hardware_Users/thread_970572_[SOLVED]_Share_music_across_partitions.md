---
title: "[SOLVED] Share music across partitions?"
date: 2008-11-04
forum: Apple Hardware Users
---

### Post by tact. on 2008-11-04
Well, I just successfully installed Ibex on my Macbook using bootcamp (so far I love it). I'd prefer to use my music through Rhythmbox but not make a copy of my songs. I can see my Mac partition through Ubuntu but cannot see any of my music files in the folder. Is there a way to "import" my songs from my Mac partition and play them like normal without copying them over?

---

### Post by moviemaniac on 2008-11-04
try to run rhythmbox by starting it from a terminal using "sudo rhythmbox". This should grant you the rights to access your music folder and files. 
A hassle-free solution would be to create a separate FAT32 (or NTFS but you'd have to install drivers on Ubuntu and OSX to get it working) partition where you store your music and shared files for both OS. That's what I do.

---

### Post by cyberdork33 on 2008-11-04
You can also modify the permissions on the files from inside OS X to allow other users access to them.

---

### Post by tact. on 2008-11-04
> **moviemaniac said:**
> try to run rhythmbox by starting it from a terminal using "sudo rhythmbox". This should grant you the rights to access your music folder and files. 
A hassle-free solution would be to create a separate FAT32 (or NTFS but you'd have to install drivers on Ubuntu and OSX to get it working) partition where you store your music and shared files for both OS. That's what I do.

I will give the command a try. Will this ultimately copy all my music onto the Ubuntu partition or just find the music from the OS X location?

---

### Post by moviemaniac on 2008-11-04
It will allow you to access the music on the OSX-partition, nothing will be copied over.

@cyberdork33: I knew there had to be an easier way :D Anyway, I still prefer an extra partition, I'm a bit reluctant to frequently write to HFS+ partitions in Ubuntu or ext2/3-partitions in OSX out of fear of data-loss.

---

### Post by tact. on 2008-11-04
> **cyberdork33 said:**
> You can also modify the permissions on the files from inside OS X to allow other users access to them.

I'll try this first, thank you!

---

### Post by cyberdork33 on 2008-11-04
> **moviemaniac said:**
> It will allow you to access the music on the OSX-partition, nothing will be copied over.

@cyberdork33: I knew there had to be an easier way :D Anyway, I still prefer an extra partition, I'm a bit reluctant to frequently write to HFS+ partitions in Ubuntu or ext2/3-partitions in OSX out of fear of data-loss.
I think that running anything like that with root permissions is a bit risky.

I agree that a separate partition (or network share) is the easiest way to handle this.

You don't have to write the HFS+ partition just to listen to music... do you? I always mount my HFS+ partition Read Only (and only do that when I really need something off there.)

---

### Post by moviemaniac on 2008-11-04
well, no, I don't think he needs write-permissions. At least not, when listening to music, but, personally I'd want to rip a CD every once in a while and I'd want to be able to to that in both operating systems.

---

### Post by tact. on 2008-11-05
> **cyberdork33 said:**
> You can also modify the permissions on the files from inside OS X to allow other users access to them.

This worked like a charm, thank you. I just set my User folder as a read only and am able to access my music, videos, photos, etc within Ubuntu.

---


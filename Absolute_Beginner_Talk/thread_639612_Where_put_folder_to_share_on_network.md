---
title: "Where put folder to share on network?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by movrshakr on 2007-12-13
I want to create a folder on the ubuntu machine where I will put files that anyone on the other networked machines (Windows XP or Vista) can read, write, make new folders etc.

In essence, this (shared folder) will be the network file server for all machines.

My question is, where is the best location in ubuntu to place this folder-to-be-shared?  In my own folder?  In usr?  Where?

---

### Post by Dr Small on 2007-12-13
It could be anywhere, so long as you set that folder up in Samba to be shared, but just go ahead and make a directory in /home and make it your shared folder. That would be simple.

Dr Small

---

### Post by movrshakr on 2007-12-13
OK, thanks.  As for making it "be" shared, is there not a way to just click on it and say, "share this folder?"

---

### Post by Dr Small on 2007-12-13
I think you need to go to System > Administration > Sharing or something of another (I forget, I'm on IceWM), and then set up a folder to be shared.

Dr Small

---

### Post by ctyc on 2007-12-13
system >>Administration>>Shared Folders

---

### Post by Dr Small on 2007-12-13
> **ctyc said:**
> system >>Administration>>Shared Folders
Thanks for correct location, ctyc :D

---

### Post by movrshakr on 2007-12-13
I had a thought (dangerous)...

is doing the "system >>Administration>>Shared Folders" thing to share it going to make it usable by the Windows machines on the network, or is that only for sharing it to other linux machines?

IOW, does doing it the GUI way take care of configuring samba?

---


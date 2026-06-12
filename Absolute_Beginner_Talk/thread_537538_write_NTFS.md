---
title: "write NTFS"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by mthalis on 2007-08-29
I had ubuntu 7.04 and dual boot machine my other partion is ntfs It gave automatically read permission. Now I want to write ntfs.

---

### Post by wormser on 2007-08-29
Applications> Accessories> Terminal

```
sudo apt-get install ntfs-3g ntfs-config
```

Applications> System Tools> NTFS Configuration Tool.

---

### Post by Hugolp on 2007-08-29
Hi

Try searching for "ntfs" in install programs under the aplications menu.

When you are looking for a feature or a problem try looking there and if you dont find it there, try synaptic. You will be very surprised by the amount of choice youll find.

Hugo

---

### Post by uputer on 2007-09-02
> **wormser said:**
> Applications> Accessories> Terminal

```
sudo apt-get install ntfs-3g ntfs-config
```

Applications> System Tools> NTFS Configuration Tool.

I installed ntfs-3g and ntfs-config but I couldn't access the NTFS Configuration Tool.   It's listed in the menu but will not start.

I could read/write to NTFS but the mounting got screwed up, I think.   Also, my /etc/fstab file was modified.   

I hope someone here can help me solve the problems and 'fix' it.

A Kubuntu user told me to remove ntfs-config.   I don't know if that's the best option or not.

---


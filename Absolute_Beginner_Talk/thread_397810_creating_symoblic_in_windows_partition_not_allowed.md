---
title: "creating symoblic in windows partition not allowed , why?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by medya on 2007-03-31
hi ,
I want to make windows and linux use the same Logfiles for Gaim .

for that I am gonna copy the logs in Fat32 partition which I use for sharing things between linux and windows.

but when I tried to create symoblic using file manager (right click and then make link) it says it is not allowed .

I can create link easily in my linux normal partitions. 

why is that ?

---

### Post by lloyd_b on 2007-03-31
You can't make symlinks on a FAT32 file system.  That file system's structure simply doesn't have any way to store the information underlying a symbolic link.

Lloyd B.

---

### Post by Patrick K on 2007-03-31
You can link from Linux to a FAT32 file. I have several. However, I was unable to do them in Nautilus. I ended up using X File Explorer (XFE) (it's in Synaptic). It made the link without any problems. It's a somewhat unstable file browser but works for links. I'm sure there is a way using the command line but I don't know it.

---

### Post by lloyd_b on 2007-03-31
> **Patrick K said:**
> You can link from Linux to a FAT32 file. I have several. However, I was unable to do them in Nautilus. I ended up using X File Explorer (XFE) (it's in Synaptic). It made the link without any problems. It's a somewhat unstable file browser but works for links. I'm sure there is a way using the command line but I don't know it.

The command line is:
```
ln -s {source} {destination}
```
where {source} is the original file, and {destination} is the link.

Lloyd B.

---

### Post by Patrick K on 2007-03-31
Thanks for that, Lloyd. I've tucked it away on my list of commands.

---


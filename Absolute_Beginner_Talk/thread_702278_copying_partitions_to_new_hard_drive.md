---
title: "copying partitions to new hard drive"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by saunders on 2008-02-20
I've bought a new hard drive for my Dell Inspiron 1300 to give me some extra storage space.

I'm not worried about installing Gutsy on a fresh drive as I've installed it a few times before.

However, as Dell only ship driver CDs with their computers, I don't have a copy of WinXp to install on the fresh drivel (and I can't switch to Linux only yet). 

Is there any way of copying an what's on my original hard drive (particularly the Windows-related partitions) to an external USB one, then recopying it back to the new blank drive, so I have windows up and running as before, and can then get on with my Ubuntu install?

I'm aware of the dd, partimage and remastersys options (I've had a quick look through the forums already), but I have a feeling they're not exactly what I need.

Any ideas?

---

### Post by Crooksey on 2008-02-20
I dont think windows will allow itslef to be copied and then be loaded of a new HD, but if you just want files copying...

```

mkdir /mnt/windows
mount /dev/sda1 /mnt/windows #windows partition is example of sda1
mkdir /home/<user>/windows_copy
cp -a /mnt/windows* /home<user>/windows_copy
```

That will copy the files to your home directory, do what you like with them.

---


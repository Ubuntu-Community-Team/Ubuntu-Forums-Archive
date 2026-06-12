---
title: "Volumes on desktop"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by NegativeSpace on 2007-04-22
Hi,

On the desktop I have two other mounted disks.  Is it possible to remove them from the desktop without unmounting them? I don't want get rid of them, just not have them represented on the desktop.

Regards.

---

### Post by Rinzwind on 2007-04-22
Yes. All volumes mounted inside /media are shown on the desktop.
So the answer to your question is: mount them elsewhere.
I have my 2 USB discs mounted in /anime1/ and /anime2/  

The mountpoints are taken from
/etc/fstab

So type
gksudo gedit /etc/fstab
(gnome)
and change the mountpoints.

---

### Post by NegativeSpace on 2007-04-22
Rinzwind, thanks for your help.

However, I seem to have run into a problem. I changed the mount point and rebooted -- when I logged in to Ubuntu, they weren't on the desktop, which was great, but they also weren't where I had specified them, either.

I created a directory, */disks*, and modified the two mount points to:

```

UUID=7A68CA8A68CA449B /disk/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
UUID=07D5-0215  /disk/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1

```

The only thing I changed at all was */media* into */disk*.

Can you suggest why this might have happened?

Regards.

---

### Post by Wight_Rhino on 2007-04-22
Ok, I'll ask the obvious first, ('cause that's all I've got!)

You said you creaated */disks* (plural)

But in fstab you've put */disk* (singular)

Probably just a typo, but I thought I'd ask anyway.:)

---

### Post by NegativeSpace on 2007-04-22
> **Wight_Rhino said:**
> Ok, I'll ask the obvious first, ('cause that's all I've got!)

You said you creaated */disks* (plural)

But in fstab you've put */disk* (singular)

Probably just a typo, but I thought I'd ask anyway.:)

Hi, Wight_Rhino -- unfortunately, it is *disk* in fstab and the directory's name. I had hoped maybe I'd made a simple mistake.

Any ideas?

Thanks.

---

### Post by zvacet on 2007-04-22
```
gconf-editor
```
apps>nautilus>desktop

---

### Post by NegativeSpace on 2007-04-22
zvacet -- perfect, thanks!

---


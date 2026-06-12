---
title: "Windows Volumes Automatically Mount"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by CosmicFlux on 2007-12-12
Hi,

OK, I have a dual-boot system with Windows Vista & Ubuntu 7.10. It's not through choice, but my girlfriend is stuck on Windows and can't seem to get her head round Linux. Anyway, when I load into Ubuntu I find the two Windows partitions displayed on the desktop. Last time I logged in, I went in as root and unmounted them. Thing is, when I shutdown and load into Ubuntu on another session, the mounted volumes are again displayed on my desktop. 

How can I rectify this?

CosmicFlux

---

### Post by p_quarles on 2007-12-12
Do you want them not to mount, or do you just not want them on the desktop?

To prevent them from auto-mounting, you can edit the file that mounts drives on startup:
```
gksudo gedit /etc/fstab
```
Once the file is open, simply comment out the two entries for the Windows partitions. (This is done by placing a "#" sign in front of the line).

To keep it from appearing on your desktop, you would need to change the appropriate settings in Gconf (which, tbh, can be a pain unless you know exactly what you're looking for).

---

### Post by jken146 on 2007-12-12
Devices that are mounted in /media are automatically displayed on the Desktop.  You can do as the previous poster advised (comment out the devices in /etc/fstab) if you don't want them mounted at all.

If you do want them mounted though, but not appearing on the desktop, you can change the mount points in /etc/fstab.  A sensible mount point would be /mnt/windows (you need to create the directory /mnt/windows first).

A third option is to disable desktop icons for mounted devices.  Press Alt+F2, type **gconf-editor** and navigate to apps > nautilus > desktop.  Then untick the box that's labelled 'show volumes' or some such thing.

---

### Post by t0p on 2007-12-12
I'm puzzled why you don't want your Windows partition to automatically mount.  I think it's great that my XP stuff is accessible from Gutsy!  When I was using Feisty, I had to use ntfs-config to make the XP files available all the time.

The auto-mount is a plus.  Enjoy it!

---

### Post by jken146 on 2007-12-12
@t0p:  Yes but having them displayed on the desktop all the time is annoying.  Plus, having them mount can be useless if you hava a shared /home partition for example.  Not every new feature is a good thing for everyone.  Customisation is the the real plus of linux!

---

### Post by ajgreeny on 2007-12-12
> I'm puzzled why you don't want your Windows partition to automatically mount. I think it's great that my XP stuff is accessible from Gutsy! When I was using Feisty, I had to use ntfs-config to make the XP files available all the time.I'm rather like CosmicFlux and don't want my windows partition mounted at all so I commented out the windows lines in fstab as one of the first thing I did when I installed gutsy.  I only use windows now for scanning as my old parallel port scanner will not work in linux, and I use it so seldom that it isn't worth getting a new one just yet.  All the files I used to work on in windows have long been either useless to me or transfered to ubuntu already, so I don't need to access windows from ubuntu any more.  Horses for courses, I suppose, what's right for some is wrong for others.

---

### Post by CosmicFlux on 2007-12-13
> **t0p said:**
> I'm puzzled why you don't want your Windows partition to automatically mount.  I think it's great that my XP stuff is accessible from Gutsy!  When I was using Feisty, I had to use ntfs-config to make the XP files available all the time.

The auto-mount is a plus.  Enjoy it!


Because Windows sucks. I don't use it, I don't need it, I don't want it leaving its ugly little imprint on my beautiful Linux system. Does that answer your question? :)


CosmicFlux

---


---
title: "external hard drive authorization"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by mceven on 2007-06-18
Hi,

A couple of weeks ago my son switched our computer from Windows to Ubuntu unwittingly -- he was trying to set up a dual-boot computer but accidentally wiped out our hard drive and left us with a dedicated Ubuntu machine.  Thus far, we've been very pleased with Ubuntu and have no desire to go back to XP, but have run into a couple of snags since then.  The latest:

We have a LaCie 250 GB hard drive, originally formatted for Windows, which contains all of our backup files and software from the XP version of this computer.  I've had no problems using and reading files from the external drive but tried to write files onto the drive today and Ubuntu won't let me do it, insisting I'm not authorized to do so.  

Question:  How do I authorize myself so I can use the drive?

Thanks in advance.

---

### Post by Jimmyfj on 2007-06-18
Hi

That is because you'd need to install NTFS read/write support for Ubuntu. Go to 

Programs/ Add/remove/system tools and installe the packet from there or through System/administration/Synaptic

after that you can change owner of the drive like this

sudo chown -R USERNAME:USERNAME /media/mynewdrive

---

### Post by Clay_Banger on 2007-06-18
> **Jimmyfj said:**
> Hi

That is because you'd need to install NTFS read/write support for Ubuntu. Go to 

Programs/ Add/remove/system tools and installe the packet from there or through System/administration/Synaptic
it may not b ntfs, it depends on where the comp came from.

---

### Post by p_quarles on 2007-06-18
Open a terminal and type the following:```
sudo apt-get install ntfs-config
```

If that doesn't take, you can go to the System/Adminstration/Synaptic Package Manager and enable the Universe repository, and then try the command again. 

Also: you need to restart the GUI/computer before this takes effect.

---


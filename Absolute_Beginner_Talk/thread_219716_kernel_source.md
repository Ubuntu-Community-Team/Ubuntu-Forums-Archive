---
title: "kernel source"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by macogw on 2006-07-20
I'm trying to install my ethernet card's drivers.  This is becoming a lengthy process.  The readme says I need compiling stuff, so I got build-essential off of the cd.  It also says I need to have the kernel source in /usr/src/linux.  Well, /usr/src is empty.  How do I get it in there?  Is that on the cd too?  If it is, what's it called?

---

### Post by ironfistchamp on 2006-07-20
I think what you need to do is get it through apt-get. Or at least that is how I did. I think. Anyway this might do it.

sudo apt-cache search linux-source

That will print a list of the packages matching that. You will want the one that coresponds to your kernel. I think the one on there is 2.6.15. Just issue

sudo apt-get install linux-source-2.6.15 

There you shoud be set now. Hope it works

---

### Post by macogw on 2006-07-20
That requires an internet connection.  I got around it already by downloading the .deb using the desktop which has internet, then using a flash drive to transfer it.  Now I'm trying to patch it so that it can support external modules (such as the driver for my ethernet card so I can get internet).  I just need to find out what to do with the source text of a patch.

---

### Post by ironfistchamp on 2006-07-20
](*,) Sorry didn't read what you needed it for.

---

### Post by az on 2006-07-20
> **macogw said:**
> I'm trying to install my ethernet card's drivers.  This is becoming a lengthy process.  The readme says I need compiling stuff, so I got build-essential off of the cd.  It also says I need to have the kernel source in /usr/src/linux.  Well, /usr/src is empty.  How do I get it in there?  Is that on the cd too?  If it is, what's it called?

You need to install build-essential and linux-headers-386

If you installed using the alternate or server cd, just install the packages.  If you installed using the Desktop cd, put it back into the drive once you have booted to the desktop and a dialog box will appear, asking if you want to start the package manager.  Click yes and then proceed to install the packages.  They will be installed from the cd.

You need to do it like that when you have installed from the Desktop cd since those packages are apart from the live cd session on the disk and do not get added to your list of repositories otherwise.

---


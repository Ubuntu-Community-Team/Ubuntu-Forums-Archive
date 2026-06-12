---
title: "How can I access my windows partition from Ubuntu?"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by Roxlo on 2007-09-17
I want to access my windows partition from Ubuntu. How is this done? :)

---

### Post by runemaste644 on 2007-09-17
if it is a virtual partition i do not know. 
if not, is it a NTFS  or FAT partition? If it is FAT, consider trying the SKINNY one.:lolflag:

---

### Post by st33med on 2007-09-17
You can. If you just want to see files and play a few games through WINE, just go to Places>>Computer and open that 'XX.XGB Volume'.

Answer your question?

---

### Post by Maestro23 on 2007-09-17
nfts-3g: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

If you are wanting read/write capabilities to it from Ubuntu.  The program can be installed from the repositories.  Use Synaptic (GUI) or Command Line (apt-get).

---

### Post by oilchangeguy on 2007-09-17
try this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by bodhi.zazen on 2007-09-17
> **Maestro23 said:**
> nfts-3g: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

If you are wanting read/write capabilities to it from Ubuntu.  The program can be installed from the repositories.  Use Synaptic (GUI) or Command Line (apt-get).

You might want to look at ntfs-config. It is a gui front end and may be easier for new users then mount/edit /etc/fstab. I run it with :```
gksu ntfs-config
``` Works with FAT and NTFS partitions.

[How to ntfs-config](http://ubuntuforums.org/showthread.php?t=337970)

> **oilchangeguy said:**
> try this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

+1 on that link, it is a classic.

---

### Post by Maestro23 on 2007-09-17
> **bodhi.zazen said:**
> You might want to look at ntfs-config. It is a gui front end and may be easier for new users then mount/edit /etc/fstab. I run it with :```
gksu ntfs-config
``` Works with FAT and NTFS partitions.

[How to ntfs-config](http://ubuntuforums.org/showthread.php?t=337970)



+1 on that link, it is a classic.

Forgot about including that. Thanks bodhi.:)

---

### Post by Roxlo on 2007-09-17
Thanks guys :D

---


---
title: "When in doubt ask the obvious question"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by jaszman on 2006-04-18
So, here it goes...

Specs:

Its a standalone
Windows XP SP2 and Ubuntu Breezy Badger 5.10
Windows is NTFS all others are FAT 32

AMD 3100
VIA Motherboard
1,256 MB RAM
CDROM Burner (F drive)
3 HD:
     1-20 Giga (C-Windows XP, G-Breezy and the smaller partition)
     2-40 Giga (D-photos, Win XP utilities)
     3-40 Giga (E-My Documents, there is no My Documents in C)

I installed the dualboot option. Everything works properly, sound, video, etc. When I'm in Windows I see the G drive as empty, but when I'm in Ubuntu I only see the drive it's installed in and the CD burner and floppy, but not the other HDs or their folders.

What I've read from the threads and reviews is that I can using the console add the other drives or add Windows as such (which I figure will let me access My Documents), as "mounting", what about the My Music folder inside the My Documents on drive E and the other folders in drive D, do I have to use the console to access them also and/or what commands to use? Does the mapping done when I mount let me see whats inside the drive? Since all my music (mp3, acc) and word, text and adobe documents are stored in drives D and E, I'm at a loss and the answers I've seen don't address documents and files in various drives. I'd like to know before I start making changes. Specific instructions will be appreciated.

---

### Post by WoodyMahan on 2006-04-18
Read this over and it will explain how to automatically mount all drives in Ubuntu.

[https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mounting%29](https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mounting%29)

Follow the steps and it works like a charm.

---

### Post by aysiu on 2006-04-18
Here's a step-by-step:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

The only thing you need to know is where the terminal is to type commands:

Ubuntu: Applications > Accessories > Terminal
Kubuntu: KMenu > System > Konsole

---


---
title: "Make LiveCD a repository?"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by bwhite82 on 2007-04-08
Need some help here. Firstly, here are my goals:

-To have a fully functioning Kubuntu Feisty desktop
-To eliminate or minimize downloading packages to accomplish above goal

What I have at my disposal:

-Ubuntu Edgy Alternate LiveCD
-Kubuntu Feisty Desktop LiveCD (Will not boot, the disk and data is fine, trust me)
-Ubuntu Edgy Minimal CD
-Ubuntu Feisty Minimal CD

I have Ubuntu Edgy desktop currently installed, I would like to know how to setup my CD's to be de-facto repositories, to eliminate the need to hamper my already-hampered bandwidth. I know I can use "apt-cdrom add" to add the disks, but since I am running Edgy, synaptic refuses to recognize the Feisty updates on the CD. Any ideas? Thank you.

---

### Post by bwhite82 on 2007-04-08
Hmm...ok, got aptitude to recognize the package list on the Kubuntu LiveCD, but it is not showing that is has the necessary files that I need, ie kubuntu-desktop, etc. I dug up the package "manifest" from the directory that I download the ISO from, and it clearly lists kubuntu-desktop package as being on the CD.

Perhaps it is compressed in such a way that it is hidden? Is there anyway to uncompress all of those packages?

---

### Post by bwhite82 on 2007-04-08
Aha! I've located a file on the disk, "filesystem.squashfs", that is indeed a compressed file that probably contains all kind of goodies. Now to find out how to get the ants from the anthill....hmmm. I just love unanswered threads, they force me to not be lazy and look up things and learn.

I'll continue to keep you..err...myself posted as to my findings.

---

### Post by bwhite82 on 2007-04-08
Alright, after installing "squashfs-tools" to "unsquash" that file, and seeing only a copy of a complete file system itself, I sought out greener pastures. Then came along jigdo! Man am I glad I discovered this in the wiki. Now, instead of downloading another entire CD image, I can only download select, updated parts, whilst utilizing the CD's I already have to create an entirely new ISO.

---


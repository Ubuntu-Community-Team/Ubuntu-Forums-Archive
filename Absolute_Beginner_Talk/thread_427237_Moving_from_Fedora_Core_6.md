---
title: "Moving from Fedora Core 6"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Les Nagy on 2007-04-29
I have posted this topic in the Kubuntu forums as I prefer KDE, but thought I would ask here also as this forum has a larger user base.

I would like to try Kubuntu after using FC6 with KDE for a few months. I am impressed with the advances that (K)Ubuntu seems to have made and and have had troubles getting some basic things working in FC6, like my Wacom Graphire. So I would like to know the best way to migrate my system to Kubuntu.

I have my drives partitioned as ext2, root and a separate home partition. I would like to be able to preserve all of my data and I assume that my home partition need not be affected by installing Kubuntu. So do I just install Kubuntu on the root partition? I would guess that I would need to install all of my apps again. Is there a specific procedure to insure that my home partition is used as home for a new install of Kubuntu? Any other concerns I should be aware of?

The other question is before I do all of this; shoulkd I do it?

I use my system for photo editing, video editing, music, TV, and the other usual computer uses.

System:
Dell e521
AMD X2 4200
2 gig
SATA HD
NV 7900GS
Audigy 2 ZS Platinum Pro

---

### Post by coxy on 2007-04-29
I use the alternate Kubuntu CD for installs because I prefer the text based installer, with that disc you can point an existing partition to where you need. Just make sure you don't format it :) 

If it can be done in the text based installer then I am sure it can be done with the desktop CD. If you have any questions then give me a shout.

---

### Post by Austin_KW on 2007-04-29
No reason not to do it. Having a seperate home partition makes it easy to reinstall or change distro. 

If you are worried about accidently formating your home partition the just tell the install to just use your / partition. You can always change fstab and mount the partition under /home.

---

### Post by Austin_KW on 2007-04-29
Also consider moving your home partition to ext3. It just involves adding jounaling to the ext2, bit slower but you are less likely to loose you work.

---

### Post by vanadium on 2007-04-29
In principle, yes, you can install Ubuntu on the former FC3 / partition and have it use your existing /home partition.

There is one caveat: /home also contains application settings. Depending on the versions of the applications, the config files you have might not be compatible with the versions that ship with Ubuntu. A safe approach would be to delete most of the existing hidden application directories, preserving only your documents and other data files, and the folder containing your mail. That would allow the Ubuntu versions of the applications to recreate their hidden folders, and you would not risk to run into some incompatibility between versions.

---


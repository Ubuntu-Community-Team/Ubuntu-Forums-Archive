---
title: "Unable to Partition!"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by kopolee11 on 2005-12-13
Hello, I recently ordered 5 CDs of Ubuntu Version 5.10 (Breezy Badger) When I first received the disk, I quickly put in the Live disk. It worked 100%, however, I didn't explore it much, because I was anxious to install the real version. After reading a few in depth documents, I felt pretty prepared to install Ubuntu. Boy was I wrong...;) 

When I got to the Partition part, I clicked "Manually edit partition table" Using both this [guide ]("https://wiki.ubuntu.com/Installation/I386")and this [guide]("http://users.bigpond.net.au/hermanzone/p2.htm"), I carefully followed the step. However, when I started trying to shrink the partition, an error came up, saying that it could not resize the partition. Puzzled, I checked both of the guides I used earlier and noticed that neither of them mention this error. I quickly looked through the wiki and found [this]("https://wiki.ubuntu.com/forum/installation/Partitioning"). At the bottom it states. 

> If, when you are trying to shrink your partition, you are not given the option to enter a smaller size, it is because the installer does not feel it is able to resize the partition. Possibly because it thinks it is full, is corrupt, or has some other problems that it cannot solve.

Not knowing what this problem was, I looked through the forums, and couldn't find this same problem in either the "Installation and Upgrade" or the "Absolute Beginner Talk". If you guys could help me figure out what the problem is with my partition that would be great. I'll give you the specs I know.

Microsoft ME
AMD Athlon Processer
368 MB of Ram
Video Card 16MB (Although I don't think that matters for installing Ubuntu)
19 GB Hard drive and I played to give the Linux partition to be 6 GB (Just for testing purposes)

Anyway, thank in advance. If you need more detail or more specs, I'll try to tell you to the best of my ability.

---

### Post by Griff on 2005-12-13
Hmm.  Well I can't really explain why the resizer didn't work for you (you did defrag the windows partion a few times before you tried this right?), but I do feel your frustration.  The resizer on the ubuntu disk didn't work for me either.  What did work for me was another partioner program.  Like you I researched an alternative approach to the resize issue.  Ever here of Knoppix?

If you aren't able to resize your partion, do a google for Knoppix and download it.  It's a live linux CD with a KDE desktop.  I mention this because it has a program in it called qtparted that will allow you to resize your NTFS partion.  (Gnome's gparted wouldn't work for me).

---

### Post by kopolee11 on 2005-12-14
Sorry for not responding for practically a day, I was very busy. I'll try not to let this happen again.

Griff, I did run defrag, but I'm planing to run it again, and run "scandisk". (Something I didn't do before I tried to install Ubuntu.) I've heard of Knoppix, but I thought NTFS patitian was for Windows XP, not Windows ME which uses Fat32. (I think :confused: ) However, if what I'm trying in the [Installation & Upgrade]("http://www.ubuntuforums.org/showthread.php?p=572462#post572462") doesn't work, I'll try that method. :cool: 

Thanks again.

---


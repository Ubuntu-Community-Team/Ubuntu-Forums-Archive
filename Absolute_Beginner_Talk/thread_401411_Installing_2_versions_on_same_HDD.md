---
title: "Installing 2 versions on same HDD"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2007-04-04
Hi all! I was wondering if I installed a second newer version of Ubuntu on the same HDD could I use the existing home and swap partions.
regards

---

### Post by Happy_Man on 2007-04-04
Well, if you do 

```

sudo apt-get dist-upgrade

```

after changing your repos you can...
but if you mean physically installing it on a new partition, i don't think so.

---

### Post by divague on 2007-04-04
Yes, you can use the same /home and swap partitions.

---

### Post by Zuuswa on 2007-04-04
Yes, you can.  Swap partition space on your hard drive can be shared by two differant linux operating systems installed on differant partitions.  /home is the same way, as long as you have your /home on a differant partition than the main operating system(s).  (But if you dont you can still mount the other partition and access the files).  During the installation process, if you manually set up the partitions you can just flag the swap and /home partitions as such, and it will work great.  That is the method I use, so I can just install or re-install on the system partitions and still have all my settings and files, etc.

---

### Post by Jussi Kukkonen on 2007-04-04
You can, but using the same home directory is probably not advisable -- you'd have different version of applications using the same config files... 

I'd probably share the swap but set different home partitions (sharing home, but using different users should be safe too).


EDIT: zuuswa said it works, so I could be wrong about any possible problems...

---

### Post by Zuuswa on 2007-04-04
The only problem I've heard of is some Evolution settings, though I dont use Evolution so I cannot attest to it's usuability.

---

### Post by zvacet on 2007-04-04
If you don´t make some reasarch I don´t see the point to have two same distro versions in the same comp,but yes,you can do it.

---

### Post by Sbarton on 2007-04-05
Thanks folks it's all done.Thanks for all your posts. The versions I have are Dapper & Edgy.
Zuuswa thats what I think, that it's easier to try another version without messing up the original.
regards

---


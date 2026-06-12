---
title: "Considering doing a Dual Boot"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Hutchie on 2008-03-05
I'm definatly new to the whole linux OS, but want a change from windows and am looking to become more familiar with opensource software.

I've got some questions..

First of all I'm running windows media edition, on a HP AMD athlon 64 dual core processor with a 250 gig hard drive and 1 gb of memory 

After i've burned the Live CD and put it into my computer to install the new OS, I create a partition for my new OS correct?, and install all the software; Will I be able to acess Windows XP with all of my original files and settings AND Ubuntu dependant upon which I choose at bootup? 

Also, making the change to Ubuntu, will I be able to import say my music files from XP to Ubuntu?

The help is much appreciated, and i'm learning as I read more and more of the FAQ's.

---

### Post by Ianman on 2008-03-05
Hi Hutchie,

Welcome! :-)

When you run the Live CD y ou can boot into Ubuntu and try it out without changing your current Windows installation at all! If you are very new to Linux I think this would be a good thing to do first.

Should you decide to create a dual boot situation then it is best if you make room for the Linux partitions (ext3 and swap). I suggest you create enough empty space on your HD first (say 10GB) and then use a partition tool to resize your partition and create an unallocated section of your HD. It would be even better if you could install a second HD for Linux.

In a dual boot situation you will indeed be able to select which OS you start when the computer is switched on. If you load Ubuntu you will be able to access your Windows files but not the other way around.

You will indeed be able import your files from Windows. There is even a wizard during the install of Ubuntu in which you can import your Windows profile. In Ubuntu you will be able to play MP3s, WMV, MOV and pretty much any other media format you like. It may however take a bit of work to get support for all formats as not all formats are supported out of the box in Ubuntu.

I hope this is enough to get you started. Feel free to ask more questions if you have doubts!

Good luck.

---

### Post by oedha on 2008-03-05
you can resize the partition and spare some for ubuntu, maybe you can try gparted ( [http://gparted.sourceforge.net](http://gparted.sourceforge.net) )
and also linux need a swap partition for about 512 - 1gb
you will have dual boot which asked everytime you restart the computer
for your music and pictures....you can share them....

---

### Post by Hutchie on 2008-03-05
awesome, the quick replies are much appreciated...I'll be burning a CD and trying out the LiveCD; to get a feel for it and see if it's worth the switch to me.

---


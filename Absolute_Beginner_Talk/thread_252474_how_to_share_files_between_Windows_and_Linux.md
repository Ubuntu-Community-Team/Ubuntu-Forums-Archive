---
title: "how to share files between Windows and Linux"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by dbonline on 2006-09-06
hello folks. I really need some help and advice here. I'm running Ubuntu as my main OS and I have VMware installed which allows me to run Windows in the background. That all works fine, but the problem I am have is when I copy a file in Windows and go to paste it in Linux, it doesn't even recognize that I copied anything. Now, the strange thing is, I can copy text just fine between OS's just not actual files.

so, to sum it up, basically what I'm trying to figure out is how can I share files between the two OS's? it's very important and I really hope someone here can help!!

thanks in advance

---

### Post by orb9220 on 2006-09-06
Well without vmware running you should see your winxp partition and can copy files from it with nautilus. However you cannot write to a ntfs partition unless you use aditional software like ntfs-3g which would give you that ability but is still consedered experimental.

For data drive sharing like docs,pics,music,movies ect... I have a 2nd hd as fat32 which windows and linux share.

---

### Post by armware on 2006-09-06
you could always install a driver into windows that allows it to read ext2/3 partitions. [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by comppsyco on 2006-09-06
I'm not sure that you guys get it. If he's running vmware, there won't be a ntfs partition. I don't actually know if there's a way to do it, but browse around vmware's help site.

---

### Post by djsroknrol on 2006-09-06
How did you set VMware up?....was it "bridged" or "NAT"?...I believe you could set up a connection as NAT and share your files across Samba that way...

---

### Post by David Corrales on 2006-09-06
You can either use samba or the shared folders utility provided by VMware. Just set a folder in your home folder that the win xp machine will see as a share and add it to the shared folders for that virtual machine.

---

### Post by haiku99 on 2006-09-07
I've done it by using a USB flash drive, Ubuntu and Windows both have no trouble reading and writing files to and from it....

---

### Post by GadgetsGuy on 2006-09-07
Since I set up dbonline's machine, I can tell you that his windows partition is FAT32 specifically so that he can mount it in Linux.

dbonline : as far as your Q goes, yes you can set up Samba to share your WIN32 <<--->> Linux partitions, or as mentioned by somebody else - and I told you same thing personally, a USB thumb drive would be a very simple way to transfer files, not only between the OSes, but between physical machines too ... and you can find thumb drives under $20 all over the place.

\\:D/

---

### Post by fjm03 on 2006-09-08
I'm facing the same dilema specifically because of VMware.

After having played with a SAMBA share I purchsed an inexpensive NAS as a work-around for the exchange challenge. The Hawking hardware worked resonably well until I tried to save a copy of my vitual XP machine. Wow. 30GB takes time to transfer to and from a cheap NAS with a reputation for slow tranfer rates.

---


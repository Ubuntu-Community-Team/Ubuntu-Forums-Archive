---
title: "partition help"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2008-02-02
Hey guys, i dual boot vista and ubuntu atm, and i would like to re-partion the disk by taking away some of the vista space, either to put into the ubuntu partion or another OS, haven't decided yet.

Either way, i couldn't get vista to give up space using the vista partioner, so i loaded up the ubuntu liveCD to use gparted, anyway, i clicked install, then  got to the partitioner and found the vista space, size 76gb, used 51gb, i would like to take 5-10gb off that. 

So i clicked on the vista partition, clicked edit partition, chose the size to be 10,000mb, the ok, continue, ubuntu told me "too small size". Even though at the bottom of the patitioner it says the minimum is 2gb for a partition. What can i do?

---

### Post by chrono310 on 2008-02-02
It may be that there is more than 10GB of data on that partition, so you can't make it smaller than that. Also, if I understand correctly, you're using gparted in the installer? Unless you want to overwrite your current Ubuntu partition or something, you should just use the one in the applications menu.

---

### Post by cubeist on 2008-02-02
Re-sizing vista is a serious step.  It took me hours to do and then the smallest I could get it is 30GB.  The reason is that vista puts hard-locked files that are used for caching and VM and backup on certain parts of the disk.

There are some lengthy tutorial around to de-activate page files and other things in vista, however, it is such a lengthy process and if you don't have at least 2 gb of ram vista will crash without a page file...So my recommendation would be to backup, resize, then reinstall vista... or just leave it as it is because even if you move the system files around in vista you will never get it down to 10 Gb

---

### Post by dstew on 2008-02-02
If you had trouble shrinking your Vista partition using the Vista disk management tools, it is probably because there are immovable files on that partition. These may be page files (like swap in Linux) or shadow files (for some kind of file system restoration, I think). You can try to shrink using gparted, but the gparted program may not respect the immovable files and damage the Vista partition. Better to try again using the Vista tool after disabling and deleting the page files. See [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by Falc7 on 2008-02-05
okay i'll try that tutorial, i tried using gparted, but it gave me that size too small error message as i said in the original post. I don't understand why. 
Gparted from the system menu dosen't work, when i right click on the vista partition, the resize option is greyed out.
I can't uninstall vista atm, because the vista disk hasen't come through from hp yet.

Just to clarify, i am not trying to get vista down to 10gb, i am trying to take 10gb off vista as it is now, now being 76, i would like to take it down to 66.

---


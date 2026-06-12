---
title: "program windows not seen in GNOME Panel"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by nandan on 2008-03-08
Have installed 7.10 and it is working well so far. However, for some reason, it does not show me the open applications in the taskbar (panel), when they are minimized. To see which programs are running, I have to do an alt+tab to cycle through them. Is there any way in which the minimized windows can be seen in the panel? I did not have this problem in 7.04.

Also, I made one more partition on my hard disk for 7.10, but have a lot of programs in 7.04, which is also on another partition of my hard disk (logical partition) Can I use those programs from 7.10? E.g., I have VLC player installed in 7.04...can I use it when in 7.10? I f yes, how do I do it? 

Thanks a lot for your time!

Nandan

---

### Post by glennric on 2008-03-08
Most likely you somehow accidentally removed the window list from the panel.  Right click on an empty spot on the panel and select "Add to Panel..."  Look for "Window List" under "Desktop & Windows" and add it to the panel.

To use what you had installed in 7.04 you will have to install those apps again.

---

### Post by spydon on 2008-03-08
You will probably have to reinstall the applications, but if you use the same home directory the apps use the same settings as they had before and this windows thing sounds like a bug to me...

---

### Post by justsomedude on 2008-03-08
Right click your panel and choose "Add to Panel".

Add "Window List" to your panel.

Concerning your second question: No, you can't. Which is not entirely true, but I recommend you install programs you need for 7.10 seperately.

---

### Post by nandan on 2008-03-08
Thanks a lot! Yes, the window list solved the issue..the problem that i face is that I inadvertently gave  7.10  partition of around 2 GB and that hs limited my options. Could I reformat the whole 7.04 to extend 7.10's disk space? Or would that be as complex as open heart surgery? :)

---

### Post by glennric on 2008-03-08
Yes, you can do that.  You will have to boot to a live cd and use the partition editor (gparted).  With that you can delete the 7.04 partition and then grow the 7.10 partition to use the empty space.  This is assuming the partitions are next to each other on the disk.

---

### Post by glennric on 2008-03-08
I should point out that you should back up anything that you don't want to lose.  This will delete anything on the 7.04 partition, and it could also mess up the 7.10 partition if things go awry.

---


---
title: "Remove unwanted boot options? Edit main.lst?"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by tjp.thomas on 2006-07-27
Hi there
I am still strugling with the dual boot Ubuntu/XP system. Right now I get 5 different Ubuntu start-up options, and the my XP system. Can I in any way remove some of the Ubuntu start-up options? So that I have latest kernel and safemode and XP only?:confused:

---

### Post by stimpsonjcat on 2006-07-27
you can remove the old kernels with synaptic (System >> Administration >> Synaptic Package Manager). this will automatically clean up the GRUB menu.

---

### Post by justicerulesok on 2006-07-27
Which did you install first?  I did xp as its on a recovery cd & wipes the whole hdd.  Then installed partion magic, made partions & then installed other os/ on other partitions.  I also found it messy IF i told pm to to create a linux boot section.  If I don't it is a lot tider & still works fine.

Hope this helps,

Justice.

---

### Post by clarkth on 2006-07-27
If you don't want to uninstall old kernels, just comment out the items you don't want in /boot/grub/menu.lst.  Be sure to make a backup first!  Also, you can retitle any item to make it more descriptive to you.  Add your own comments if you do so you can retrace/restore if necessary.

---

### Post by moma on 2006-07-27
Remove unnecessary kernels
o-> [http://ubuntuforums.org/showthread.php?p=1301606#post1301606]("http://ubuntuforums.org/showthread.php?p=1301606#post1301606")


// moma 
   [http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")

---


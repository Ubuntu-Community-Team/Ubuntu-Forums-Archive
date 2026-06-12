---
title: "Changing Directories in Photorec"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by The Transporter on 2008-02-14
Recovering Data...  I'm in Photorec, and would like to have it recover the files to my external drive (sdb).  When in the shell, it doesn't seem to recognize the "cd" command to change directories, and can't find the either the internal or external drives when I try to mount them to copy the files or photorec to another drive (if it uses the current drive).

I've read articles with people saying they copied their recovered files to the external drive, but they don't say how. The Linux distro that comes with the recovery cd doesn't seem to have a drag and drop window situation, and Midnight Commander was foreign to me.  

Any ideas?

---

### Post by Jimmey on 2008-02-14
There's a dialog that asks if you want to save the recovered files in the current directory. It will allow you to select other directories within the current directory, **or,**, you can select the two dots "..". 

If you select the two dots a couple of times (moving to the parent directory of the current directory), you should eventually reach /. Presumably your external drive is mounted in /media, which should then be selectable.

---


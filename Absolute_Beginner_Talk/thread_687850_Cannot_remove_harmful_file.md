---
title: "Cannot remove harmful file"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Thyzer on 2008-02-04
I recently started having problems with my computer running very slowly, and after looking through the system monitor I found that the problem was a process that continually consumed more and more RAM. I stopped the process (called trackerd), and the computer stopped constantly loading, as it had been all day, but the ram was still taken up. So I took the risk of killing the process (end process didn't work), and it gave me my RAM back. However, every time I turn the computer on, it starts this process, and I have to go in and kill the process. So I tracked the file down, but its in the usr/bin file, and it says I'm not authorized to change it or its parent folder, so i can't delete it. Is there a way to override that so I can delete it, or to at least keep it from being loaded when the computer boots?

---

### Post by Blutack on 2008-02-04
Go into Preferences --> Sessions 
and untick trackerd.  It's an indexing daemon that lets you search instantly through all your emails/files and stuff if you were interested.

---

### Post by Waappu on 2008-02-04
Hi

See if this helps your problem
[http://ubuntuforums.org/showthread.php?t=591867](http://ubuntuforums.org/showthread.php?t=591867)

---

### Post by Thyzer on 2008-02-04
Got it, thanks guys!

---


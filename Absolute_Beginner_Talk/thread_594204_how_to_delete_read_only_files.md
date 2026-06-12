---
title: "how to delete read only files ?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Simple512 on 2007-10-27
I stupidly imported my xp account / settings ( i dont know why ) and it copied alllllllllllllllllllll of the program files, the windows folder ( ??? ) to the sda1 partition where ubuntu is installed. Nothing conflicts but it takes up alot of space and i need to delete it b/c its useless. How do i do it, when i drag it to trash it just says i cant do that.

---

### Post by DezSP on 2007-10-27
You need to be root. Easiest way is to press Alt+F2, then type "gksu nautilus /" (without quotes); that'll give you a root file manager. Make sure you empty root's trash (stored in /root/.Trash), not your own, though if the folders are huge they probably won't be sent there anyway.

---


---
title: "&quot;Do not have permissions&quot; error"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Puptentacle on 2007-12-06
Hello all, long time no post! 

I recently was gifted with an HP laptop. FIRST thing I did was remove Vista and install Ubuntu. After several changes (7.10 32bit to Mandriva and to 7.10 64bit) I'm left with a file on my storage partition that goes back to the original 32bit install that I cannot access. It's giving me "You do not have the permissions necessary to view the contents of..." when I try to open it. Any way to change this? chmod doesn't seem to work. Thanks in advance!

---

### Post by wormser on 2007-12-06
Who is the owner of the partition and how is it formatted?  You could use **chown** and **chgrp** to change the owner and group.  Are you using sudo or gksudo before opening?  Give those a try and let us know how it goes.

---

### Post by aysiu on 2007-12-06
Press Alt-F2 and type ```
gksudo thunar
```

---


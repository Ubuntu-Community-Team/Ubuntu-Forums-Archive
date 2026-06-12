---
title: "[SOLVED] Backups for Windows and Mac OS X"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-09-06
Hi,

I have successfully set up my first stripped down Ubuntu Samba server to use as a file server. I want to back up some Windows and Mac OS X machines to the Ubuntu file server and I want to do a full backup and then incremental thereafter on both types of system.

What's the best way to do this? Can I use rsync on windows, Mac OS X? What's the best backup tool to use that gives full and incremental functionality on Windows and OS X?

Thanks

---

### Post by wirelessmonkey on 2007-09-06
1)  Yes
2) Script it yourself, or use BackupPC or AMANDA

---

### Post by keymoo on 2007-09-06
Thanks what scripting language would you use on windows and os x? Which utility to do the actual work?

---

### Post by hyper_ch on 2007-09-06
On windows you can install Cygwin that will provide rsync... on Mac OS X - no clue...

---

### Post by wirelessmonkey on 2007-09-06
OS X has rsync natively I believe. You can use cygwin rsync or DeltaCopy for Windows. 
You can also mount either as a samba share and compress via tar.

---

### Post by HermanAB on 2007-09-06
Rsync is your friend.

---

### Post by keymoo on 2007-09-12
Thanks for all your replies. I set up BackupPC with samba on linux and OS X clients and it works great. I might look into using rsync one day on the windows and OS X clients - but it's working great with samba for now. The pooling and compression is very clever. Great script.

---


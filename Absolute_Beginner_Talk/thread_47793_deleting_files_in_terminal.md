---
title: "deleting files in terminal"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by xbilly on 2005-07-10
After playing around and learning how to do stuff... i have ended up with certain files and folders extracted in places i dont want. How can i delete these files in terminal since I do not have permission to so otherwise?

---

### Post by kvidell on 2005-07-10
[QUOTE=xbilly]After playing around and learning how to do stuff... i have ended up with certain files and folders extracted in places i dont want. How can i delete these files in terminal since I do not have permission to so otherwise?[/QUOTE]
 sudo rm -i file1 file2 file3 so on and so forth

---

### Post by xbilly on 2005-07-10
thank you, an whole directories?

---

### Post by Leif on 2005-07-10
rm -R dir. In general, if you want to find out about the options of a command, try it with the --help option, ie. rm --help. If you want more in-depth data, use man rm.

---


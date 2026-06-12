---
title: "Can't get video out of WINE Folder"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by David2569 on 2007-08-21
I used WINE to install shareaza, and i downloaded a movie but how do i get it on to my desktop? and more importantly how do i get to the file because it is in the directory of shareaza and i don't know where that is ?:confused:

---

### Post by dragomirov on 2007-08-21
Open the file manager (nautilus) then press ctrl+h in order to see hidden files/folders. Look for a folder named **.wine**, then go to dosdevices or drive_c folder; there you will find the windowz file structure.

Another tip is to open the terminal, launch **winecfg** by simply typing the command and press enter :). Look for the tab named **Drives**, there you can have a llok how your virtual drive are managed.

---

### Post by David2569 on 2007-08-21
Nice... worked like a charm... cheers for that, i was beginning to think i had got it for nothing, but now it's all good... and thanks again... it's helped me a lot

---

### Post by dragomirov on 2007-08-23
glad to be helpful. :lolflag:

---


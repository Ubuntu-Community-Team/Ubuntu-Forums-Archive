---
title: "move many files as root??"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by sirfonners on 2008-04-05
I want to move all my Microsoft core fonts from

/usr/share/fonts/truetype/msttcorefonts

to

/home/sirfonners/.wine/drive_c/windows/fonts


I cant do it by drag and dropping because it says I dont have permission
how can i move them all?

---

### Post by shawnjones on 2008-04-05
Try this:

sudo mv /usr/share/fonts/truetype/msttcorefonts *.* /home/sirfonners/.wine/drive_c/windows/fonts

You can also change the *.* to a different extention, eg. *.ttf , *.TTF , *.txt , etc.

Hope it helps.

Shawn

---

### Post by sirfonners on 2008-04-05
I did that but I think it just moved things from my home foldeR??

---

### Post by Ptero-4 on 2008-04-05
Does it show that error when moving the fonts as root? Also are you using anyone of those fonts in your desktop?

---

### Post by shawnjones on 2008-04-05
Sorry try this

sudo mv /usr/share/fonts/truetype/msttcorefonts/* /home/sirfonners/.wine/drive_c/windows/fonts

also you said that you wanted to move, you may just want to copy, just change "mv" to "cp"

Too much multitasking going on here, sorry again.

---

### Post by sirfonners on 2008-04-05
> **shawnjones said:**
> Sorry try this

sudo mv /usr/share/fonts/truetype/msttcorefonts/* /home/sirfonners/.wine/drive_c/windows/fonts

also you said that you wanted to move, you may just want to copy, just change "mv" to "cp"

Too much multitasking going on here, sorry again.

FANTASTIC! thank you so much, I was looking forever for the right code to use. I will have to remember that:guitar:

---

### Post by lswest on 2008-04-05
yeah, however, those fonts (if you used mv) are no longer in the original folder, cp would be what you want to use to keep them in the original folder.

---

### Post by shawnjones on 2008-04-05
If you did issue the mv command, you should use this command to copy the fonts back to their original directory

sudo cp /home/sirfonners/.wine/drive_c/windows/fonts/* /usr/share/fonts/truetype/msttcorefonts/

This will place the fonts in both places so other applications still have access.

Glad it worked for you, good luck.

Shawn

---

### Post by twright on 2008-04-05
if you want to do it in a visual way you can use 'gksu nautilus' to open the file manager as root

---


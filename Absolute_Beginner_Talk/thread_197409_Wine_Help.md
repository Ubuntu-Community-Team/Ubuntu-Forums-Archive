---
title: "Wine Help"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by truNWA on 2006-06-15
I installed a demo of Emperor:Rise of the Middle kingdom on wine. I just can't figure out how to run it. It would be saved in windows as C:\Sierra\EmperorRotMKDemo.

---

### Post by sgtBiafra on 2006-06-15
Hmm... I don't know where to begin.

Does this mean that from a terminal window you've traversed into the installation folder (/home/*user*/.wine/drive_c/Sierra/EmperorRotMKDemo)
and then run the executable for the demo (i.e. 'wine EmperorDemo.exe')?

Or did you get that far and then received some error messages?

---

### Post by CarpKing on 2006-06-15
Did you install it through wine, or is it installed on a windows partition?  If you installed it through wine, it is likely in /home/(username)/.wine/drive_c/Sierra/EmperorRotMKDemo, though this will depend on how you have your drives set up in wine.  In any case, open up the terminal and type cd and then whatever the path after your username is.  Then when you are in the proper directory, type wine (name of exe.exe).  

Alternatively, you could open up your home folder, press ctrl+h to view hidden directories, and open up the folder .wine to look for the exe.  When you find it, right click and go to "open with wine windows emulator."

---

### Post by truNWA on 2006-06-15
I installed it though wine and i haven't changed any drives in wine so i guess they're default.

---


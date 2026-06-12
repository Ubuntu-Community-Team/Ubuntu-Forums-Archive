---
title: "Where does WINE install files to?"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-03-14
I downloaded the deb file of WINE -- it installed without a hitch. Then installed Quickbooks -- again without a hitch -- except that it told me that the files were being installed to the Windows directory structure -- Programs/Intuit/... (or whatever). As usual the Windows app asks if I want to create an icon on the desktop, to which I answered "Yes". There's no icon (which I pretty much expected), but where are the files? Where did WINE install the app? I'm sure the executable file will run -- if I could find it.

---

### Post by divague on 2007-03-14
Go to:

$ cd ~/.wine/drive_c

there should be the installed files

---

### Post by adamr on 2007-03-14
if you open up a terminal window and type
```
winecfg
```
If you look at the 'desktop integration' tab (I think it's that one), you'll see the default locations for the corresponding windows folders (e.g. My Documents, Desktop etc.). They'll show you where it is for now, and allow you to change it to somewhere else if needs be.

(I'm at work right now and can't check 100%, I'm pretty sure that's right though)

---

### Post by lwalper on 2007-03-14
You're both correct. Thanks! I had to open the hidden folders to get to it. Now, is there a way to create a link on the desktop (or some other convenient place) to the executable file?

---

### Post by eljalill on 2007-03-14
Well, you could always link your YourProgram.exe, however that would do much good, since you have to open this file with wine .

So you would need to do a custom command or so.

You have to create a .sh in /usr/local/bin, make it executable (sudo chmod +x ) , and write:
#!/bin/sh
wine /home/USER/.wine/drive_c/[and so on... the path to your programm]
and save the whole thing.

With this (./???.sh) you should be able to start your program from the terminal. Of yourse you can also create a link in to your desktop with ln. (For more about the ln command type man ln into a terminal)

Hope this was of help,

Cheers

---

### Post by AtrejuT on 2007-03-14
apparently (at least for me) wine creates .desktop files automatically for any programm you install. these are located in
/home/yourusername/.local/share/applications/wine/Programs/programfolder/program.desktop

if you link to these:
```

cd /home/yourusername/desktop
ln -s /home/yourusername/.local/share/applications/wine/Programs[etc]

```

have fun

atreju

---

### Post by lwalper on 2007-03-15
Is there any way to print the man ln information? There's no print option in the window and I cannot copy/paste into the wordprocessor.

---


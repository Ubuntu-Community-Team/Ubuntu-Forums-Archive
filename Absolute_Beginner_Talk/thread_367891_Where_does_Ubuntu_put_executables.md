---
title: "Where does Ubuntu put executables?"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by elaich on 2007-02-22
Looking all over for XMMS, so I can associate mp3 files with it. Can't find it anywhere. In Windows this is so easy, and probably is in Linux, too, but I don't understand the file structure. I have an icon on my launch bar for it, so I must have found it when I installed it.

There is an .xmms folder in my home directory, but no executable there. I can right click the icon in Windows, select Properties, and see where the file is. Not so in Linux.

---

### Post by annda on 2007-02-22
usually /usr/bin or /usr/share

you can find any file by running

sudo updatedb

and then

locate what_you_need

---

### Post by Maestro23 on 2007-02-22
> **elaich said:**
> Looking all over for XMMS, so I can associate mp3 files with it. Can't find it anywhere. In Windows this is so easy, and probably is in Linux, too, but I don't understand the file structure. I have an icon on my launch bar for it, so I must have found it when I installed it.

There is an .xmms folder in my home directory, but no executable there. I can right click the icon in Windows, select Properties, and see where the file is. Not so in Linux.

Open terminal and type: 

which <program name>: will give the path to the .bin file.

/usr/bin

Linux commands/fie structure: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by linux_kid on 2007-02-22
Linux dosen't use .exe's as Windows does.  I'm not sure how to find the exectuable, but I hope this can clear a little fog out of your Windows window.

---

### Post by elaich on 2007-02-22
Thanks for the help, and thanks for that link, Maestro.

---

### Post by nickoli_02 on 2007-02-22
A menu entry for xmms should have been added under Applications -> Sound and Video when you installed it...

---

### Post by Maestro23 on 2007-02-22
> **elaich said:**
> Thanks for the help, and thanks for that link, Maestro.

No prob.  Here is another good one: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

---

### Post by sloggerkhan on 2007-02-22
you should be able to right click on any mp3 file and choose choose properties, go to "open with" and choose what app to associate it with by default. The change should automatically apply to all files of the same type.

---


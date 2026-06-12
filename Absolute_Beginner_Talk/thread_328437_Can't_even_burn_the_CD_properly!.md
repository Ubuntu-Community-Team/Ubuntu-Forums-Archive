---
title: "Can't even burn the CD properly!"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Gengineer on 2006-12-30
Hello, my husband really wants ubuntu on his computer.  We have been burning CDs left, right and center on our CD RW drive all day.  However, when we try to open the program downloaded onto the CD we get a message asking us to choose the program we want to open this file with.....

I am assuming we are not burning it correctly or are missing a step.

Currently our computer is a standard windows XP operating system.

Thanks for your time and help,  Catherine.

---

### Post by Sef on 2006-12-30
You need to burn it as an iso file and not a data file.   

First, read [How to Write an iso file to a cd]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm").

Next download [isorecorder]("http://isorecorder.alexfeinman.com/isorecorder.htm").  It is a no cost program that only burns isos to a cd.

---

### Post by obsidion on 2006-12-30
> **Gengineer said:**
> Hello, my husband really wants ubuntu on his computer.  We have been burning CDs left, right and center on our CD RW drive all day.  However, when we try to open the program downloaded onto the CD we get a message asking us to choose the program we want to open this file with.....

I am assuming we are not burning it correctly or are missing a step.

Currently our computer is a standard windows XP operating system.

Thanks for your time and help,  Catherine.

What are you trying to open, did you just copy the iso to the disk ?
  You've got to burn it as an image, hopefully your burning software gives you that option.
Another note you cannot run ubuntu from xp, it is a complete os not a program.

---

### Post by raul_ on 2006-12-30
> **obsidion said:**
> Another note you cannot run ubuntu from xp, it is a complete os not a program.

Actually the Edgy Live CD can be loaded with XP running, but only provides windows's versions of open source programs (like Firefox)

---

### Post by 3rdalbum on 2006-12-31
When you've correctly burnt the CD and put it into your drive, you will see a whole bunch of folders on it.

Now reboot with the CD in the drive. When your computer first turns on (i.e. before Windows starts to load), you will see some text on the screen, possibly like this:

```

<Esc> Boot Sequence

or

Press Backspace to enter SETUP

```

Something similar to that. Press the key specified (i.e. Escape in the first example), and follow the onscreen instructions to change the boot sequence. Set it so that the CD/DVD drive is on top. Exit your setup screen, and Ubuntu's menu should appear. If not, try restarting again.

---


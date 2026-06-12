---
title: "Command Line Launcher [Resolved]"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by ushills on 2007-04-13
I am looking to create an icon on my desktop to run the following terminal command

```
sudo cpbk /home /media/dvd --exclude="/home/ian/Archive,/home/ian/Music,/home/ian/Podcasts"
```

I could do this in Windows with a bat file, how can I do this in ubuntu.

---

### Post by aysiu on 2007-04-13
> **ushills said:**
> I am looking to create an icon on my desktop to run the following terminal command

```
sudo cpbk /home /media/dvd --exclude="/home/ian/Archive,/home/ian/Music,/home/ian/Podcasts"
```

I could do this in Windows with a bat file, how can I do this in ubuntu.
You can create a shell script.

Open your favorite text editor.

Paste this text in: ```
#!/bin/bash
sudo cpbk /home /media/dvd --exclude="/home/ian/Archive,/home/ian/Music,/home/ian/Podcasts"
``` Save it and close the text editor. Right-click the file. Select Properties. In Permissions, mark it as executable.

Then, when you want to run it, double-click it (assuming you're in Gnome--it's a little tricker in KDE or Xfce).

---

### Post by ushills on 2007-04-13
Thanks that worked fine:)

---


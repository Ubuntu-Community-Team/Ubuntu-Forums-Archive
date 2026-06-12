---
title: "How do I extract a RAR file if I need root access?"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by thunderstorm on 2007-01-13
I've been using Linux for a while now, but I just hit a big snag.  I'm not familiar with the Command Line interface enough to figure out how I can extract a RAR file to /opt/lamp.  This would require root access so I know I have to type sudo and then the command, but I can't get a combination of commands to do anything.

What would I type to extract a rar file on my desktop to /opt/lamp?  I know, I'm a newb...

---

### Post by Iarwain ben-adar on 2007-01-13
```
sudo aptitude install p7zip p7zip-full
```

This installs 7z,

Then just enter this command
```
sudo 7z e your_rar.rar /opt/lamp
```


This should do the trick :D


Iarwain

---

### Post by thunderstorm on 2007-01-13
Error:
cannot use absolute pathnames for this command


I'm typing in this:  sudo 7z e /home/user/Desktop/file.rar /opt/lamp

---

### Post by Iarwain ben-adar on 2007-01-13
Try this then:
```
7z e file.rar
sudo cp contents_of_file /opt/lamp
```

This could work


Iarwain

---

### Post by ajmorris on 2007-01-13
if that doesn't work get the rar package from the repositories (sudo aptitude install rar) from the command line. (the package might be unrar though, try both)

---


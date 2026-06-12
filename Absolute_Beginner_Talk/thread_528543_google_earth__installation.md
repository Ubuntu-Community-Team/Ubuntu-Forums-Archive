---
title: "google earth  installation"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by jon zendatta on 2007-08-18
problems installing after downloading bin file on ubuntu 7.04

---

### Post by Arisna on 2007-08-18
How did you try to install it?  Did you get an error message?  If so, what did it say?

---

### Post by jon zendatta on 2007-08-18
could not open the file /home/jon/Desktop/GoogleEarthLinux.bin
gedit has not been able to detect the character open. as have the option to open using Unicode or ISO.
so i tried this command-
sudo apt-get install /home/jon/Desktop/GoogleEarthLinux.bin
as you've guessed i'm 2 weeks new to this & need simple explaination.

---

### Post by Perfect Storm on 2007-08-18
It's

```
sudo sh <path>/GoogleEarthLinux.bin
```

gedit is text editor
apt-get is a command to communicate ubuntu's central package facility, so you can't use apt-get on a manual downloaded file.

---


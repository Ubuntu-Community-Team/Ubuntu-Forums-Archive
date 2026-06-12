---
title: "unable to intall firefox 1.5.0.1"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by candide on 2006-02-21
i am trying to install firefox 1.5
i have downloaded the firefox.tar.gz to my desktop, and when i type:

sudo tar -C /opt -x -z -v -f firefox-1.5.0.1.tar.gz

in console, nothing happens and it says:cannot open, so such file.
I am following instructions from here:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

what is going on?

---

### Post by kaamos on 2006-02-21
Hello!

If the tile is on your desktop, you should move there before using the command. So try
```
cd Desktop
sudo tar -C /opt -x -z -v -f firefox-1.5.0.1.tar.gz
```

Cd changes directories. You can use the command "pwd" if you don't know where you are. "ls" lists files and directories. "cd .." goes one directrory backwards. Anyway, if the file is on the desktop, you should go to /home/candide/Desktop (remeber that names are case sensitive)

---

### Post by bluevoodoo1 on 2006-02-21
did you 

```

cd Desktop  

```

first??

EDIT: kaamos beat me.

---

### Post by Coelocanth on 2006-02-21
Have you changed location to your desktop in terminal?

cd Desktop

*edit* D'oh. *Way* too slow!

---


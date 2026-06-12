---
title: "Runlevel and X windows"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by johnnybgood115 on 2007-02-08
I'm trying to install the driver's for my NVIDIA Geforce 3 graphics card.  Followed all the instructions on the NVIDIA website however I keep receiving an X windows error and it tells me that I need to disable the X windows and run the install through command prompts.  I understand all this and have looked up numerous help documents explaining how to stop X windows from running automatically.  I can't find how to disable this in Ubuntu.  Is there anyway to disable X windows from opening in Ubuntu and boot up through the command prompt after the operating system has loaded.  

thanks

---

### Post by RomeReactor on 2007-02-09
Hi. One way to disable X after the system boots is to press **CTRL+ALT+F1**; that will send you to the command line and you will be asked to login. After that, write

```
sudo /etc/init.d/gdm stop
```

Then run the installation commands, and when you finish, type

```
sudo /etc/init.d/gdm start
```

and the press **CTRL+ALT+F7**; that will bring you back to your desktop.

---


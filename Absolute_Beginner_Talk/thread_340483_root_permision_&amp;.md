---
title: "root permision &amp;"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Homie_S on 2007-01-17
Hi guys !

Im new on the forum, and totaly new to Linux. (did my first install EVER yesterday)

I was looking for a good FPT client that had a good GUI and found IglooFTP.

But i have a slight problem to install it, i think ?

This is how it looks when i try installing it:

> homie@homie:~/DOWNLOADS/IglooFTP-PRO-1.2.5-linux$ ./Install
mkdir: cannot create directory `/usr/local/IglooFTP-PRO': Permission denied
mkdir: cannot create directory `/usr/local/IglooFTP-PRO/bin': No such file or directory
mkdir: cannot create directory `/usr/local/IglooFTP-PRO/share': No such file or directory
mkdir: cannot create directory `/usr/local/IglooFTP-PRO/share/docs': No such file or directory
mkdir: cannot create directory `/usr/local/IglooFTP-PRO/share/html': No such file or directory
mkdir: cannot create directory `/usr/local/IglooFTP-PRO/share/html/images': No such file or directory
mkdir: cannot create directory `/usr/local/IglooFTP-PRO/share/xpm': No such file or directory
mkdir: cannot create directory `/usr/local/IglooFTP-PRO/share/bookmarks': No such file or directory
mkdir: cannot create directory `/usr/local/IglooFTP-PRO/share/app_***': No such file or directory
mkdir: cannot create directory `/usr/local/IglooFTP-PRO/share/icons': No such file or directory
/usr/bin/install: cannot create regular file `/usr/local/IglooFTP-PRO/bin': No such file or directory
/usr/bin/install: target `/usr/local/IglooFTP-PRO/share/docs/' is not a directory: No such file or directory
/usr/bin/install: target `/usr/local/IglooFTP-PRO/share/docs/' is not a directory: No such file or directory
/usr/bin/install: target `/usr/local/IglooFTP-PRO/share/docs/' is not a directory: No such file or directory
/usr/bin/install: target `/usr/local/IglooFTP-PRO/share/docs/' is not a directory: No such file or directory
/usr/bin/install: target `/usr/local/IglooFTP-PRO/share/xpm/' is not a directory: No such file or directory
/usr/bin/install: cannot create regular file `/usr/local/IglooFTP-PRO/share/xpm/splash.xpm': No such file or directory
/usr/bin/install: target `/usr/local/IglooFTP-PRO/share/icons/' is not a directory: No such file or directory
/usr/bin/install: target `/usr/local/IglooFTP-PRO/share/bookmarks/' is not a directory: No such file or directory
/usr/bin/install: target `/usr/local/IglooFTP-PRO/share/app_***/' is not a directory: No such file or directory
/usr/bin/install: cannot create regular file `/usr/local/IglooFTP-PRO/share/gtkrc-2.0': No such file or directory
/usr/bin/install: target `/usr/local/IglooFTP-PRO/share/html/' is not a directory: No such file or directory
/usr/bin/install: target `/usr/local/IglooFTP-PRO/share/html/images/' is not a directory: No such file or directory
ln: creating symbolic link `/usr/local/bin/IglooFTP-PRO' to `/usr/local/IglooFTP-PRO/bin/IglooFTP-PRO': Permission denied

-------------------------------------------------------------------------
IglooFTP-PRO has been installed in /usr/local/IglooFTP-PRO directory.
-------------------------------------------------------------------------

To start IglooFTP-PRO enter at the prompt:
"/usr/local/bin/IglooFTP-PRO" or just "IglooFTP-PRO"

Anyone who can tell me what im doing wrong here ?

Thanks in advance  /Homie

---

### Post by taurus on 2007-01-17
```
sudo ./Install
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Homie_S on 2007-01-17
WoW !!

It's that easy  :D


well thanks for the information.
Mutch needed in the future probably.  :)


/Homie

---


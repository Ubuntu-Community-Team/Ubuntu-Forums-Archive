---
title: "Problem With apache"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by WojtekX on 2005-12-21
Apache used to work perfectly but after remotely restarting it im now having a problem... for some reason Apache/1.3.33 is installed.  I never installed that version so im not sure where its coming from... I've tried to uninstall apache and php and reinstall it, but it fails saying that another program is broadcasting on port 80.  I've tried doing apt-get remove apache but it says that this does not exist.   I remember opening backports but i dont think that was it

I've followed most of the things suggested in the PHP4 with Apache thread [http://www.ubuntuforums.org/showthread.php?t=105107](http://www.ubuntuforums.org/showthread.php?t=105107)

please help me

BTW im using Ubuntu Breezy 5.10

---

### Post by kaamos on 2005-12-21
To see what apache packages you have installed you can use this command in terminal:
```
dpkg -l | grep -i apache
```
Note that "apache" is version 1.3.xx and "apache2" is a separate package. Hope this helps some.

---


---
title: "Ubuntu Won't Start Up"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by mikaelsnavy on 2007-03-26
Hello,
Somehow (let's not get into details...)  The device bus id got deleted in my /etc/x11/xorg.conf file. Is there anyway besides re-installation to fix the file? GDM wont start up and I get to a command interface. BTW, I am pretty noobish.
Thanks,
Mikael

---

### Post by profXavier on 2007-03-26
Not sure what you mean, but you probably have a backup of your xorg.conf that you could use. Check in your /etc/X11 for any other xorg.conf that you can replace it with, so you can get your system up.

If you need to setup your drivers, take a look at the [Ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") as a reference.

What type of video card do you have?

---

### Post by mikaelsnavy on 2007-03-26
Lol, there was a thread right above mine with the same question.
[http://ubuntuforums.org/showthread.php?t=393206](http://ubuntuforums.org/showthread.php?t=393206)
I followed directions and I fixed it (kind of by myself)
lol. ty anyways (ati, I got the driver installed for it, the fx or fg whatever one)

---

### Post by NikoC on 2007-03-26
When you enter a terminal you can:
```
sudo dpkg-reconfigure xserver-xorg
```
This allows you to make a new xorg.conf.
Most of the configuration option can be set to default.
But just to make sure first do:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
This will make a backup of your xorg.conf file which, in case of an emergency, you can use to recover your old settings!

---


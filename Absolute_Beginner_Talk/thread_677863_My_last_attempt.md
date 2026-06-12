---
title: "My last attempt"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by leafhound on 2008-01-25
I have a USB modem and driver

I am trying to run it on KDE Kubuntu Gusty

so far
I have managed to extract the firmware files and copy them to the appropriate location.

the part i'm stuck on is configuring the connection as the instructions are for Gnome not KDE
[https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm)
stuck on the configuraton part about half way down the page

```
gksudo gedit /etc/ppp/peers/ueagle-atm

gksudo gedit /etc/ppp/chap-secrets

gksudo gedit /etc/ppp/pap-secrets

gksudo gedit /etc/init.d/modem-startup
```

so i use kdesu kwrite to open up the txt files and it works but with errors in the terminal

```
john@kubuntu:~$ kdesudo kwrite /etc/ppp/peers/ueagle-atm
Error: "/var/tmp/kdecache-john" is owned by uid 1000 instead of uid 0.

Error: "/tmp/kde-john" is owned by uid 1000 instead of uid 0.

Error: "/tmp/ksocket-john" is owned by uid 1000 instead of uid 0.

john@kubuntu:~$ kdesudo kwrite /etc/ppp/chap-secrets
Error: "/var/tmp/kdecache-john" is owned by uid 1000 instead of uid 0.

Error: "/tmp/kde-john" is owned by uid 1000 instead of uid 0.

Error: "/tmp/ksocket-john" is owned by uid 1000 instead of uid 0.

john@kubuntu:~$ kdesudo kwrite /etc/ppp/peers/ueagle-atm
Error: "/var/tmp/kdecache-john" is owned by uid 1000 instead of uid 0.

Error: "/tmp/kde-john" is owned by uid 1000 instead of uid 0.

john@kubuntu:~$ kdesudo kwrite /etc/ppp/pap-secrets
Error: "/var/tmp/kdecache-john" is owned by uid 1000 instead of uid 0.

Error: "/tmp/kde-john" is owned by uid 1000 instead of uid 0.

Error: "/tmp/ksocket-john" is owned by uid 1000 instead of uid 0.
```


I tried running as root to open the txt files up

sudo passwd root

but have the same errors, even when trying kdesu konqueror the same error comes up,

---

### Post by ynef on 2008-01-25
Well, since it's complaining about those files having some other owner than the user with id 0 (that would be root), you should just write the following in a terminal: "sudo chown root filename" where you substitute "filename" for each of the files it's complaining about. The command simply changes the owner (hence ch-own, change owner) of the file to root.

---

### Post by leafhound on 2008-01-25
I will try that and report back here

---

### Post by leafhound on 2008-01-25
I tried it with the first file
/etc/ppp/peers/ueagle-atm

And it said no such directory, so i checked and it was right. just not happening so i will stick with windows.

---

### Post by rosegarden78 on 2008-01-25
No need to choose just dual boot.  Sorry to hear your first experience was so bad.  I posted something [here]("http://ubuntuforums.org/showthread.php?t=677959") that might lift your spirits.  Don't give up! :KS

---

### Post by nowshining on 2008-01-26
was this a dialup usb modem?

---

### Post by jfinkels on 2008-01-26
Hmm, have you perhaps tried editing using the program "nano"?
```
sudo nano /etc/ppp/peers/ueagle-atm
```

You might not get those pesky KDE errors that way....

The reason you can't change the permissions of those files is that they were temporary files created either by kdesu or by kwrite (or some other KDE program), I'm not sure which one exactly.

---


---
title: "xfce install problem"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by champ_rock on 2006-07-07
i have  xfce-4.2.3.2-src.tar.bz2 

i want to know how to install it? .. i have extracted it.. but after that it shows a lot of more archives... what should i do?

```


root@ubuntu:/home/ubuntu# cd xfce-4.2.3.2/
root@ubuntu:/home/ubuntu/xfce-4.2.3.2# ls
src
root@ubuntu:/home/ubuntu/xfce-4.2.3.2# cd src/
root@ubuntu:/home/ubuntu/xfce-4.2.3.2/src# ls
dbh-1.0.24.tar.gz              xfce4-session-4.2.3.tar.gz
gtk-xfce-engine-2.2.8.tar.gz   xfce4-systray-4.2.3.tar.gz
libxfce4mcs-4.2.3.tar.gz       xfce4-toys-4.2.3.tar.gz
libxfce4util-4.2.3.2.tar.gz    xfce4-trigger-launcher-4.2.3.tar.gz
libxfcegui4-4.2.3.tar.gz       xfce-mcs-manager-4.2.3.tar.gz
xfcalendar-4.2.3.tar.gz        xfce-mcs-plugins-4.2.3.tar.gz
xfce-4.2.3.2.md5               xfce-utils-4.2.3.tar.gz
xfce4-appfinder-4.2.3.tar.gz   xfdesktop-4.2.3.tar.gz
xfce4-iconbox-4.2.3.tar.gz     xffm-4.2.3.tar.gz
xfce4-icon-theme-4.2.3.tar.gz  xfprint-4.2.3.tar.gz
xfce4-mixer-4.2.3.tar.gz       xfwm4-4.2.3.2.tar.gz
xfce4-panel-4.2.3              xfwm4-themes-4.2.3.tar.gz
xfce4-panel-4.2.3.tar.gz
root@ubuntu:/home/ubuntu/xfce-4.2.3.2/src# tar xvf xfce-4.2.3.2-src.tar
tar: xfce-4.2.3.2-src.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
```

---

### Post by T700 on 2006-07-07
If something is in the repositories, that is a much easier way to install.  Please see the link in my sig for more details.

Paul

---

### Post by Kilz on 2006-07-07
If all you want is to install the Xfce desktop. 
```
sudo aptitude install xubuntu-desktop 
```
should install it for you without any problems.

---

### Post by FredB on 2006-07-07
And you will get a younger version than the one you're trying to install. Xubuntu => Xfce 4.3.90.1, and the one you're trying to use was made on november 2005 !

> 
**2005/11/15 - Xfce 4.2.3.2 released**  A "micro" release to fix a regression in the window manager settings, get it from one of the download locations from [this page]("http://www.xfce.org/index.php?page=download&lang=de"), the change log for 4.2.3 remains [here]("http://www.xfce.org/release_notes/4.2.3.1_changelog.html").

Source ? [http://www.xfce.org/](http://www.xfce.org/)

---

### Post by Dr. Nick on 2006-07-07
[http://www.psychocats.net/ubuntu/xubuntu.php](http://www.psychocats.net/ubuntu/xubuntu.php) will help you install xfce. The way you are trying would require you to compile it all from source, which can be time consuming and would require alot of work.

---

### Post by champ_rock on 2006-07-07
ok will go through the long way

actually i got this version by some linux magazine.. so i thought that instead of downloading 25 mb on my dialup.. i woould use this...

---

### Post by FredB on 2006-07-07
A simple look at [http://www.xfce.org/](http://www.xfce.org/) could gave you some infos ;)

---


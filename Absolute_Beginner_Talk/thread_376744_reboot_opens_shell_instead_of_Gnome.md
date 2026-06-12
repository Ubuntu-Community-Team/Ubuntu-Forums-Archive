---
title: "reboot opens shell instead of Gnome"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by marciano#1 on 2007-03-05
After I removed app NetworkManager I cannot get my Desktop but shell.
How can I correct this?
Thank you

---

### Post by taurus on 2007-03-05
What happens if you run this command after you log in?

```
sudo /etc/init.d/gdm start
```

---

### Post by marciano#1 on 2007-03-05
command not found !!  (I am writing well)  (Thank you
Another graph interfase? I don't know.  Kubuntu 6.10

---

### Post by taurus on 2007-03-05
Since it's KDE, then 

```
sudo /etc/init.d/kdm start
```

---

### Post by marciano#1 on 2007-03-05
"KDM already running"

---

### Post by taurus on 2007-03-05
What happens if you press <Alt>F7?  Do you see a KDM login screen?  Otherwise, post the output of this command here.

```
ps -A
```

---

### Post by marciano#1 on 2007-03-05
(I am posting from another computer)
Alt F7 -> black screen with a single blinking cursor
ps -A  -> long list
4515 ? 00:00:00:00 apache2
4553 tty1  00...   bash
4580 tty1  00    ps
 
are the three bottom lines
Previous ones contain something similar but nfsd, rpc.mountd, ondemand, hcid, sdpd, krfcommd, atd, cron, lockd rpciod/0

---

### Post by taurus on 2007-03-05
Okay, let's ask this question first to get it over with.

Do you have Ubuntu or Kubuntu on your machine?  You have Gnome in the title but said you use Kubuntu 6.10 in #3.

Look if you see a line that has **kdm** in there with that command.

```
ps -A | more
```
That would be the pipe, |, not letter l from above and hit the space bar for the next 24 lines.

---

### Post by marciano#1 on 2007-03-05
It is a four screens of data.
May I ps -A >data and then send this file to 192.168.1.1? Which command can I use?

$startx says smth about no video modes for chosen depth. Screens found but none have usable configuration

---

### Post by taurus on 2007-03-05
Okay, that would narrow down a lot.  It's a problem with /etc/X11/xorg.conf.  Can you post your /etc/X11/xorg.conf here 

```
cat /etc/X11/xorg.conf
```
or you can reconfigure it again with

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```
Make sure you use Depth 24.

---

### Post by marciano#1 on 2007-03-05
Well, back to the normality. 
sudo /etc/init.d/kdm restart
Thank you.

---


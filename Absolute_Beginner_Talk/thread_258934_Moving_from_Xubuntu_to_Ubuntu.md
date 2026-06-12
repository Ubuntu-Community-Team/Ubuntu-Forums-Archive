---
title: "Moving from Xubuntu to Ubuntu"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by soless on 2006-09-16
I'd like to move from using Xubuntu to Ubuntu.  How do I go about doing that?  Do I just reformat my drives and do an install from the live CD, or is there a better way to go about it?

Please keep in mind that I've had no experence with linux beyond this past week.

Thanks in advance.

Oh, I should mention that I'm dual booting to Windowos XP...

---

### Post by bodhi.zazen on 2006-09-16
Even easier.

In a terminal:
```
sudo aptitude install ubuntu-desktop
```

When you log-in you will have the choice of Gnome or XFCE.

Both of these are window managers. Under the hood (window managers) the OS is identical.

---

### Post by Iarwain ben-adar on 2006-09-16
Hi,
it's as easy as counting to 1,2,3

```
sudo aptitude install ubuntu-desktop
```

This will install the Gnome desktop (the standard Ubuntu desktop)

Just log out, and change your session type ;)

Btw, welcome to the forums!

Iarwain

---

### Post by shoot2kill on 2006-09-16
dont forget to UPDATE

```

sudo aptitude update
sudo aptitude install ubuntu-desktop

```

---

### Post by mixmaster on 2006-09-16
I think installing the gnome-desktop package will give you an gnome desktop as default but leave all the KDE stuff in place, and allow you to boot KDE from the session menu.  Thats fine but it can leave a lot of apps laying around that you don't want/need.  I don't know of a simple way of getting rid of them all.

Personally unless you have a lot of stuff you are unwilling to mess with, I think I would reinstall.  It is so simple and you will start from a known base.

---

### Post by xpod on 2006-09-16
aint kde Kubunto`s ......xfce??

---

### Post by soless on 2006-09-17
Thanks, everyone, for the friendly and speedy help.  I look forward to joining the community, learning Linux, and leveling up my geek status.  ^_^

---

### Post by alienexplorers on 2006-09-17
To make sure you have a clean install of ubuntu follow the directions on this page:
[URL="http://www.psychocats.net/ubuntu/puregnome.php"]

---

### Post by soless on 2006-09-18
Will this work even if I've already installed the GNOME gui?

> **alienexplorers said:**
> To make sure you have a clean install of ubuntu follow the directions on this page:
[URL="http://www.psychocats.net/ubuntu/puregnome.php"]

---


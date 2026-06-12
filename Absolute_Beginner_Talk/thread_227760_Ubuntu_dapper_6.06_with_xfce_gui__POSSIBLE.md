---
title: "Ubuntu dapper 6.06 with xfce gui?  POSSIBLE???"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by Mangledbmx on 2006-08-02
is it possible to install ubuntu dapper 6.06 and then uninstall the gnome desktop and install the xubuntu desktop? and if so would that make a big change in overall performance?

---

### Post by GreenHawkIA on 2006-08-02
Yes,all that is possible.  Yes, there is a performance difference.  However, the difference will not be as great if you are using a modern machine as if you are using older hardware.  However, if you want to use Xubuntu, and not gnome at all, it is easier to download & install a Xubuntu CD from the start, and not do Ubuntu or Gnome at all.  See this site to download:
[http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/](http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/)

---

### Post by GreenHawkIA on 2006-08-02
To do what you wanted, install the normal Ubuntu.  Then ```
sudo apt-get install xubuntu-desktop
```  Reboot and at the GDM choose XFCE for your Session.  Then ```
sudo apt-get remove ubuntu-desktop
```.  I've never done it, but that might work for you.

---

### Post by moma on 2006-08-02
Keep the gnome-desktop and 
$ sudo apt-get update 
$ sudo apt-get install xubuntu-desktop

Return to the login-screen (press CNTR + ALT + BACKSPACE) and choose XFCE from the [Options], Select session... menu.

ps. I suppose you have set package repositories like this
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories")

---

### Post by Mangledbmx on 2006-08-02
my reasoning for asking such a question is because i love the instant connectivity of ubuntu dapper and the speed of xubuntu dapper. so i was hoping for a bit of both. basically ubuntu runs a bit slow on my laptop and im having tons of problems getting xubuntu to connect to my home network. yes yes you will say "SAMBA" but i attempted and still no luck.... im obviously doing something wrong but i was looking for an easy fix i guess haha!

---

### Post by Lord Illidan on 2006-08-02
If you want a fast XFCE desktop, consider Zenwalk..

---

### Post by verbatim210 on 2006-08-02
where are all these warcraft ubuntians coming from?

---

### Post by Mangledbmx on 2006-08-02
nice spam there buddy!   anyway, has anyone done this before? just curious if its even worth trying! frankly im just curious if its worth my time to reinstall or just hunker down and manually move all my files back and forth between computers

---

### Post by Socratez on 2006-08-02
Has Anybody attempted these steps?

1. sudo apt-get update
2. sudo apt-get install xubuntu-desktop
3. sudo apt-get remove ubuntu-desktop
4. sudo reboot or sudo init 6


I am going to do it today to see what is up. I have a Book PC II with 900MHz Celeron with 256MB of Ram with some i810 graphics. Not a screamer so i want to give Xface a try to boost the speed. Any other suggestions for a noticable boost in usage speed?

Soc

P.S - I just did a dist upgrade the other day ... I will be impressed if I can go from Breezy to Dapper and then from Gnome to XFCE on the same base install from so long ago no system format and restore ... here is hoping all is smooth

---

### Post by Lord Illidan on 2006-08-02
I am not so sure you can remove ubuntu-desktop and preserve 100% functionality.

---

### Post by Mangledbmx on 2006-08-02
well i think i may try anyway, i just installed this xubuntu this morning so its not like im gonna be losing anything sooooo... ill install dapper 6.06 and then switch out the desktop to xubuntu

ill tell you how it goes

---

### Post by clarkth on 2006-08-02
> **Lord Illidan said:**
> If you want a fast XFCE desktop, consider Zenwalk..

I use Zenwalk on a PII computer, works great.

---

### Post by dolby on 2006-08-02
check [this](http://psychocats.net/ubuntu/purexfce.php)
& also [this](http://www.ubuntuforums.org/showthread.php?t=227781&highlight=xfce)
i dont have any personal experience but it might work

---

### Post by carlosqueso on 2006-08-02
Unless you're really hurting for hard drive space....just ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```  You'll be able to quickly find out which GNOME components that you like, and so have them start at the beginning of your session (I still use gnome-cups-manager to run my printer because it's easier).  I guess once you find out the GNOME components that you need, you could then remove the rest, but it's probably not the best idea.

---

### Post by dolby on 2006-08-02
> **carlosqueso said:**
> ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

in situations like this its better to use aptitude in order to be able to remove the packages ith all their dependencies easily later

---


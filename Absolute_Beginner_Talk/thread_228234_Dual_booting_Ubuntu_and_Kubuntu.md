---
title: "Dual booting Ubuntu and Kubuntu"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by bh351 on 2006-08-02
I have been running ubuntu for about 3 months but now i would also like to try out kubuntu. Is it possible to dual boot the two.

---

### Post by rattlerviper on 2006-08-03
> **bh351 said:**
> I have been running ubuntu for about 3 months but now i would also like to try out kubuntu. Is it possible to dual boot the two.

Yes, it is possible to dualboot Ubuntu and Kubuntu but there is no need to!
Just type this into the terminal.

Sudo aptitude install kubuntu-desktop 

you will be given a choice when the install is almost finished for the default desktop GDM or KDM  choose kdm if you think you will use Gnome more often.  After everything finishes installing log out, and in the bottom left corner of the login screen(splash screen) change the session to KDM and login .  welcome to Kubuntu!  You will still have access to all your gnome files as well. Also since you installed via aptitude if you decide you no longer want Kubuntu you can just type

sudo aptitude remove kubuntu-desktop

here's a link to better instructions than mine(it's where I learned it)
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)[http://www.psychocats.net/ubuntu/kde.html]("http://www.psychocats.net/ubuntu/kde.html")

---


---
title: "Installing GNOME on Server"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by spit334 on 2006-11-26
Im looking to set up a simple FTP server on an old PC while learning this new operating system.

I have put it on the machine and I understand that that it uses the command line by default. The command line is very foreign for me so I would like to install a visual interface.

Could someone instruct me on how to install GNOME on my machine and get it to work. thanks!

*I am using 6.06 LTS

---

### Post by madmetal on 2006-11-26
some specs of the computer? if its old maybe you have to install xfce instead of gnome..

---

### Post by taurus on 2006-11-26
```
sudo aptitude update
sudo aptitude install ubuntu-desktop  <-- for Gnome
sudo aptitude install xubuntu-desktop  <-- for XFce4
sudo /etc/init.d/gdm start
```

---

### Post by spit334 on 2006-11-26
I believe its about 400 mhz with 128 RAM or something of the sort.

instructions on xfce installation would be great too

---

### Post by spit334 on 2006-11-26
Thanks!

---

### Post by taurus on 2006-11-26
Otherwise, you can install Xubuntu directly...

[http://www.xubuntu.org](http://www.xubuntu.org)

---


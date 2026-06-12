---
title: "[SOLVED] Uninstalled old Kernels, now I see blank screen"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by altonbr on 2006-09-27
I was reading some threads as to why my Ubuntu install is taking up 9GB. One of the reasons was old kernels that I don't use anymore. So, thinking it'd be smart to remove anything I don't use, I removed all the kernels except 2.6.15-27.

Everything boots up as normal and I enter in my username and password at the login screen.. but then it goes to a blank, orange/brown screen.

I can still run SSH, gnome-screenshot and gnome-system-monitor (by click CTRl + ALT + DEL).. but it seems to be having problems with x-window-manager? or X in general.

Screenshots are attached.. any advice is appreciated.

---

### Post by altonbr on 2006-09-27
I hit Ctrl + Alt + F1 and ran
```

sudo dpkg-reconfigure xserver-xorg

```
rebooted... and it didn't help.

Am I using the wrong kernel?

```
uname -r
```

gives me 2.6.15-27-386

---

### Post by altonbr on 2006-09-27
I have a feeling this doesn't have to do with my kernel though... else I wouldn't be able to boot correct?

My LiveCD's work by the way... so it's got to be a configuration file of some sort.

---

### Post by altonbr on 2006-09-27
So all four posts are by me.. but my friend found a fix:

```
sudo apt-get remove nautilus && sudo apt-get install nautilus
sudo killall gdm
sudo gdm
```

and done.

---


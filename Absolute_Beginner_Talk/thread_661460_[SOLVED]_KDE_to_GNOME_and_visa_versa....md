---
title: "[SOLVED] KDE to GNOME and visa versa..."
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by cartisdm on 2008-01-07
I installed Gusty on my roommate's desktop yesterday (I got us another Linux user!) and I decided to make a profile on his computer too.  I use a very customized version of GNOME on my laptop so I wanna give KDE a shot.

I have him setup using GNOME and when I log in KDE I can switch fairly easily to his user (however, I do errors quite often because things like Trash wont load) but I can't switch from GNOME to my KDE because I don't have GDM (GNOME display manager).  I looked all in  Synaptic and Add/Remove but I don't see it.  It's possible I overlooked it but it's just as easy to ask for help:)

---

### Post by p_quarles on 2008-01-07
It's simple to install:
```
sudo apt-get install gdm
```
During the installation, you'll be asked whether you want kdm or gdm to be the default. If you ever need to change the default later:
```
sudo dpkg-reconfigure gdm
```
and it will ask you again. ;)

---

### Post by cartisdm on 2008-01-08
it said it's already installed and doesn't need to be updated either.

I'm getting this following error within GNOME during switching to KDE:
> GDM (GNOME DISPLAY MANAGER) is not running

You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm. If you wish to use this feature, then your system will need to be configured to use GDM instead. 

---

### Post by p_quarles on 2008-01-08
Hmm. Can you post the output of the following two commands?:
```
ps aux | grep kdm
```
and
```
ps aux | grep gdm
```

---

### Post by cartisdm on 2008-01-08
kdm:
> root      5038  0.0  0.0   2944   688 ?        Ss   Jan07   0:00 /usr/bin/kdm -config /var/run/kdm/kdmrc
jeremy   10013  0.0  0.0   2980   776 pts/1    R+   00:30   0:00 grep kdm


gdm:
> jeremy   10017  0.0  0.0   2976   752 pts/1    R+   00:32   0:00 grep gdm


---

### Post by p_quarles on 2008-01-08
Okay, that output means that gdm is not currently running (it shows up in the "ps" output, though, because the grep command was looking for it). This should allow you to activate it:
```
sudo dpkg-reconfigure gdm
```

---

### Post by cartisdm on 2008-01-08
That did the trick, thanks man

I haven't had the crashing problem recently so hopefully that's fixed too but if not I'll be in here posting shortly:)

---


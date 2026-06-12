---
title: "No GUI"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by mzakharo on 2008-02-01
Hi, I Have Ubuntu 7.10, I call myself an absolute noob in linux so bare with me please. Here is what I have done: Installed KDE 4.0 from the terminal  using these [instructions]("http://www.ubuntugeek.com/howto-install-kde-40-stable-in-ubuntu-gutsy.html"). During the installation, the terminal turned scarry blue and when promoted to choose a default (i believe login manager, or i cannot remember, I did not spend too long on that screen), the two choiced came up, i believe one of them was either deb, or gnom, and the other was kde-4 - well, i scrolled down and selected kde-4. After thre installation, i have rebooted and noticed crazy effects happening. First of all, my default login screen was gone and replaced by something blue and unfriendly. I did not like kde-4, so i loged in with a gnome session and was unpleasantly surprized that shutdown/restart buttons have disappeared from the logoff menu, and most of all, i could not locate login manager, so out of desperation, i removed the kde-4 using this command : sudo aptitude remove kdelibs5 kde4base-data kde4libs-data. then after reboot everything was GONE. no GUI at all, just a big black terminal screen, i was able to login, but all the GUI has disappeared and I do not know how to revert everything back to normal. PLEASE help, I have no idea what to do, and I want my gnome desktop back!:confused:

---

### Post by LowSky on 2008-02-01
from the screeen prompt type ```
start x
```

that should get you into gnome 

if not type

```
sudo aptitude install ubuntu-desktop
```

---

### Post by mzakharo on 2008-02-01
> **LowSky said:**
> from the screeen prompt type ```
start x
```

that should get you into gnome 

if not type

```
sudo aptitude install ubuntu-desktop
```

how do i make it start automatically like it used to before?

---

### Post by LowSky on 2008-02-01
ubuntu-destop should reinstall gnome properly, and it should revert back to the way it should be.

---

### Post by mzakharo on 2008-02-01
ok, I have tried both lines and firs one said that the command is unknown, second said that my ubuntu-desktop is installed and up to date. I believe that I havent deleted it during the installation of kde-4, and I do not want to reinstall it, I have it customized the way I like it, Is there any other way of getting my GUI back?

---

### Post by ~LoKe on 2008-02-01
That should have been:
```
startx
```
But what you should be doing is...
```
sudo /etc/init.d/gdm restart
```
Or simply...
```
sudo gdm
```

---

### Post by mzakharo on 2008-02-01
Thank you Loke - it worked, kida. Here is what I did. I typed the first command you posted and here is the error message it displayed:
*stopping GNOME Display Manager..
* Not starting GNOME display Manager (gdm); it is not the default display manager

Out of desperation, I typed the second command you told me to try ( sudo gdm) - and it worked! - everything was back to normlal. So i rebooted and it was broken again. My question here I guess would be how to make GNOME the default display manager?

---

### Post by ~LoKe on 2008-02-01
I didn't read the whole post, so I assumed you used GDM.  If you use KDM, you can do the same...
```
sudo /etc/init.d/kdm restart
```
```
sudo kdm
```

I think it's called KDM.

---

### Post by jan quark on 2008-02-01
during login there are sessions options 
select gnome session and make default when asked

---

### Post by mzakharo on 2008-02-01
sory Loke, you misunderstood me. I have removed KDM - it is gone for good, I want only GNOME - and I want it to be default, and it is not, so could someone help me make it default at startup?

---

### Post by mzakharo on 2008-02-01
> **jan quark said:**
> during login there are sessions options 
select gnome session and make default when asked

I do not have sessions options because my user logis in automatically. I forgot how I achieved that - my second question would be, how do I disable automatic login?

---

### Post by mzakharo on 2008-02-01
Ok, firs of all, System >adminsitration > Login Screen Setup option is gone - what happened to it? second of all, The system does not promote to make GNOME the default display manager when I select it, so no contact there either, please help!

---

### Post by mzakharo on 2008-02-01
I Kinda fixed everything myself here - here is what made everything work:

sudo dpkg-reconfigure gdm

Thanks for your help, keep up the good work!

---


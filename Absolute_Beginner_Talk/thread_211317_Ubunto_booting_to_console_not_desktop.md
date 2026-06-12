---
title: "Ubunto booting to console not desktop?"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by Karti on 2006-07-08
Hi,

I installed the alternative desktop cd install. It works fine but as it was a text install I now boot to console and have to logon and "startx" to get to the graphical desktop interface. 

I would like it to boot to grapical interface so users can log on and change their session to either kdm or gnome. I just wondered if there was a file that I could amend to get it to boot into graphic login mode.

Any help would be appreciated and welcome

Cheers

K
;)

---

### Post by Rui Pais on 2006-07-08
hi,
you must have gdm or kdm installed.

The install process should automatically config things to the graphical session manager start at end of boot process.

---

### Post by Karti on 2006-07-08
I am sitting here working the desktop fine. After I have started "startx" it is great. But if I log off it goes straight to console again. This is my only problem. I just need to be able to have the grahic option to log on. I wondered if it was in the conf files that I could amend it. 

I did have to do the alternate install which I believe starts in console

K
;)

---

### Post by Rui Pais on 2006-07-08
Yes, but which one do you have kdm or gdm?

---

### Post by Karti on 2006-07-08
It defaults to Gnome when I startx

K
;)

---

### Post by Rui Pais on 2006-07-08
Hi, 
try to do on terminal:
```
sudo apt-get install gdm
```
and then logout. 

If the graphical session manager dont start do:
```
sudo /etc/init.d/gdm restart
``` 
that should do the trick.

---

### Post by infoseeker on 2006-07-08
Install gdm (gnome desktop manager)
> sudo aptitude install gdm

EDIT   oops dual post :D

---


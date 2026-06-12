---
title: "Help!, My screen won't work!"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by uberzorz on 2006-12-10
Hi, I installed the OEM version of Ubuntu (latest) on my computer and have some trouble, I recently installed my new monitor (trashed the old one) and it says xserver is not configured!, so I configure it and it only lists really old display  driver! (mine is a new intel: 915GV - 128mb). I tried many of them yet they all come up with errors!, How do I setup my display driver???? (from recovery mode...) 

:confused:  :confused: ](*,) ](*,)

---

### Post by taurus on 2006-12-10
```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by uberzorz on 2006-12-10
I just tried that and it just said that there were errors and xorg was not installed
any other suggestions? (monitor specs: 1152x864 @60hz - 32bit)

---

### Post by taurus on 2006-12-10
```
aptitude update
aptitude install xserver-xorg
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by uberzorz on 2006-12-10
Thx!, But now I have installed it but gnome dosnt work at all... the task bar is ALWAYS frozen and blank even in failsafe mode ](*,) ](*,) ](*,) ....

How can I install KDE???? (I'm using my XP computer right now)

---

### Post by taurus on 2006-12-10
Boot into recovery mode from GRUB menu and at the prompt, do

```
aptitude update
aptitude install kubuntu-desktop
```
Reboot and pick KDE from the Sessions, bottom left corner...

```
shutdown -r now
```

---


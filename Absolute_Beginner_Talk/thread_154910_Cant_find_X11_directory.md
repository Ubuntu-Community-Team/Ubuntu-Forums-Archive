---
title: "Cant find X11 directory"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by purepest on 2006-04-04
Hi

Totally new to linux nevermind ubuntu

I have installed the OS on virtual PC and I am now having graphical issues. On the install I tried to setup 1024x768 but at the login screen its a bit odd to say the least.

I have read through [http://ubuntuforums.org/showthread.php?t=124543&page=2&highlight=change+resolution+recovery+mode](http://ubuntuforums.org/showthread.php?t=124543&page=2&highlight=change+resolution+recovery+mode) which looks like the solution to my problem, but, when I go into recovery mode I type in 'cd /etc' which looks as though it changes it to the etc directory. When I try to change to X11 directory to try and edit the conf file it says that the directory doesnt exist.

Can anyone plz help?

---

### Post by trent dillman on 2006-04-04
edit:oops, didn't read...did you install X?

try

```
sudo apt-get install xserver-xorg
```

---

### Post by purepest on 2006-04-04
doh!

got it ta

---

### Post by dermotti on 2006-04-04
do** cd /etc/X11**  (notice the caps on X11, linux is case sensitive)

---


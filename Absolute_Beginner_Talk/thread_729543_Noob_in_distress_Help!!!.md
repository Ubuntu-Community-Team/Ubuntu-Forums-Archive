---
title: "Noob in distress Help!!!"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by vergil66 on 2008-03-20
Okay, Just installed fiesty fawn on my laptop with vista preinstalled
I wanted to get a bigger resolution, so I went to restricted drivers and downloaded the nvidia driver for ubuntu.
After I restarted, he will stay on a black screen.
WHAT THE HELL DO I DO TO SOLVE THIS?
sorry for the caps.

---

### Post by NightwishFan on 2008-03-20
If you use the recovery mode can you get a bash shell? (command line)

---

### Post by vergil66 on 2008-03-20
alright ok
Im there
it says root@vergil6-laptop:~#

---

### Post by NightwishFan on 2008-03-20
I am not going to tell you to do anything I have not done myself so lets try to at least start x. Log in as your user and type:
```
startx
```
If you just get the black screen again I think you would have to reconfigure the config file. We will get to that when we get to it if it comes to that.

---

### Post by vergil66 on 2008-03-20
ok i did the startx command 
and it is still a black screen

---

### Post by NightwishFan on 2008-03-20
Ok. Give me a minute. I have never done the reconfigure as I have never needed to.

---

### Post by vergil66 on 2008-03-20
Alright

---

### Post by NightwishFan on 2008-03-20
Run this command. I believe it will get you to a dialog to answer some questions to configure your display.
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by vergil66 on 2008-03-20
alright, it says package configuration
now i hafta select the x server driver

---

### Post by NightwishFan on 2008-03-20
I am not sure what to do from here like I said. If you can try vesa as it is a safe option. I think that will get you to a desktop. Mainly use the default options I would assume, unless you know the answer.

---

### Post by vergil66 on 2008-03-20
holy **** u are awesome
I bow down to you thx

---

### Post by NightwishFan on 2008-03-20
I am glad I could help. I do not want to get in over my head too much. Although a Linux is normally as easy to fix as it is to break.

---


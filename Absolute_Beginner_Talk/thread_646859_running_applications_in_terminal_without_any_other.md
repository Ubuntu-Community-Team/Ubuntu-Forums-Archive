---
title: "running applications in terminal without any other messages"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-12-21
I was just wondering how do you run an application from the terminal without running any of the things that the terminal monitors. like for example if you start an internet connection the terminal will display everything that is going on while connecting. how, for all applications, do you stop this from happening?

thanks

---

### Post by RomeReactor on 2007-12-21
Hi. I'm not sure this is what you want, but if you mean starting an application and then let it run in the background, so you can continue using the terminal, you can start applications like this (for example, to launch nautilus):
```
nautilus &
```

---

### Post by ssaamon on 2007-12-22
no I mean like if you run a program like wifi-radar, then as it trys to connect to the network it will output stuff to the terminal. I guess one way to do what I want to do is to block the communication between the program and the terminal. but how would I do this?

thanks

---

### Post by RomeReactor on 2007-12-22
Just launch WiFi-Radar from the menus, not from the terminal (I get the feeling that I'm not completely understanding your issue...)

---

### Post by Whiffle on 2007-12-22
wifi-radar > /dev/null

---

### Post by akiratheoni on 2007-12-22
Maybe using Alt+F2 and use the dialog box instead? I'm not entirely sure what you mean, either.

---

### Post by ssaamon on 2007-12-25
thanks whiffle

---


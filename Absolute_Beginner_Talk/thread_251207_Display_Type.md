---
title: "Display Type"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by debasishg on 2006-09-05
Hi to all

I have installed Ubuntu LAMP server. but when i booted up my PC, its running on console mode. now i want to enable GUI mode. how do i do this.. please help.

---

### Post by n00b@linux on 2006-09-05
I'm a n00b at linux and I've never set up a LAMP, but I do know that the following command in the console starts the X server:
```
 
startx

```
I hope it helps.:)

---

### Post by debasishg on 2006-09-10
Not working. i have tried with several times

---

### Post by Najand on 2006-09-10
> **debasishg said:**
> Not working. i have tried with several times

It is because there is no X packages included in UBUNTU Server Installation. I think you can install other applications included in UBUNTU Desktop using the command:
```
sudo apt-get install ubuntu-desktop
```
without deleting your new installed server.

---

### Post by debasishg on 2006-09-18
Thank you

---

### Post by Brunellus on 2006-09-18
> **debasishg said:**
> Hi to all

I have installed Ubuntu LAMP server. but when i booted up my PC, its running on console mode. now i want to enable GUI mode. how do i do this.. please help.
Linux server installs seldom include GUIs by default, by the way, because the assumption is that server administration will take place remotely, over ssh. 

As has otherwise been suggested, simply installing the ubuntu-desktop package will give you a "regular" Ubuntu box.

---


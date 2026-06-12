---
title: "Need help with gDesklets"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by lanmonkey on 2006-06-17
I am totally new to linux, and this is really my first time trying to do anything with it. i was trying to set up a LAMP server, but i got sidetracked by gDesklets. I read in their forum that all you had to run was apt-get install gdesklets, but every time i try that, it tells me it doesnt exist/cant find it. I am logged in as root and everything, and it wont do it. after that, i found the application, and installed it myself, like, i downloaded it, extracted it, then did "./configure". that told me i needed to update python, so i got everything for python. after that, i did it again, and everything worked. then i did "make" then "make install". it said it installed, and it is there under applications->accessories, but when i click on it, it says starting, then it quits. so i tried logging in as root and running it, and the same thing happened. so i did a whole bunch of research, and found to run the get it through "apt-get" i had to add repositories, so i added the ones the thing told me, but it still says it cant find it. i added these repositories through synaptics package manager, and had it check them and stuff, i dont know if that matters. i just want these things to run. 
on other forums, they want specs so they can help you, so here are mine:
800 mhz PIII
512 mb ram
13 gig HD
Ubuntu 6.06

---

### Post by catlett on 2006-06-17
It is always best to install applications from repositories. If it is in the repositories then it will work with ubuntu. When you compile from source the application created does not always run.

The reason for your error when you apt-getted gdesklets was you didn't have the universe repository enabled. Now that you have the repositories enabled install gdesklets again. It should install no problem

Use aptitude just to make sure any dependency issue from your compliling gets taken care of. So update the cache and then install.```
sudo aptitude update
``` ```
sudo aptitude install  gdesklets
```
If aptitude runs successfully and you still have an issue, try rebooting and see if that sets everything straight.

---

### Post by taurus on 2006-06-18
Also don't forget the
```

sudo aptitude install gdesklets-data

```

---


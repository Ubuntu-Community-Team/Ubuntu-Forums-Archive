---
title: "Problem with Synaptic package Manager"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by icyblue on 2007-07-26
Hello!

I recently installed Ubuntu Feisty fawn. Everything went fine till now but suddenly, when I tried to install Sun java6(Using ADD/REMOVE). An error popped out and after that I can't install any package. Each time when I open Synatic package manager, I get "An error occured" with the following description

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can anyone help me out of this prob?

Thanks!!!

---

### Post by deadgobby on 2007-07-26
Please open up your terminal and copy and paste this 

sudo dpkg --configure -a

Then enter your password. It should be the password you logg into ubie splash screen

Gobby

---

### Post by Seisen on 2007-07-26
Open up the terminal by going to Applications>Accessories>Terminal and put the command they tell you in the error

```
sudo dpkg --configure -a
``` and that should fix your problem.

---


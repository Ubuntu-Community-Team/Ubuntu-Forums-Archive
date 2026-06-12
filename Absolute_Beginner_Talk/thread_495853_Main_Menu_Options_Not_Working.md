---
title: "Main Menu Options Not Working"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by HaloZero00 on 2007-07-08
Ok, I went under System, Applications and main menu.

I try to put some applications on the main menu such as Systems Tools, but whenever I check them, they jsut uncheck, it happens with Add/Remove Programs, and a few things in System as well including the Restricted Drivers Manager. 

The update manager also fails to update everything. I didn't write down the error message at the time but it had something to do with not enough adminstration access. I'm using the default account made by Ubuntu after installation. 

Any help would be appreciated.

---

### Post by overdrank on 2007-07-08
> **HaloZero00 said:**
> Ok, I went under System, Applications and main menu.

I try to put some applications on the main menu such as Systems Tools, but whenever I check them, they jsut uncheck, it happens with Add/Remove Programs, and a few things in System as well including the Restricted Drivers Manager. 

The update manager also fails to update everything. I didn't write down the error message at the time but it had something to do with not enough adminstration access. I'm using the default account made by Ubuntu after installation. 

Any help would be appreciated.

Hi and welcome could you try this command in the terminal located under applications, accessories, terminal
```
sudo apt-get update
```
And post any errors given

---

### Post by HaloZero00 on 2007-07-08
Had to type in password and then nothing.

---

### Post by overdrank on 2007-07-08
> **HaloZero00 said:**
> Had to type in password and then nothing.

Ok very strange, Is this a fresh install? Which version of ubuntu are you using and are you able to connect to the web?

---

### Post by HaloZero00 on 2007-07-08
This is version 7.04. The installation first required making a new partition (I'm dual booting XP and Ubuntu right now). 

And yes I'm on the web using Ubuntu.

---

### Post by overdrank on 2007-07-08
> **HaloZero00 said:**
> This is version 7.04. The installation first required making a new partition (I'm dual booting XP and Ubuntu right now). 

And yes I'm on the web using Ubuntu.

Ok would you mine trying this, using the keys at the same time ctrl,alt,backspace this will restart X and then login again. Then go to the terminal again with that same command.

---

### Post by HaloZero00 on 2007-07-08
Tried, same thing.

---

### Post by HaloZero00 on 2007-07-09
I'm just gonna assume my install got screwed up and have to format my drive again and reinstall Ubuntu.......

---

### Post by Kono on 2007-07-10
Weird, I got the same problem, yet I don't even see an error message. The boxes just uncheck themselves after about 1 second.

I tried "sudo apt-get update"--apparently with success, it updated something, but the problem still remains. If you find out what the problem is, please let me know. :)

---


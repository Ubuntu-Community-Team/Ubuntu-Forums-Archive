---
title: "Xlib: connection to &quot;:0.0&quot; refused by server"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by anniya0n on 2007-04-01
root@sudhakar-desktop:/home/sudhakar# gedit /etc/apt/sources.list
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.

How to solve this problem???

plz help

---

### Post by Perfect Storm on 2007-04-01
Use:
```
sudo nano /etc/apt/sources.list
```
Instead of activating the the root.

---

### Post by anniya0n on 2007-04-01
yes nano is working but if i give vlc or firefox or anything it shows the same problem.

My login preference window is not getting opened..

I think this problem affects login preference window also

---

### Post by Perfect Storm on 2007-04-01
What have you messed with lately? Have you made any changes on Ubuntu's behaviour versus the default setup for ubuntu?

---

### Post by anniya0n on 2007-04-01
I dont know..

While installing ubuntu i had only resolution in about 640*77 something like that..

That is only option i had..

so i used reconfigue/xorg.conf

after that i got normal resolution

Is that the problem

---

### Post by Perfect Storm on 2007-04-01
Shouldn't be. Which version of Ubuntu do you use? Have you activated the root account which can cause the trouble? Is it a clean install or an update from previous ubuntu version?

---


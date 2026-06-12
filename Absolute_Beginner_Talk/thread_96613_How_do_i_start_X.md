---
title: "How do i start X?"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by bete on 2005-11-29
Uhm after doing a standard install for ubuntu x doesnt auto start..

How do i start X manually? Or install...

---

### Post by odin on 2005-11-29
Do you have gdm installed?

I dont know what the problem might be but as far as I remember If when you boot you do ti in text mode just typing gdm should start the x.

---

### Post by bete on 2005-11-29
When i do that i get :
Command not found
:(

---

### Post by Ulokye on 2005-11-29
sudo apt-get install gdm

---

### Post by atoponce on 2005-11-29
[quote=bete]Uhm after doing a standard install for ubuntu x doesnt auto start..

How do i start X manually? Or install...[/quote] 
Sounds like you might either have a driver not working correctly, or the Gnome desktop manager isn't isntalled.  Try running:

```
[SIZE=-1]sudo dpkg-reconfigure xserver-xorg[/SIZE]
```[SIZE=-1]

Run through the screen prompts, and when finished, you should be able to run X. That is, if you are having a driver issue. If you haven't installed the GDM, run at the terminal:

```
sudo apt-get isntall ubuntu-desktop
``` 

Good luck!
[/SIZE]

---

### Post by Brunellus on 2005-11-29
"standard install?"

On a standard install, X should start up and get you to a GDM login screen.  If you're not seeing X, you have probably chosen a "server" install by accident, whereupon you must 

```
$ sudo apt-get install ubuntu-desktop
```

to get you all the GUI desktop goodies.

---


---
title: "Help please, most of screen is black"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by CougarisAlsar on 2007-04-20
Oh goodness gracious, big problem, i installed Ubuntu fine and indeed it has been working phenomonally, untill a couple minutes ago when i booted up my computer. 

Now only the top left corner of my screen is visible workspace. But it seems to be registering all the other space, just not showing it to me because my mouse shows up on the black, and i can make a highlight box on my desktop that starts in the black and shows up on the top left corner when i drag it. Oh help me fix this please.
it looks like this
[IMG]http://img231.imageshack.us/img231/5909/screenshotxz3.png[/IMG]

and that black portion is where the rest of my desktop should be please help, i really wanted to join the Ubuntu community

---

### Post by Kobalt on 2007-04-20
Did you install any graphic card drivers ?

---

### Post by CougarisAlsar on 2007-04-20
only driver i installed was the one that desktop effects made you install to do it, and i had restarted multiple times after i installed that with no problem

---

### Post by Kobalt on 2007-04-20
Which graphic card do you have ?

---

### Post by CougarisAlsar on 2007-04-20
nvidia geforce 7600

---

### Post by Kobalt on 2007-04-20
All right then,

press Ctrl+Alt+F1 to access a command line, log in, then enter the following command line (write it down and read the rest now, you'll leave graphical session from this point on) : 
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions you're asked and when it gets to the point of asking you graphic card driver select "nvidia". For other options, if you don't know pick the default choice. Restart, and hopefully you have a normal screen back.

---


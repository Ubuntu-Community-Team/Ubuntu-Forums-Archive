---
title: "How to reinstall Feisty?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-04-24
I just upgraded to Feisty but I am having problems with it. How can I re-install Feisty from within Feisty? My CD-ROM is broken.

---

### Post by aktiwers on 2007-04-24
What kind of problems are you having?

---

### Post by syalam on 2007-04-24
See this thread:

[http://ubuntuforums.org/showthread.php?t=421546&goto=newpost]("http://ubuntuforums.org/showthread.php?t=421546&goto=newpost")

---

### Post by aktiwers on 2007-04-24
Have you tried the simple:
```
startx
``` 
??
If that doesnt work,try running a:
```
sudo dpkg-reconfigure xserver-xorg
```

and the startx afterwords...

---

### Post by syalam on 2007-04-24
tried both no good =(

---

### Post by aktiwers on 2007-04-24
Sorry man.. then I dont know.
Maybe you could try uninstall Gnome and install it again?

Use the remove command here:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
I think you have to go for the long one :S
But you could try the short one first..

And then:
```
sudo aptitude install ubuntu-desktop
```I have no idea if this will work, but thats what I would try.
Let me know how it went.

---

### Post by syalam on 2007-04-24
ive tried this one also ... didnt work =(

---

### Post by aktiwers on 2007-04-24
Sorry for wasting your time.. then I dont know.
I dont think its easy to install it without a CD. Only if you have a usb drive or something?

Lets see if someone else got any ideas

---


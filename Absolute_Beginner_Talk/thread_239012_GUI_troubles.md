---
title: "GUI troubles"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by gwendes on 2006-08-18
I've been running my LAMP webserver from an old machine. 

I've just upgraded the computer just swapping over the hard drive. Ubuntu nearly loads then there is a GUI error and it goes to the prompt. What is the quickest, messiest resolution?

---

### Post by ciscosurfer on 2006-08-18
Perhaps I'm reading your post wrong, but, why do you want to run a GUI on a server?

---

### Post by gwendes on 2006-08-18
I'm new to it and having a pretty GUI makes it easier to digest when I'm sitting at that PC.

---

### Post by ciscosurfer on 2006-08-18
Ok.  I understand.  Install "ubuntu-desktop"...just copy/paste the following in a terminal, download the appropriate files given and then reboot your box...```
sudo aptitude update && sudo aptitude install ubuntu-desktop
```

---

### Post by gwendes on 2006-08-18
It won't install because it is already there. Can I repair in anyway?

---

### Post by muep on 2006-08-18
sudo dpkg-reconfigure xserver-xorg

When you are done with that, try:

sudo /etc/init.d/gdm restart

If this doesn't work, try the dpkg-reconfigure thing again.

---

### Post by ciscosurfer on 2006-08-18
> **muep said:**
> sudo dpkg-reconfigure xserver-xorg

When you are done with that, try:

sudo /etc/init.d/gdm restart

If this doesn't work, try the dpkg-reconfigure thing again.

Agreed.

---

### Post by gwendes on 2006-08-18
Linux community is awesome. Thanks guys :)

---


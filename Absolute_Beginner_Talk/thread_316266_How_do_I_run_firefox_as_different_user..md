---
title: "How do I run firefox as different user."
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by thelocust on 2006-12-10
**[SIZE="2"]How do I make a script in KDE to run fire fox as a different user.[/SIZE]**

---

### Post by aysiu on 2006-12-10
```
firefox --profilemanager
```

---

### Post by thelocust on 2006-12-10
**[SIZE="2"]All that does is bring up firefox as the current user. What I am going for here is 2 diffrent firefox setups one for school and one for play.[/SIZE]**

---

### Post by aysiu on 2006-12-10
> **thelocust said:**
> **[SIZE="2"]All that does is bring up firefox as the current user. What I am going for here is 2 diffrent firefox setups one for school and one for play.[/SIZE]**
No.

That allows you to create a new profile.

There is one profile that's the Default Profile. You can then add a new profile called "Play" or "School."

---

### Post by gaten on 2007-12-11
I'm actually interested in running ff as a completely different user for security purposes. All of my attempts to do this have ended in failure, mostly due to Xhost authentication problems. 

In short, I've created a user "ff" with a home directory of /home/ff, and issued  the command:

```
sudo -u ff -s /usr/bin/firefox
``` 
and receive this in return:
```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firefox-bin:22280): Gtk-WARNING **: cannot open display: 
```

Which I believe has something to do w/ X authentication, but I have no idea how to get around it. Any ideas?

---


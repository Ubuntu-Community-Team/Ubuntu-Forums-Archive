---
title: "I've done something stupid - No GUI"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by bparham on 2007-03-03
Ok, brief background. I have the Ubuntu and Kubuntu desktop on my system and lately I've been using Kubuntu exclusively, 

I was in Boot Manager and turned off the Ubuntu desktop now I can only get into the system through the command line. Any time I try to run a program through the command line I'm told that the display isn't set-up properly. 

At this point, I'm not sure where to begin. My first though was to run Boot Manager through the command line and reset the system, however that doesn't seem to be a possibility. Any other suggestions?

---

### Post by taurus on 2007-03-03
What happens if you run this command at a prompt to start X?

```
startx
```

---

### Post by bparham on 2007-03-03
That enabled me to log back in and correct the problem. Thanks!

Out of curiosity, is there a command to log into Kubuntu from the command line?

---

### Post by taurus on 2007-03-03
Before you run startx, try

```
sudo /etc/init.d/kdm start
```
That should fire up the KDE login screen.

---


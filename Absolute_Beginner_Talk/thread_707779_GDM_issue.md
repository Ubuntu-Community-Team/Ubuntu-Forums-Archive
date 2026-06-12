---
title: "GDM issue"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by phili_fan on 2008-02-25
well don't tell me i have driver issues b/c i just finally got this thing to display something. Well basically gdm does not start at boot up i used to have beryl but i got rid of it because my graphics card was acting up. I now fixed that and now i have to push ctrl alt f1. Then sign in. run this 

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

this turns it off then back on

then i get my desktop.

How do i get the gdm to run at start up???

---

### Post by rapiscan on 2008-02-26
Check to see if gdm is set to run in the init script links.

```
sudo update-rc.d -n gdm defaults
```

This tells update-rc.d to make links to start and stop the service.  The -n option means "not really" so it's a test run that won't really do anything.  If the start/stop links are already there, you will get:

> System startup links for /etc/init.d/gdm already exist.

EDIT: I just realized that your previous post implies that gdm is in fact already running, but you're still at the command line.  If this is the case, there is likely some sort of error output from when gdm tries to start.

---


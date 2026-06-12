---
title: "Graphical log-in issues"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by dogsouljah on 2006-08-24
Hi there.

i've done a search for this problem but nothing simular seems to be resulting

I'm new to Ubuntu and practically new to Linux too. having installed ubuntu last night, everything went smooth. I could log in to the graphical log-in page with the initial accound I set up last night.
However, when I attempt to log in this morning, I get the message that either my username or password were incorrect.
When I switch to a console, I can log in no problem. I set up a new user account through the console, switched to the graphical log in page and could log in no problem with that.
I havent changed anything as far as setting root accounts or permissions with my main log in, so I am slightly confused.

Any ideas?

---

### Post by dogsouljah on 2006-08-24
So sorry for bmping this, but I've been trying to figure this problem out for most of the day but I am getting no where fast.

Does anyone have any ideas what could be stopping me from logging in?

---

### Post by mssever on 2006-08-24
Here's an idea (assuming you're using Ubuntu, not Kubuntu):


Install KDM and see if KDM works. (If you're already using KDM, switch to GDM--or XDM)
```
sudo aptitude install kdm
```
Be sure to tell the installer that you want to use KDM as the default login manager when it asks. You can manually change this by editing /etc/X11/default-display-manager.

If kdm doesn't start automatically, do this:
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/kdm start
```

If this works, then you problem is with GDM and you can either try to fix GDM or just use KDM.

---


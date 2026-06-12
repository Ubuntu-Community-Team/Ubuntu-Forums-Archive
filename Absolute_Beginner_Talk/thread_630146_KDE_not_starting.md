---
title: "KDE not starting"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-12-03
Kubuntu was working fine for a while, but when I installed a bunch of updates for it and did a restart, KDE wouldn't start.
It starts in terminal (root, just letters) just fine but if I push Alt+F7 than just the prompt sits there blinking

---

### Post by Dapman01 on 2007-12-03
The last thing that comes up before it asks me for my username and passward (in terminal mode) is
kinit: No resume image, doing normal boot...
Than it asks me for my passward and username

---

### Post by jordanmthomas on 2007-12-03
log in to one of those terminals that are there.
```
sudo /etc/rc.d/kdm start
```
what happens if you do this?  Does kdm start or does it crash?

*edit*  don't worry about the kinit message, that seems normal.

---

### Post by Dapman01 on 2007-12-03
Nothing happens, it says
sudo: /etc/rc.d/kdm: command not found

---

### Post by jordanmthomas on 2007-12-03
oh, woops.  Mixing up Arch and Ubuntu
```
sudo /etc/init.d/kdm start
```
Sorry about that.  :blush:

---

### Post by Dapman01 on 2007-12-03
I think that i forgot to mention that I am using kubuntu, will that matter?

---

### Post by jordanmthomas on 2007-12-03
No.

---

### Post by Dapman01 on 2007-12-03
Didn't help the situation
starting K Display Manager: KDM already running
but it's not.  I'm stuck in the terminal

---

### Post by jordanmthomas on 2007-12-03
Do this then:
```
sudo /etc/init.d/kdm stop
sudo /etc/init.d/kdm start
```

---

### Post by GSF1200S on 2007-12-03
I dont know if this is much different, but what happens if you type:

sudo /etc/init.d/kdm restart

What video card do you have? Perhaps you have a driver issue...

**EDIT** Actually, start and stop would accomplish this same thing.. it doesnt return any messages? It seems like it may be an xorg problem and not kdm.

---


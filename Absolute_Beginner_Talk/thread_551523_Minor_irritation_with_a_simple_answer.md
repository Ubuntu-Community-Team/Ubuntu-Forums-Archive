---
title: "Minor irritation with a simple answer?"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by spr6wo on 2007-09-15
Hi All,

Having just set up my old PC and giving up on Windows I have decided to install Ubuntu. I have tried Linux a few times in the past and given up mainly because of hassles with getting connected to the internet.

Anyway, I have just finished installing Ubuntu and have come across a bit of a problem. I'm certain there is a simple answer to resolving it but I just don't know how.
I downloaded the Ubuntu Limewire application and tried to install it, however just prior to this the automatic updater ran and updated my system, during this process I noticed a number of failure notes. So now when I try to install Limewire I get a message saying that only one software management tool is allowed to run at a time. 

It looks to me like the Synaptic Package Manager hasn't closed down properly and I don't know how to do it. When I run Synaptic I get this error message "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." I have tried running this in a terminal window but nothing happens, can anyone help?

Steve

---

### Post by schorsch on 2007-09-15
Try
```
sudo dpkg --configure -a
```

---

### Post by nixclusive on 2007-09-15
try running```
sudo dpkg --configure -a
```in the terminal window.

---

### Post by spr6wo on 2007-09-15
Great! thanks for that, I had completely forgotten about sudo. It looks to be installing well right now.

---


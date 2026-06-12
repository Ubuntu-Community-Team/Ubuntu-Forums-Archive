---
title: "synaptic package manager problems"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by davidwrocklage on 2008-01-30
when I try to open the package manage I recieve the following error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I'm at a loss as how to continue.  This same error occasionally appears when I try to use the add/remove applications.

---

### Post by taurus on 2008-01-30
Close down synaptic or Add/Remove.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by DMK62 on 2008-01-30
The installation of packages / updates either encountered a problem or were not finished.

Try the following

Reboot the computer.

Go to Applications>Accessories>Terminal

In the terminal enter

sudo dpkg --configure -a

Let it run its course. It may take a while depending on how many packages need to be updated.

After that run the following commands in Terminal

sudo apt-get update

sudo apt-get upgrade

sudo apt-get clean

exit out of terminal

Dale

---

### Post by davidwrocklage on 2008-01-30
I guess it told me what to do right in the message (partially at least) I'm doing what you said right now and will get back to you in a few minutes. Worked Fine thank you both very much

---

### Post by DMK62 on 2008-01-30
You're welcome and thank you for letting me know that it worked. System messages and messages in Terminal can be confusing at times. With time they will make more sense.

Dale

---


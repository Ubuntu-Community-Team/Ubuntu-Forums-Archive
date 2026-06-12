---
title: "Update manager tells me another s/w management tool is running (there isn't)"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-02-11
Hi guys,

I just installed Ubuntu 6.06 i386 on my mom's laptop last night. So after that I started downloading the updates(clicking on that orange square on the task bar).

It happened to hang once or twice, after which I restarted the laptop(held down the power button). But its an old laptop, which I suspect the hard disk is gonna die(I hear clicking noises). So I kinda just want to keep it running until it dies.

Anyways, after the second time it hung after trying to update(not sure where in the update, it hung in the screensaver :(  ). When I restarted, I saw the orange update button still there, so when clicking on it, it starts up the update manager and says:

> 
only one software management tool is allowed to run at the same time


please close the other application e.g. 'aptitude' or 'synaptic' first.


screenshot: [http://img405.imageshack.us/img405/4549/screenshotwc5.png](http://img405.imageshack.us/img405/4549/screenshotwc5.png)

But I just started the laptop, and I don't have anything else running. Its a freshly installed system, other than the said updates(or failed updates, I'm not sure).

The laptop seems to be working, except when I update. Any idea? 

I'm not sure whether it has anything to do with it, but it also hangs in several places when using Xubuntu from live cd. When I right click on the task bar and select "add item to panel" , it hangs(tried it a few times).

Anyways, like I said, I just want this laptop to be functional for my mom at the moment, so I'm worried about security issues or whatnot if I don't update the system.

Cheers, and thanks in advance.
Kinson :)

---

### Post by meng on 2007-02-11
Try in terminal:
sudo dpkg --configure -a

---

### Post by jordanmthomas on 2007-02-11
```
ps -A | grep dpkg
```
If it shows anything, dpkg is indeed running.

Also, there may be a lock left at /var/lib/dpkg/lock which you must remove.

---

### Post by teaker1s on 2007-02-11
ubuntu-demon helped me when this happened to me

P> lease do this to make sure every packages is configured properly :
$sudo dpkg --configure -a

Do this to ensure there are no broken dependencies :
$sudo apt-get remove -f

If there are any broken dependencies please make sure to read,understand and follow my guide here :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

also make sure to do this (even if there are no more broken dependencies) :
$sudo apt-get install ubuntu-base
$sudo apt-get install ubuntu-desktop

---

### Post by kinson on 2007-02-11
> **meng said:**
> Try in terminal:
sudo dpkg --configure -a

This worked for me, thanks a lot ! :D

not exactly sure what it does, but thanks again, eheheheh :)

btw, is there a way to see what wrong went when the system hung? so that I can ask others or something..like a log file etc?

Btw, I've been here for some time now, and the speed of response in this forum never ceases to amaze me. I've yet to see any commercial support anywhere(computer related, banks or whatever) that has response time anything close to this. Go Ubuntu !

Kinson :)

---

### Post by Zyphrexi on 2007-02-12
> Also, there may be a lock left at /var/lib/dpkg/lock which you must remove.

how exactly is said lock removed?

---

### Post by jordanmthomas on 2007-02-12
```
sudo rm /var/lib/dpkg/lock
```
basically, dpkg puts that file there before it runs so other instances of dpkg won't try and run (they look to see if it is there before doing anything)

---

### Post by Zyphrexi on 2007-02-12
excellent

---


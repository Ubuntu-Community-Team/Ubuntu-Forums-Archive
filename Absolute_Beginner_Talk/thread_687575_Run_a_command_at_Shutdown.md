---
title: "Run a command at Shutdown?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Twizzle on 2008-02-04
I have read a few threads about similar questions, and seen posts about /etc/rc0.d and similar,  but being a bit of a newbie and not understanding what a lot of the code means that people have talked about, I thought I would ask in plain English...

I want to run this command when I shut down Ubuntu:
```
VBoxManage controlvm "Windows XP" poweroff 
```

Is there a shutdown script in the same way that there is a startup script / option? (So if I reboot or shutdown it will still close the virtualbox). I assume that I will have to tell it to wait a few minutes for Virtualbox to close first too?

---

### Post by scorp123 on 2008-02-04
As far as I know VirtualBox already does this upon shutdown. So what you are trying to do here is kind of redundant I think.

---

### Post by Twizzle on 2008-02-04
It does to a certain extent in that it pops up a dialogue box asking if I want to Save the machine state, Shut Down the Machine or Send a Shut Down Signal.

The only problem is that as I use a cube desktop with Compiz, this does not always appear on the side of the cube I am working on. As a result it appears to be stalling and I have to flick round the cube to find out what is causing the problem.

I would prefer it if when I click Shutdown in Ubuntu, it does just that, but shuts Virtualbox down gracefully too without any further imput.

---

### Post by scorp123 on 2008-02-04
> **Twizzle said:**
>  I would prefer it if when I click Shutdown in Ubuntu, it does just that, but shuts Virtualbox down gracefully too without any further imput. Make a kill script then. Read this:

[http://ubuntuforums.org/showpost.php?p=4247684&postcount=187](http://ubuntuforums.org/showpost.php?p=4247684&postcount=187)

So you could create a script which executes what you want, and then place it (or a symbolic link ... see my explanations above) into **/etc/rc0.d** (runlevel 0 = power off) and **/etc/rc6.d** (runlevel 6 = reboot). Something like e.g.:
```
#! /bin/bash
VBoxManage controlvm "Windows XP" poweroff 
```

---

### Post by Twizzle on 2008-02-05
Thankyou - That looks like just what I want. I will give it a try tonight. :)

---


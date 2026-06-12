---
title: "HELP!!!!  I have a problem instaling updates."
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by rednauj on 2008-04-05
When I try installing the updates or using the add/remove thing It says this:
An error ocurred:
The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.




P.S. I'm really new to this so please tell me step by step.
Thanks.

---

### Post by riven0 on 2008-04-05
Try going to the terminal (Applications > Accessories > Terminal), and copy and paste: **sudo dpkg --configure -a**

---

### Post by Seti on 2008-04-05
It could be you were trying to install programs while getting your updates. afaik you will get errors if for example you were

a) installing stuff via Synaptic or Add/Remove

while 

b) getting updates via ```
sudo apt-get udate
```

just a hunch

---

### Post by rednauj on 2008-04-05
riven0, Seti thanks

riven0: now says ldconfig deferred processing now taking place
I just wait or I had to do something else?

P.s. I want to know more so I leave the noob title what happend if I put the code:
sudo rm -rf anything,

---

### Post by riven0 on 2008-04-06
> **rednauj said:**
> riven0, Seti thanks

riven0: now says ldconfig deferred processing now taking place
I just wait or I had to do something else?

P.s. I want to know more so I leave the noob title what happend if I put the code:
sudo rm -rf anything,

Well, ldconfig configures the linking libraries; you can read more about it if you type in **man ldconfig**. But I honestly have no idea what ldconfig deferred processing means. I'm guessing there was something mis-configured on your system. But as long as there are no more errors, I'd say your okay. :popcorn:

As for sudo rm -rf anything; there has been some malicious advice going around the forums where people are telling new Ubuntu users to type in sudo rm -rf /, or sudo rm -rf /*, which basically deletes your entire Ubuntu installation. Therefore, it's good practice never to sudo rm -rf anything unless you know exactly what your doing. 

Welcome to Ubuntu. :guitar:

---

### Post by 4nsitian on 2008-04-06
try first 
1. apt-get upgrade.
if error persists, then
2. go in archeive folder. for this type: " cd /var/cache/apt/archives/"
and then type "rm -rf *.deb"
3.now your cache is cleared and you can install from starting.

obviously you should be root and exclusive lock access.
:lolflag:

---

### Post by keeler1 on 2008-04-06
I know its a different package management system, but back when I used fedora as my main OS I was installing a program through the add/remove software and for some reason or another I wanted to stop the process.  I hit ctrl-c which didnt work (because it shouldnt) so then I sent the process a kill -9.  Turns out that this is one of those processes that needed to shut itself down.

I ended up corrupting the database or whatever the package manager used and I had to run a rpm --reconfigure <something>.

I dont know if it is a possibility with apt, but if you killed an update process while it was running (either sent it a SIGKILL kill -9, or lost power) something could have been corrupted and need reconfiguring.

Which would be why you would need to run apt --configure -a

---


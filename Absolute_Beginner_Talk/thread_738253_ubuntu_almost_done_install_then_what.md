---
title: "ubuntu almost done install then what?"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by mikey908 on 2008-03-28
ubuntu almost done install then what? Once i have finished the install what should i do next?  Just looking for some general advice on how and what to install next. Thanx

---

### Post by jan quark on 2008-03-28
after the successful installation I would check if my drivers for the graphic card and the wlan card are recognized or if they need some tweaking

go to system > administration > restricted drivers manager
and check if there are drivers not active

if yes run an update via the terminal

```
sudo apt-get update
sudo apt-get upgrade 
```


if everything is fine then you want to install this package via terminal so the most important codecs and extension are installed

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by sailor2001 on 2008-03-28
and then go to administration/ synaptics and find programs you never dreamed of for downloading.
enjoy

---

### Post by Daveth on 2008-03-28
you may find this a handy guide to those undreamed of programs.....

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by LowSky on 2008-03-28
all I can say is welcome to the community of open source. If anything  goes wrong any of us can help

---

### Post by Furat on 2008-03-28
It is depend   what you want to do with your box

---

### Post by y-lee on 2008-03-28
I always install the build-essential package because I compile programs now and then and ya need it for that :)

---

### Post by MeTylerDurden on 2008-03-28
i would go to System / Administration / software sources /  then check the first four boxes  and leave sources box unchecked and leave the cd rom box unchecked.  (source code is for people writing programs)   
  If you want to choose a server choose other and do a few tests and pick one- (where it says download from)    

 Ok  move on to the next tab in software sources  which is third party software  and: check the first and third boxes  and leave the source code ones unchecked.  

 OK  move on the the next tab in software sources which is updates and :  check all the boxes except perhaps the( gutsy proposed)  you may want to leave that unchecked.    
  ok , and check for updates daily is good and the rest is your preference.. 

  I would then open  System / Administration / Synaptic manager  and:  I installed the flash plugin non free..                            and you may have to reinstall certain applications if they dont work ( i had to reinstall firefox  and restart your pc  if you made alot of changes.    ( on installing the flash i remember i uninstalled gnash ,but i dont remember if i installed or was there by default ..
  remember reinstalling flash or firefox from synaptic manager may be a quick fix down the road.. 

:popcorn:you're fired!
: I have a better solution. You keep me on the payroll as an outside consultant and in exchange for my salary, my job will be never to tell people these things that I know. I don't even have to come into the office, I can do this job from home.

---

### Post by MeTylerDurden on 2008-03-28
As you see i did this all manually ..   I am fresh off of windows xp ..  the terminal is a great tool and the earlier post probly did all i explained with a few commands in terminal!! :popcorn:

Tell him the liberator who destroyed my property has realigned my perception.

---


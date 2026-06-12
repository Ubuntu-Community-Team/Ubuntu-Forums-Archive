---
title: "Does the sever package have a gui front end?"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by veeateme on 2007-06-30
Morning all,

Just a query from a noobie... does the serve package come with a gui front end? If so how can I get it to run? I'm a web developer and want to slide across to a unix base system. (sick of widows crashing apache and & MySQL). So I'm after a development environment, something like a LAMP server with a desktop front end..

all help will be greatly appreciated...


Veeateme (Mark)
:(

---

### Post by Nekiruhs on 2007-06-30
No, but its really easy to get one. Just type in```
 sudo apt-get install ubuntu-desktop
```

---

### Post by chamberlain2006 on 2007-06-30
Yes.  It does.  The only difference between the server install and the normal install is that the server is more lightweight.  But you can still get those same packages on a normal install.  If you want all of the programs, just make sure you're connected to the internet, and run this command:

sudo apt-get install ubuntu-desktop

and then reboot.

---

### Post by arpegiator on 2007-06-30
Rebooting is NOT necessary,the only reason to reboot is when you add/remove hardware or want to use another kernel.
after installing the ubuntu-desktop package just do
```
/etc/init.d/gdm start
```
and then
```
startx
```
you people should stop telling other people to reboot when it's not necessary!....this isn't Windows you know!

---

### Post by AndyCooll on 2007-06-30
> **chamberlain2006 said:**
> Yes.  It does.  The only difference between the server install and the normal install is that the server is more lightweight.

That's incorrect. Out of the box the Server install comes _without_ a gui frontend. However, as has been mentioned in this thread, it is then easy to add a frontend.

:cool:

---

### Post by veeateme on 2007-06-30
Thankyou very much everone, 

for the quick responce :o (wishes MS run forums were this fast...lol) 

Happy happy happy :D:D:

Well all is working fineish...hmmm well during install got this 
----- Font config error: cannot load default config file----------
this happened for all the font files it seems but hey its up running no other probs so far

yeah! no reboot although I did get the message [FAIL] when running  /etc/init.d/gdm start
but xstart worked I'm assuming that the process was already running that's why it failed...

Again thnx for the help!:D:D

Well if I ever meet you guys, I'll buy the drinks...:popcorn:

---


---
title: "I'm in the live cd"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Xplunger on 2008-03-09
I loaded it up in safe graphics mode and installed I chose to stay in live cd, when I boot up what I installed can I choose to stay in safe graphics mode, because before when I tried the reg. graphics boot thing I just got a black screen with four lines and some stuff that said running local boot script [ok], or something like that, can't remember.

Sorry about the large block of probably grammatically incorrect questioning.

---

### Post by szymon_g on 2008-03-09
what kind of graphic card you have?
could you rewrite this errors messages?

---

### Post by halitech on 2008-03-09
you should be able to and that should make it easier for us to help you resolve whatever is causing the problem of not booting properly

---

### Post by jan quark on 2008-03-09
what is your problem? :confused:
if you encounter graphical problems, but you manage to login into the safe graphic mode
try to install ubuntu and enable the drivers for your graphic card afterwards

---

### Post by Xplunger on 2008-03-09
Yeah, safe graphic mode works perfectly, I'm using now off of the live cd, so I'm not sure if its just I need to install the Drivers for my Nvidia card or what.

edit:
When I loaded up outside safe graphic mode I believe it was just in a command line interface. I could enter and type, and when I turned it off I could see all the shutdown scripts, Just saying in case it helps.

---

### Post by halitech on 2008-03-09
chances are you either need a) the Nvidia drivers or b) might just need to reconfigure xserver

---

### Post by jan quark on 2008-03-09
please post the result of the terminal command

```
sudo lshw
lspci
```

to clarify your hardware

---

### Post by Xplunger on 2008-03-09
ok, so when I boot up from my harddrive is there an option to load in a safe graphics mode, just to be safe, and then where would the restricted drivers be?

---

### Post by jan quark on 2008-03-09
if your internet connection is working during the live cd session you can download the restricted drivers going to

system > administration > restricted drivers manager

and checking the box next to your graphic card entry

---

### Post by Xplunger on 2008-03-09
Sweet thanks for the help. I can't wait to really start using it, and it will also allow me to beginning actually apply the knowledge that I hope I'm going to get from some linux books I've picked up.

---

### Post by Xplunger on 2008-03-09
Thanks guys, I just booted up form the hdd and everything worked without error :)!

---

### Post by halitech on 2008-03-09
glad to hear it worked for you :D enjoy your new found freedom and don't forget to mark this as solved :)

---


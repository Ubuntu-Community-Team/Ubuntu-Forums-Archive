---
title: "[SOLVED] a few questions about 7.04 and the one due out in oct."
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by xxhaloownerxx on 2007-09-21
Hi


yesterday i booted up my computer and started gaim, 30 mins later, ubuntu 7.04 completely froze, no mouse, no keyboard, nothing ive gotten the following error 3 times 

E [20/Sep/2007:19:39:16 -0400] Creating missing directory "/var/run/cups/certs"

FED up with the problem, i installed a freash install, im on it right now, i went to system log and suprise! it followed me!

E [21/Sep/2007:15:19:16 -0400] Creating missing directory "/var/run/cups/certs"

i have not had a crash, SO FAR. there seems to be a major flaw in 7.04 with this folder. anyway i can keep this from happening? or any way i can fix it?


moving on,

PLEASE tell me that the new version wont be as near as buggy as 7.04, i dont want to have to switch back to 6.06 :(

---

### Post by kellemes on 2007-09-21
[https://answers.launchpad.net/ubuntu/+question/2077]("https://answers.launchpad.net/ubuntu/+question/2077")

---

### Post by mlentink on 2007-09-21
> **xxhaloownerxx said:**
> PLEASE tell me that the new version wont be as near as buggy as 7.04, i dont want to have to switch back to 6.06 :(

Buggy????

---

### Post by xxhaloownerxx on 2007-09-21
> **mlentink said:**
> Buggy????

very buggy indeed, graphical problems,random freezes, i almost bought vista today because i was so fed up with it. finally got everything to work after 5 hours of messing around with stuff.

---

### Post by Dr Small on 2007-09-21
Almost bought Vista!? That's a crime... Just kidding.
But really, if you have the time to sit down and play with the system, you can solve most of your problems, and it is usually free. :|

Dr Small

---

### Post by xxhaloownerxx on 2007-09-21
> **Dr Small said:**
> Almost bought Vista!? That's a crime... Just kidding.
But really, if you have the time to sit down and play with the system, you can solve most of your problems, and it is usually free. :|

Dr Small

yeah i guess your right, just school, and stress, :P anyway, so far everything works fine :) still getting the error, but nothing wierd.

kellemes, i took a look at that, not sure what to do still to troubleshoot or solve the problem.

---

### Post by st33med on 2007-09-21
You can get on the terminal or shell, I suppose? Try downloading sysv-rc-conf:
```
sudo apt-get install sysv-rc-conf
```

And then:
```
sudo sysv-rc-conf
```

And scroll down and find cupsys. Disable every option, taking note of what was on.

Does that solve your problem?

EDIT: Forgot, you have to restart.

---

### Post by xxhaloownerxx on 2007-09-21
> **st33med said:**
> You can get on the terminal or shell, I suppose? Try downloading sysv-rc-conf:
```
sudo apt-get install sysv-rc-conf
```

And then:
```
sudo sysv-rc-conf
```

And scroll down and find cupsys. Disable every option, taking note of what was on.

Does that solve your problem?

EDIT: Forgot, you have to restart.

Alright, i did what you said, im going to disable the following and report back

Cupsys  numbers 2 3 4 and 5


yes! restarted and checked the system log, no error apon booting, which was what was happening.
im very happy right now ^_^

now one totally unrelated question, where did amarok go to :( it was on automatix and now its gone :'(

Edit 2: nevermind, found it on add/remove programs ^_^

---


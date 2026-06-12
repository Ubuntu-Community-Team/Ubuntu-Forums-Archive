---
title: "Ubuntu hangs...just like that"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by nandan on 2007-10-25
Hi 
Have been on Feisty for close to six months now...after some teething troubles, things have generally been going well.
Today, though, ran into a problem..Ubuntu decided to hang. No new installs done...last done about 2 days ago and usage post install was ok.
I noticed that after around 5 minutes into my session, everything just stops. No response to keyboard commands or mouse movement and have no option but a hard restart. Any idea why this is happening? Right now I am writing this thru Windoze, so loose hardware connection etc. may not be the issue. Any help will be appreciated.

---

### Post by ItsMitsHere on 2007-10-25
in any situation like this, you should update your system if possible. though u say that u have not installed anything new, i think there is some problem with kernel module / dependencies. in any case try to clean your system, **apt-get clean**, autoremove redundant files, **apt-get autoremove** and fix missing chunks/broaken parts, **apt-get --fix-missing**. try to get some info about system log file (i dont know how:confused:) which may tell you what is the actual problem. Post back if you get anything to tell us...

---

### Post by nandan on 2007-10-25
Thanks...but I have no idea abt how to use CLI...could you tell me where and how I put in these commands? Do I put them directly into the terminal?
Thanks

---

### Post by xyz on 2007-10-25
> **nandan said:**
> Thanks...but I have no idea abt how to use CLI...could you tell me where and how I put in these commands? Do I put them directly into the terminal?
Thanks

Yes go Application > Accessories > Terminal.
Good Luck.

---


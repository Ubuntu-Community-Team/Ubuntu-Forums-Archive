---
title: "bootup freezes at running local boot scripts"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by CShane on 2007-04-01
System:
Dell PowerEdge 1900
2 Dual Core Xeon Processor 5050
2x2MB Cache, 3.00GHz, 667MHz
2Gigs of RAM
80 Gig Hard Drive

OS Ubuntu 6.06.1 LTS Server Edition

I have a Dell PowerEdge 1900 that has no pre-installed Operating System.  I installed Ubuntu 6.06.1 LTS Server Edition.  The screen said something along the lines - remove installtion CD ...will reboot.  I removed the Cd and it seemed to proceed and then locked up on me.  After 10 mins at the same spot on the screen I shut the computer off and rebooted. The computer now freezes at:

* Running local boot scripts  (/etc/rc.local)     [ ok ]

I rebooted 4 times with the same results.  

I am new to linux and Ubuntu and any suggestion would be appreciated.

---

### Post by CShane on 2007-04-01
I found the solution.  I just needed to hit the "Enter" key to get to the login.

The script does nothing.

I am now having problems logging in.  Nothing shows up on the screen when I type in the Username till I hit the enter key.  Then I get the prompt for the password.  When I type in the password it also does not show up on the screen.  When I hit enter I get the message invalid user and the password I typed in shows up at the login prompt.  

I will do some more research and post a new thread for this if needed.

---

### Post by quicksilver1024 on 2007-06-17
I am having the same problem!

Have you figured it out yet? :)

I mean...why it does that?

---


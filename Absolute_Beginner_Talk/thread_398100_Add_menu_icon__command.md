---
title: "Add menu icon / command ?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-03-31
Is there a way i can add a menu entry with a command..

sudo /opt/lampp/lampp start
sudo /opt/lampp/lampp stop

So i can quickly start a lampp server?

---

### Post by djrosen on 2007-03-31
using the menu editor you can add icons for:

gksudo /opt/lampp/lampp start

note the use of gksudo instead of sudo which is what you should use if you are using GUI tools, the easier way IMO, is to create an alias so you can start/stop from the command line

alias lstart = "sudo /opt/lampp/lampp start"
alias lstop = "sudo /opt/lampp/lampp stop"

put the above in ~/.bashrc

now from the prompt:

$ lstart
PASSWORD:

starts lamp.

---


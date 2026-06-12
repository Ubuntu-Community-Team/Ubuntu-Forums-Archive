---
title: "One More Question"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by Terrapin77 on 2006-06-25
How would I set my DSL up at my house to run on Ubuntu.  I have tried calling my ISP and asking them but they do not support Ubuntu.  I have Alltel DSL.  Do I need to try and set up my connection through my Terminal Server Client or what?  Thanks for all the help.

---

### Post by aysiu on 2006-06-25
[QUOTE=Terrapin77]How would I set my DSL up at my house to run on Ubuntu.  I have tried calling my ISP and asking them but they do not support Ubuntu.  I have Alltel DSL.  Do I need to try and set up my connection through my Terminal Server Client or what?  Thanks for all the help.[/QUOTE] In my experience with several computers and in seeing others' posts here, I don't think you should have to do anything to set it up--just make sure everything's physically connected.

Only in these situations have I seen complications with getting internet connectivity in Ubuntu:

Dial-up Modems
USB Modems
Wireless

---

### Post by Terrapin77 on 2006-06-25
When I plug in the cable to my laptop is doesn't do anything and Firefox cannot find an active connection.

---

### Post by Apple 101 on 2006-06-25
If it's a normal modem that you connect to via LAN:
1. If you get a connection via DHCP - that's fine.
2. If you have IP settings - find them out from Windows (or other OS) and write them down.

By cable, I'm assuming you are referring to a LAN (blue/gray) cable.  How did you connect to the internet before (ie: on Windows or other OS)?

---

### Post by Jucato on 2006-06-25
Try typing in the terminal:
```
sudo pppoeconf
```
That's what I used to enable my DSL internet connection.

---


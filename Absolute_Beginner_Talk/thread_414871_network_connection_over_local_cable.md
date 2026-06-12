---
title: "network connection over local cable"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Dark-Angel on 2007-04-20
hi,
   I've got ubuntu 6.06 lts on my machine and i have windows xp on my other. I have the xp one connected to my wireless router and won't to connect the xp to my ubuntu via the ethernet port. I've plugged in the cable but not sure what i need to do to set up the connect. Any help is appreciated.
Thanks in advance

---

### Post by tbg58 on 2007-04-20
Sorry for being picky, but when you say "connect" what do you have in mind? -- do you just want to ssh from the xp box to your dapper system?  Or would you like to access a file system?  If so, which file system are you trying to access from where?  Right now it looks like you have two systems on your network, both talk to the network.
That's okay -- now if you could describe exactly what you want to see that you're not seeing:
e.g. I would like to access my XP file system from Ubuntu so I can read/write files on the XP machine's drive(s) from the Ubuntu box.
-Rob

---

### Post by Cypher on 2007-04-20
Rather than directly connecting the two machines with a cable, what you should do is ensure that they are both on the same network, which they presumably already are. From there, you can run an SSH server on Ubuntu and then use PuTTY from the XP machine to connect. Once that is working, you can even run a VNC session on Ubuntu and use a VNC Viewer on your XP machine and get the whole desktop.

Regards

---

### Post by Dark-Angel on 2007-04-20
well basicly i want to connect my ubuntu machine to my xp machine so i can have the internet connection on my ubuntu machine. I'm not really sure how to put my ubuntu machine on the same network. So basily i want to get the internet connection on my ubuntu but as it doesn't have a wireless card i'm trying to work out how i can do this.

---


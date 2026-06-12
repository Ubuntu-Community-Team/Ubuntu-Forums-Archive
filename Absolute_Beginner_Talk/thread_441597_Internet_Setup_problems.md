---
title: "Internet Setup problems"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by DUDE_2000 on 2007-05-12
Having installed Ubuntu successfully ( thanks to starcraft.man ), I would like to use the internet, but it doesnt work. In our house we use windows computers, and have a windows based network.

---

### Post by wormser on 2007-05-12
You need to do some trouble shooting.  Open up the terminal and try the following.

Check that your cables are plugged in.

**ifconfig**   This command is like ipconfig in windows.  Check to see if you have an ip address.

**ping ubuntu.com**  See if you can ping anything.  Try ip numbers and domain names

Report back those results back.

---

### Post by DUDE_2000 on 2007-05-12
thanks, I'll try that

---

### Post by DUDE_2000 on 2007-05-12
do you mean the terminal sever client?

---

### Post by DUDE_2000 on 2007-05-12
typo correction: *server*

---

### Post by wormser on 2007-05-12
The terminal or shell.  It is like the command prompt in windows.  I am not in Ubuntu right now so I cannot point you to it.  Just look threw the menus.

---

### Post by amaroKer on 2007-05-12
I'm sure he means regular teminal.  Just go to Applications > Accessories > Terminal and type it in.
```
ifconfig
```

It shows me all of my network devices, and other miscellaneous information.  Just copy and paste everything that comes up after you type the code.  Are you wired in or are you using a wireless connection?

---

### Post by DUDE_2000 on 2007-05-12
as far as i can tell my current connection is wired

---


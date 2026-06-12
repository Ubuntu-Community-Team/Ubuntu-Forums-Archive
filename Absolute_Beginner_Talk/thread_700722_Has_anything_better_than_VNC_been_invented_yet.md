---
title: "Has anything better than VNC been invented yet?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2008-02-18
I have a server that needs to start up and just be on without a monitor, kbd or mouse. Problem is that VNC is not great because:

1- session needs to be logged in.
2-VNC is horrible to use compared to more modern protocols.
3-I know XDMCP is an option but apparently doesnt work in 7.10
 
What are all the options available for remote control access?

---

### Post by zerhacke on 2008-02-18
I am guessing that you need an X display to be forwarded to the remote machine.  This rules out plain Jane SSH.

Lemme look around.

---

### Post by ScottC454 on 2008-02-18
NX is the best thing I've found.  It goes through SSH and  uses compression and peforms very well.

[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

There is also something called Tight VNC that is better than regular VNC. I think it does create a new session too (not sure).

---


---
title: "so strange !can't enter ubuntu 6.10"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by wincasy on 2006-12-17
I have installed the ubuntu 6.10 on my ibm r50e laptop ,before i install ubuntu ,there was already a winxp pro exist.
when i finished the installation,i can't enter  ubuntu.it keeps me typing my username and password again and again.
when i press ctrl+alt+backspaces .it pops up a messagebox Error message:
"the greeter application appears to be crashing.Attemping to use a different one".
and i click ok .type my username and password ,i still can't enter the ubuntu .it just let me type again and again .but there was no error message.

---

### Post by dannystaple on 2006-12-17
> **wincasy said:**
> I have installed the ubuntu 6.10 on my ibm r50e laptop ,before i install ubuntu ,there was already a winxp pro exist.
when i finished the installation,i can't enter  ubuntu.it keeps me typing my username and password again and again.
when i press ctrl+alt+backspaces .it pops up a messagebox Error message:
"the greeter application appears to be crashing.Attemping to use a different one".
and i click ok .type my username and password ,i still can't enter the ubuntu .it just let me type again and again .but there was no error message.

Hmm - Control-alt-backspace is an instruction to Xorg to restart, so it may think that the greeter (display manager) crashed. 

So confirm for me what is happening - you are being prompted for a username, entering the username, prompted for a password, entering your password, and then it is just carrying on back around to prompting you for a username again? Are you sure you are typing the same username and password you did when you installed it?

One way to eliminate it being a problem with the greeter, is to try your username and password in one of the virtual terminals. As well as a graphical environment, linux has several non-graphical terminals running on your computer as well. To call one up, you can press ctrl-alt-f1. It will also ask for a username and password. Try entering there - if you cannot, it is almost certainly a problem with your entered details, if you can, well there are more things that could be wrong.. Please let us know how you do..

---

### Post by wincasy on 2006-12-17
yeah Dannystaple you are really great .you really understand what i said .
You said "Are you sure you are typing the same username and password you did when you installed it?"
yeah.if i try to type the wrong password and username  ,it will prompt me wrong username and password .
i use a none graphic terminal to enter the system .i use exactly the same usernameand password i used before .and i can enter the system .when i press ctrl+alt+f1.yes it exactly calls up a graphical interface .but when i enter the username and password ,i get back to the none graphical terminal .

what should i do ? is there some method i can use to repaire my ubuntu or is that possible i reinstall it ?
thanks a lot .

you are really great!!

---


---
title: "Prob with installing / booting/ logging on"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by cyberlite on 2006-07-08
Hey all

I Have a problem, I installed ubuntu 6 on my computer with no problem(a duel boot system xp n ubuntu) it only ask me for the computer name & to make a new password, whicht I found ood but ok I new at this, now when ubuntu boots up, its asks me for user name & password????](*,) :confused: 
Any help here?????

Thx cyberlite

---

### Post by GStubbs43 on 2006-07-08
This should have been a screen during instalation:

[img]http://img159.imageshack.us/img159/9441/w2u254ly.png[/img]

The second box is your username.

---

### Post by cyberlite on 2006-07-08
no I get no shatch screen, I,m getting a (DOS) like question to give a computer name and then it just asks me for a password.
This is right at the beging of my installation??]:confused:

---

### Post by Apple 101 on 2006-07-08
Press Ctrl+Alt+F7 when you get to the bash shell (DOS-like screen).

---

### Post by richbarna on 2006-07-08
> **Apple 101 said:**
> Press Ctrl+Alt+F7 when you get to the bash shell (DOS-like screen).
You can also put your user name and password to login and then type startx.

---

### Post by Spleenie on 2006-07-08
Strange that you end up at a CLI console though. Does ctrl-alt-F7 bring you back to a graphical login screen?

---

### Post by cyberlite on 2006-07-08
I,ve solve the prob I download another copy of the OS and installed it with no problem :-k  maybe a problem in downloading the iso or when I burnte the cd, I don,t know. But know I have another prob cant get on the net, the ethernet card is working, its active, but I cant get on the net or ping a site???
Any help here, I have not modifed nothing it was a standard instalation.:rolleyes: 

but thax all

---

### Post by Dr. Nick on 2006-07-08
You may have had the server iso install before and thats why you got a command line login.

For you ethernet problems try running the following commands from the terminal

[B]sudo ifdown eth0
sudo ifup eth0

[/B]That will disable/re-enable your card. Note any errors and post them back here. Also going into the network control panel and setting a static ip may help. I have seen alot of similar problems like this here lately

---

### Post by cyberlite on 2006-07-08
by the network tools then if i look at network information hardware info, multicast etc says not available.

---

### Post by cyberlite on 2006-07-08
I tried the sudo but it asks for pw but will not let me type it in???

---

### Post by Dr. Nick on 2006-07-08
it will type it in, you just cant see it for security reasons, when it ask type teh passwored and hit enter

---

### Post by cyberlite on 2006-07-08
it hangs for 1min or 2 when I sudo ifup eth0.
But here is a new one right after I restart the OS I have internet for a second or two??? I gave it a static ip.

---

### Post by Dr. Nick on 2006-07-08
Their are a fw similar threads going on about this tye of problem like this one
[http://ubuntuforums.org/showthread.php?t=208013&highlight=internet+works+seconds](http://ubuntuforums.org/showthread.php?t=208013&highlight=internet+works+seconds)

Is your situation similar? DSL...

---


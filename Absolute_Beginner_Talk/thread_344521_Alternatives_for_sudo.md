---
title: "Alternatives for sudo??"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by tin2 on 2007-01-23
I am looking for an alternative for sudo wherin i need not type the password.
The thing is, that i need to go into root before i can log into net and i am tired of typing my password again and again. I need to type my password for disconecting too..

---

### Post by mizar001 on 2007-01-23
Really odd that you have to type your password every time, but if you want you can follow instructions to activate root user. For me it was easy as i have done only this command :
$*passwd root*

and hence :
$ su root

when you digited your setted pass for root you are root at all effects. Remember that this is working only from terminal mode(you can launch even graphics apps), and gnome does not start nothing directly in root mode. This is the safe way of ubuntu, but most distro will follow these rules, firstly when browsing in the net.

I remember an old red hat version that used to say 'it's stupid to access the internet as root' when login as root with a web browser. Too risky.

---

### Post by Sasa_Ivanovic on 2007-01-23
You can also log in graphicaly as root, when Ubuntu boots type in root as username and your password. You will have to enable this in system prefences. I don't recommend this though.

---

### Post by angkor on 2007-01-23
> **tin2 said:**
> The thing is, that i need to go into root before i can log into net 

How come? What do you need to do every time to connect?

---

### Post by deadgobby on 2007-01-23
Yes there is a way to do what you want.
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#User_Administration](http://ubuntuguide.org/wiki/Ubuntu_Edgy#User_Administration)
Gobby

---


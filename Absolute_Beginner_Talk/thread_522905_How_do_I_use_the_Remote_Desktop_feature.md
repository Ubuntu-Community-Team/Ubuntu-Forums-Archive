---
title: "How do I use the Remote Desktop feature?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-08-11
I want to assist my Friend in using Ubuntu and the Remote Desktop feature is perfect but we do not know how to use it. 

My friend ticked all the check boxes in the Remote Desktop Preferences Window. I know now his password and his vncviewer command.

What do we do next?

---

### Post by Waappu on 2007-08-11
Hi

Type in terminal ```
vncviewer friendip
```
replace "friendip" actual ip address

Edit:

this might help
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Desktop_Sharing.2FDuplication_using_VNC](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Desktop_Sharing.2FDuplication_using_VNC)

---

### Post by wersdaluv on 2007-08-11
Can I do this even if we are not connected by a server?

We are from two different cities. Can we connect just throught the internet?

What IP do I need? His DSL's IP?

---

### Post by Waappu on 2007-08-11
Hi

You need him external IP.
He can check it e.g. from here [http://myip.dk/](http://myip.dk/)

---

### Post by bodhi.zazen on 2007-08-11
This link may help :

[http://doc.gwos.org/index.php/Reverse_VNC](http://doc.gwos.org/index.php/Reverse_VNC)

---

### Post by wersdaluv on 2007-08-11
> **Waappu said:**
> Hi

You need him external IP.
He can check it e.g. from here [http://myip.dk/](http://myip.dk/)

How about his vncviewer command?

---

### Post by medley on 2007-08-11
> **wersdaluv said:**
> I want to assist my Friend in using Ubuntu and the Remote Desktop feature is perfect but we do not know how to use it. 

My friend ticked all the check boxes in the Remote Desktop Preferences Window. I know now his password and his vncviewer command.

What do we do next?

You'll need his IP address first of all. However, if he's behind a router, he'll have to configure his router to forward ports 5800 and 5900 to his local address (probably 192.168.1.X or 192.168.0.X). And when I say you'll need his address, that's the address of his router if he has one, and not his computer. Be aware that his IP address will likely change from time to time, which can cause things to stop working all of a sudden.

Good luck.

---

### Post by moose4204l on 2008-05-29
i been trying the same thing and my and my friend cant get it to work either.

we tried 

vncviewer 192.168.0.X
vncviewer 192.168.0.X:5900

everytime we get Network is unreachable (101)

if we do the command given in system-preferences-remote desktop we get unable to resolve host by name: connection timed out (101)


whats going on here?

---


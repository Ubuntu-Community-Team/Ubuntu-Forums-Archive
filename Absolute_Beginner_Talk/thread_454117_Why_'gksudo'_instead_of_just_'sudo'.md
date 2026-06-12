---
title: "Why 'gksudo' instead of just 'sudo'?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by whitefort on 2007-05-25
Hi,

I keep reading that I should use gksudo to open any non-terminal apps, and not sudo.

I'm just curious as to why?  When I use gksudo, to, say, open nautilus as root, it works, but it also throws up some error message in my terminal window - namely:

[B](nautilus:7382): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension
seahorse nautilus module initialized[/B]

On the other hand, if I just use 'sudo nautilus', it still works perfectly, but without the error message (in this case, I just get [B]"Initializing gnome-mount extension
seahorse nautilus module initialized"
[/B]

Just curious!!

---

### Post by tkjacobsen on 2007-05-25
If you are opening the apps from a terminal i think it is pretty much the same (I always use just 'sudo'). But if you run them form the "run command" (Alt +F2) then you have to use gksudo or else you will not be able to type  the password anywhere.

---

### Post by Outrunner on 2007-05-25
because gksudo is used to open graphical appllications in su mode. I don't think the error really means anything but I may be wrong

---

### Post by maob on 2007-05-25
gksudo and sudo are actually the same.. The only difference is that gksudo displays a dialog in which you can enter your password, similar to the dialogs you see when you run synaptic or any other application that needs a password..

---

### Post by STREETURCHINE on 2007-05-25
have a read of this it will help sort you out.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> (nautilus:7382): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension

this is a harmless bug no great threat.

> gksudo and sudo are actually the same.. The only difference is that gksudo displays a dialog in which you can enter your password, similar to the dialogs you see when you run synaptic or any other application that needs a password..

this is not exactly correct,if you read the link above you will see why.

> If you are opening the apps from a terminal i think it is pretty much the same (I always use just 'sudo'). But if you run them form the "run command" (Alt +F2) then you have to use gksudo or else you will not be able to type the password anywhere.

you still need to use gksudo from terminal if opening a graphical app.

i hope this helps a little

---

### Post by ajgreeny on 2007-05-25
In theory if you use sudo you could find yourself in trouble with not being able to login at all.  Have a look at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) which will tell you more.

---

### Post by whitefort on 2007-05-25
Thanks for the replies, everyone.  OK!! I'm a convert to gksudo!!!

I had no idea that just using sudo for these graphical apps could be so risky - I'm glad I asked the question and gained this information.

Thanks again.

---

### Post by Happy_Man on 2007-05-25
Actually, I've gotten that ICE error before. I could always log in after, though.... odd.

---


---
title: "Authentication failure"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by dondad on 2007-04-26
In terminal, when I try su, I get the following errors. Also, for gksudo gedit. Can anyone tell me what is wrong and how to fix it?

This is what I get in terminal:

xxxxxx@main:~$ su
Password: 
su: Authentication failure
Sorry.
xxxxxx@main:~$ gksudo gedit
(gedit:4887): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Thanks for any help.

The problem was the permissions. It would not install wothout sudo, but it did make the folders root, so it could not modify whatever it needed to to register. I fixed that and it worked fine. Thanks for the pointers.

---

### Post by CupofDice on 2007-04-26
Ubuntu uses sudo, not su like other distros. It does use gksudo though. That error message is a bug. Just use the sudo command in the terminal like "sudo gedit".

[http://ubuntuforums.org/showthread.php?t=6267](http://ubuntuforums.org/showthread.php?t=6267) if you want to use su.


Edit without bumping post- 

STREETURCHIN -

When using the terminal, sudo works just fine. When making launchers, use gksudo.

---

### Post by Seisen on 2007-04-26
What exactly are you trying to do anyway?

---

### Post by STREETURCHINE on 2007-04-26
> **CupofDice said:**
> Ubuntu uses sudo, not su like other distros. It does use gksudo though. That error message is a bug. Just use the sudo command in the terminal like "sudo gedit".

[http://ubuntuforums.org/showthread.php?t=6267](http://ubuntuforums.org/showthread.php?t=6267) if you want to use su.

you are correct the error message is a bug and it is harmless,

but the advise of just use sudo is not correct

 for all your graphical applications you need to use gksudo

     ```
gksudo gedit 
```

---

### Post by dondad on 2007-04-27
This all started when I wanted to install a couple of applications under WINE. First, I installed ultraedit. I read some threads about doing this, and they stated that I needed to use sudo to do it, so I did the install for ultraedit with sudo. It worked fine.

I then tried to install irfanview, but , in this case, I put in the command, but it just comes back to the command line and nothing happens. No error messages, nothing. When I did the gksudo and got the error, I was trying to edit a file in the .wine directory and needed sudo to do it. When I got the error message (which is apparently a bug), I started playing around to see if I could figure out what was going on.

I guess my real question is why nothing happens when I try to install irfanview under wine?

---

### Post by STREETURCHINE on 2007-04-28
you use sudo in terminal for normal root access to install things and such 

and you use gksudo for  all graphical applications like gedit and nautilus

the error message is related to a bug it has been posted ,and it is harmless

as to the wine install of irfanview ,sorry i cant help

---

### Post by Nythain on 2007-04-28
well... you would use sudo i guess... but you shouldnt have to use sudo to install wine apps... they all install into your home directory... one would think installing with the sudo would change permissions of a lot of stuff to root that you would want to stay as your user... just speculation on that... i've never had to use sudo when installing windows apps with wine... just "wine /path/to/install.exe" has always worked fine...

---


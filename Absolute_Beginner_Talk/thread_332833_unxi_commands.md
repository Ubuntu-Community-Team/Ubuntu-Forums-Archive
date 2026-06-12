---
title: "unxi commands"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by rbhigday on 2007-01-06
Where is a good site that will give me a description of what all these unix command do?

I would like to know what they are and do and not just blindly cut and paste what already works. I guess I just want to understand what I am doing.

---

### Post by 23meg on 2007-01-06
[https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)
[http://linuxcommand.org](http://linuxcommand.org)

A web search for "unix commands" will also give you more info than you need.

---

### Post by Bachstelze on 2007-01-06
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

If, like me, you like having a real solid book in your hands, [Linux in a nutshell](http://www.amazon.com/Linux-Nutshell-OReilly-Ellen-Siever/dp/0596009305/sr=8-1/qid=1168116890/ref=pd_bbs_sr_1/105-2192374-9918051?ie=UTF8&s=books) is a must-have.

---

### Post by DavidW2 on 2007-01-06
If you are using the BASH shell - which is the default for Ubuntu - this site may work for you.
[http://www.ss64.com/bash/index.html](http://www.ss64.com/bash/index.html)

Also, the built-in man pages are a good reference.  They can be accessed by typing 

man <command>
For instance "man cd" will describe the change directory command.

If you are trying to find a command related to a function you can type
man -k <search word> 
For instance "man -k format" will list all commands with format in the description.

---

### Post by 23meg on 2007-01-06
> the BASH shell - which is the default for UbuntuActually Ubuntu is using dash now, but the change is transparent to the user.
> Also, the built-in man pages are a good reference.As well as the "apropos" command.

---

### Post by Bachstelze on 2007-01-06
By the way, the funny thing is that Ubuntu uses the Debian Almquist SHell by default while Debian itself doesn't :p

---

### Post by dorcssa on 2007-01-06
> **HymnToLife said:**
> 

If, like me, you like having a real solid book in your hands, [Linux in a nutshell](http://www.amazon.com/Linux-Nutshell-OReilly-Ellen-Siever/dp/0596009305/sr=8-1/qid=1168116890/ref=pd_bbs_sr_1/105-2192374-9918051?ie=UTF8&s=books) is a must-have.

It's too expensive for me, even if amazon.de can deliver it to our country I think..But maybe they offer a cheeper price.

---

### Post by DavidW2 on 2007-01-06
> **23meg said:**
> Actually Ubuntu is using dash now, but the change is transparent to the user.

I didn't realize that.  Thanks for the info.  That must have happened with Edgy.  I did a dist-upgrade from Dapper to Edgy and when I type "env | grep SHELL" the reply is SHELL=bash.  

> **23meg said:**
> As well as the "apropos" command.

I believe "man -k" and "apropos" are the same thing essentially.

---

### Post by seijuro on 2007-01-06
[This]("http://8help.osu.edu/wks/unix_course/intro-1.html") is a great place for an introduction to linux/unix imo. It's even downloadable in pdf and other formats.

---


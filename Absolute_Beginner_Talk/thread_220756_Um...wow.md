---
title: "Um...wow"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by telegramsam on 2006-07-22
Ok...as promised, I installed Xubuntu.  I am SO confused.  I have NO idea what I'm doing.  I know there's a "start at the VERY beginning tutorial for knuckleheads"...could you all direct me to some of those?
I don't know what repositories are, I don't know how to install software beyond "click here to download" and "do you want to install this software?" yes...no...
I wouldn't say I'm discouraged, I just need to get down with the plan...

---

### Post by GuitarHero on 2006-07-22
I would take a look at the wiki.  Try Easy Ubuntu(search the forums) to install codecs and commonly used programs for you.  Ive never tried xubuntu(only k/ubuntu) so I dont know where synaptic or its version of synaptic is, but theres a program on there that uses those packages to automatically download and install programs from those repositories.  Its very simple.

---

### Post by steve.horsley on 2006-07-22
There's also a lot on [www.tldp.org](www.tldp.org), and you can find many others by reading this forum regularly.

P.S. Also [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by K.Mandla on 2006-07-22
The Synaptic Package Manager is under Applications > System in Xubuntu. You can enable the extra repositories there, or you can open a terminal (under Applications) and edit it with this command. ...

```
sudo mousepad /etc/apt/sources.list
```
Uncomment the repositories you want (which is probably all of them ;) ) by removing the leading number sign (#) from lines that begin with deb.

Save the file with Control-S, then close mousepad and enter this in the terminal window. ...

```
sudo apt-get update
```
Now you're ready to go!

There's a better explanation here. ...

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Good luck!

---

### Post by John.Michael.Kane on 2006-07-22
These should get you going.
[**[COLOR="Green"]UDSF[/COLOR]**]("http://doc.gwos.org/index.php/Main_Page")
[**[COLOR="Red"]installingsoftware[/COLOR]**]("http://www.psychocats.net/ubuntu/installingsoftware.php")
[**[COLOR="DarkOrange"]Ubuntu_dapper_guide[/COLOR]**]("http://ubuntuguide.org/wiki/Ubuntu_dapper")

---


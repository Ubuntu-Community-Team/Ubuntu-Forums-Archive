---
title: "Can't figure this out"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by Rickster on 2006-03-18
I have installed ubbuntu 5.10 server following the directions of this site
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3)
and everything went very well till I typed in  /etc/network/interfaces...
I keep getting this error  bash  /etc/network/interfaces: permission denied.

I'm fairly new but have managed to get the gnu version networked and working fine awhile ago and I'm learning but not very good with the command line version.

could anyone help????[http://ubuntuforums.org/images/smilies/eusa_think.gif](http://ubuntuforums.org/images/smilies/eusa_think.gif)
:-k

---

### Post by az on 2006-03-18
"Edit /etc/network/interfaces  and adjust it to your needs (in this example setup I will use the IP address..."

Open a terminal and type

sudo gedit /etc/network/interfaces

---

### Post by FizDev on 2006-03-18
[QUOTE=azz]sudo gedit /etc/network/interfaces[/QUOTE]
Actually, because it is a server installation.. I believe there is no X, so no Gnome and no Gedit... Instead try using nano :)
```
sudo nano /etc/network/interfaces
```

---

### Post by Rickster on 2006-03-18
I'm using the server setup install and it logs in like this.

it start with this
Ubuntu 5.10 "Breezy Bager" server1 tty1

server1 login: admin
password: and I enter my password
admin@server1~$  sudo passwd root
it asks for my password and I enter it then asks to enter a new one and I use root

admin@server1~$  su
password:  root
root@server1:/home/admin# and this is where I type /etc/network/interfaces

The second post worked thaaaankyouuuu Tried reinstalling 4 times thinking I did something wrong.
 looks like I have a bit more reading to do.

Is there any place that has a list of all commands that I can printout.

Thank again

---

### Post by FizDev on 2006-03-18
Well you could start with the basic commands :
[https://wiki.ubuntu.com/BasicCommands?highlight=%28commands%29](https://wiki.ubuntu.com/BasicCommands?highlight=%28commands%29)

---

### Post by Rickster on 2006-03-18
Well thanks 

I thought when reading a guide to a complete working server, that all instructions were laid out and just read and type, I thought wronge. Oh well I'm up for the challenge.

I'm quite stubborn, should have asked at 8am.

I will say that installing the X/(windows) version was very easy and with a little
reading (some of these forums are really good) I was able to get a system up and running networked with 4 other xp computers.

A thanx goes out to you responders in the forums

---


---
title: "Unable to Install package: I need to be root???"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by robinlennox on 2007-05-31
Hey All,

I am trying to log into my corp VPN under Linux, via a web browser... I need to install a java applet but it insists that i need to be a root... 

Help...:(

---

### Post by southernman on 2007-05-31
I think all you need to do robin, is:

> gksudo <insert command here>
You'll be prompted for a password. Just enter the password for your user name and away you go...

I think that's what ya want.

---

### Post by robinlennox on 2007-05-31
Basically I am prompted within the browsers the following when i try and log in:  "Do you trust this...." I click yes... "do you wish to install the java appliet..." i click yes, then i get an error message "You must be login as root to install this applet"

---

### Post by HarmonicaGoldfish on 2007-05-31
try going to your terminal, and entering the command 

sudo -s

you will be asked for your password

this will log you in as root

---

### Post by taurus on 2007-05-31
If you need to install java plugin for firefox, install it with

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin
```
Then, open firefox again and see if java 1.6 plugin is there.

Otherwise, here's a guide, [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java).

---

### Post by robinlennox on 2007-05-31
I can install java applets from other websites, but this website wants me to have root permissions to do it. I have java applets installed.

I have attached a print screen of my issue.[IMG]http://img372.imageshack.us/img372/6087/javaissuewy5.jpg[/IMG]

---

### Post by lamalex on 2007-05-31
you probably need to launch firefox as root. gksudo firefox

---

### Post by Anicka on 2007-05-31
Maybe it would be possible to run Firefox as root? I "gksudo firefox" would do that. Then you should be able to install this program, but you'd better get a second opinion by somebody more experienced.

Iamalex just gave that second opinion, so I guess it's ok...

---


---
title: "how to install JAVA?"
date: 2005-06-26
forum: Absolute Beginner Talk
---

### Post by snoopgst on 2005-06-26
I am running kubuntu and want to install java.  Is there an easy *.deb file I can use to install it?

thanks

---

### Post by Alexander Kirillov on 2005-06-26
[QUOTE=snoopgst]I am running kubuntu and want to install java.  Is there an easy *.deb file I can use to install it?

thanks[/QUOTE]
 See ubuntuguide.org

---

### Post by Kvark on 2005-06-26
If/when you have done the steps at [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) then just install the package called "jre" with apt-get or synaptic. Easier then .deb files.

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=snoopgst]I am running kubuntu and want to install java.  Is there an easy *.deb file I can use to install it?

thanks[/QUOTE]


Yes. If you allow Ubuntu to access a certain software server (the other posts point out the place in the guide that tells you how) then it is easy to install java.

---

### Post by snoopgst on 2005-06-26
[QUOTE=Kvark]If/when you have done the steps at [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) then just install the package called "jre" with apt-get or synaptic. Easier then .deb files.[/QUOTE]

ok I tried doing that but I get an error:

jimmy@LinuxLaptop:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
jimmy@LinuxLaptop:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found
jimmy@LinuxLaptop:~$

---

### Post by roach of discord on 2005-06-26
Are you trying to edit that sources config file?  If so..try using pico instead of gedit.

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=roach of discord]Are you trying to edit that sources config file?  If so..try using pico instead of gedit.[/QUOTE]


it would look this way:

sudo pico /etc/apt/sources.list

after you are done, hit control and "x" at the same time to exit and save

---

### Post by snoopgst on 2005-06-27
[QUOTE=poofyhairguy]it would look this way:

sudo pico /etc/apt/sources.list

after you are done, hit control and "x" at the same time to exit and save[/QUOTE]
 thanks I got that think sorted out.  Now where is the java package uner? i can't find it.

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=snoopgst]thanks I got that think sorted out.  Now where is the java package uner? i can't find it.[/QUOTE]

Hold on a sec. Check something real quick. Are these lines added:?

> deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

If not...add them. Then type this command:

> sudo apt-get update

and when its done, this command:

> sudo apt-get install sun-j2re1.5

Boom. Java.

---

### Post by snoopgst on 2005-06-27
thanks, this place is great.

---


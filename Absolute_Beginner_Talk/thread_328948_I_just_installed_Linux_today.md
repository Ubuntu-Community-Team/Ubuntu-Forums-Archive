---
title: "I just installed Linux today"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by iqmeister on 2006-12-31
Hi, I'm a totally new to Linux, and I'm trying to get madwifi installed from here: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo).  When I try to set my device down it tells me permission denied, and it never asks for password.  Also,  I don't know what is shell terminal and how to open it in a directory.
Thanks

---

### Post by meng on 2006-12-31
Start from the beginning. What card do you have? Is your card already recognized by Ubuntu? Look in System >Admin > Networking and see if your device is listed.

You may need to tell us if you have WEP or WPA encryption, etc., if you continue to have trouble.

The terminal is under System > Accessories > Terminal.

To perform commands requiring root privileges, you preface the command with sudo
e.g. instead of iwconfig eth1 ...
you type: sudo iwconfig eth1 ...

---

### Post by riven0 on 2006-12-31
> **iqmeister said:**
> Hi, I'm a totally new to Linux, and I'm trying to get madwifi installed from here: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo).  When I try to set my device down it tells me permission denied, and it never asks for password.  Also,  I don't know what is shell terminal and how to open it in a directory.
Thanks

Are you using sudo with the commands? For example, in Ubuntu

This: > ifconfig ath0 down is wrong. You need to do this instead:

> sudo ifconfig ath0 down

Just put sudo in front of each of the commands and that will give you appropriate permission.

EDIT: meng beat me to it! :D

---

### Post by foolsh on 2006-12-31
sudo *command* 
will prompt for your password to perform superuser functions sudo = superuserdo
i.e. sudo ifconfig ath0 down

console, terminal, shell prompt,command prompt...all of these are basicly same, this is where commands are entered at a prompt much like dos.
in ubuntu goto application -> accessories -> terminal 
in kubuntu goto K -> system -> konsole

some commands for the console 
ls - list the directory contents
cd - changes directory i.e. cd /home

here's a link to some info on console commands [http://www.roesler-ac.de/wolfram/acro/Cmd.htm](http://www.roesler-ac.de/wolfram/acro/Cmd.htm)

---

### Post by macogw on 2006-12-31
> **foolsh said:**
> sudo *command* 
will prompt for your password to perform superuser functions sudo = superuserdo

su stands for "switch user" though.  I've heard it being superuser before, but some other books said "no no it's switch user, superuser is just a rumor"

---

### Post by riven0 on 2006-12-31
> **macogw said:**
> su stands for "switch user" though.  I've heard it being superuser before, but some other books said "no no it's switch user, superuser is just a rumor"

Really? I always though sudo was superuserdo? All this time I was wrong? :(

---

### Post by foolsh on 2006-12-31
[http://www.roesler-ac.de/wolfram/acro/credits.htm#2](http://www.roesler-ac.de/wolfram/acro/credits.htm#2) 
superuser

---

### Post by iqmeister on 2006-12-31
I have netgear wg511t, and right now it does not work. Sudo works good, but the second step, execute command when being in a directory.  How is that done? Because when I do it in the terminal window it tells me no such file or directory.  btw the folder is on Desktop, and it is named madwifi-0.9.2.1.

---

### Post by macogw on 2006-12-31
maybe it's superuser in sudo and switch user when it's just su?
[http://www.ss64.com/bash/su.html](http://www.ss64.com/bash/su.html) says it's "substitute user" and if you "man su" it says changes user or if no arguments are given, the default is the superuser....so it's sort of a combination of both? [http://en.wikipedia.org/wiki/Su_%28Unix%29](http://en.wikipedia.org/wiki/Su_%28Unix%29) also says "substitute user"

---

### Post by foolsh on 2006-12-31
then 

cd Desktop/madwifi-0.9.2.1.

should get you there

---

### Post by jimrz on 2006-12-31
> **iqmeister said:**
> I have netgear wg511t, and right now it does not work. Sudo works good, but the second step, execute command when being in a directory.  How is that done? Because when I do it in the terminal window it tells me no such file or directory.  btw the folder is on Desktop, and it is named madwifi-0.9.2.1.

I have a wg511t that I use with my old laptop ... "works out of the box" on (X)ubuntu  5.10/6.06/6.10 ... have you enabled the connection in Networking? are you using network-manager ? ... also check in Networking and make sure that there are valid DNS servers listed, if you had no connection while installing there probably are not and you will need to manually enter the appropriate sites.

it would help if you listed which version of ubuntu you installed and what you are using to try to connect. in any case, there should be no need to manually install madwifi fot that card.

---


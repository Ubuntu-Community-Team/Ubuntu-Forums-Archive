---
title: "sources.list"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by Struck on 2005-09-30
whenever I type >    sudo gedit /etc/apt/sources.list I get this 

(gedit:15740): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I was wondering if anyone could help me fix this?

---

### Post by tehwa on 2005-09-30
[QUOTE=Struck]whenever I type >    sudo gedit /etc/apt/sources.list I get this 
(gedit:15740): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
I was wondering if anyone could help me fix this?[/QUOTE]
Among other things, this could be caused by your machine not being listed properly in your hosts file. Type```
gedit /etc/hosts
```into a terminal and post the contents of the file.

---

### Post by Struck on 2005-10-01
root@pc12:/home/andrea # gedit /etc/hosts

(gedit:3668): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


then this shows up:

127.0.0.1 localhost localhost.localdomain pc12

# The following lines are desirable for IPv6 capable hosts
192.168.2.12 localhost localhost.localdomain pc12

---

### Post by aysiu on 2005-10-01
Does this show up in the background while you're still able to edit the /etc/apt/sources.list? I've had that warning and it doesn't affect my ability to function. Have you tried, instead...? ```
gksudo gedit /etc/apt/sources.list
``` or ```
sudo nano /etc/apt/sources.list
```

---

### Post by Struck on 2005-10-01
[QUOTE=aysiu]Does this show up in the background while you're still able to edit the /etc/apt/sources.list? I've had that warning and it doesn't affect my ability to function. Have you tried, instead...? ```
gksudo gedit /etc/apt/sources.list
``` 

I tried this one and it asked for my password and a window poped up saying Untitled 1 -gedit* blank*

or ```
sudo nano /etc/apt/sources.list
```[/QUOTE]

I tried this one and this came out:

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe

                               [ Read 36 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

---

### Post by Leif on 2005-10-01
[QUOTE=Struck]I tried this one and this came out:
## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe
[ Read 36 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell[/QUOTE]


:) that's nano for you ! it may look a bit, err, basic, but it's actually a great text editor. scroll around to edit the file, then ctrl-o to save, ctrl-x to exit.

---

### Post by aysiu on 2005-10-01
That's the /etc/apt/sources.list

Just edit it as you see fit.
When you're done, press

control-x
y
Enter

Then, you're done.

---


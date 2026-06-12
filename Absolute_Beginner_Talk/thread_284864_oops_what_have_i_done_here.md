---
title: "oops what have i done here"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-10-26
rex@Linux:~$ gksudo gedit /etc/apt/sources.list

typed this in to get to my source.list
and this message came up

(gedit:9591): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
rex@Linux:~$

what have i killed now,lol:-D

but the sources.list still loads?

---

### Post by taurus on 2006-10-26
Use a text base editor then...

```

sudo nano -B /etc/apt/sources.list

```

p.s.  That's just a warning, nothing to be worried about.  ;)

---

### Post by DougieFresh4U on 2006-10-26
Be careful or you will be in a real jamm like I am(see thread in General Help). :confused:

---

### Post by Xkutzy on 2006-10-26
It does the same thing for me, but seems to load and save files without a problem.

---

### Post by STREETURCHINE on 2006-10-26
> **taurus said:**
> Use a text base editor then...

```

sudo nano -B /etc/apt/sources.list

```

p.s.  That's just a warning, nothing to be worried about.  ;)

ok i used text editor copied the code and pasted it ,hit save but i still get warning](*,)

---

### Post by taurus on 2006-10-26
> **STREETURCHINE said:**
> ok i used text editor copied the code and pasted it ,hit save but i still get warning](*,)
What kind of warning did you get with nano???

---

### Post by STREETURCHINE on 2006-10-26
> **taurus said:**
> What kind of warning did you get with nano???

 ok i think i misinterprated your instructions i ran nano in terminal and this is what i got.

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restri$## Uncomment the following two lines to add software from the 'universe'## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ub$## team, and may not be under a free licence. Please satisfy yourself a$## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu secu$## team.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backport$##N.B. software from this repository may not have been tested as
##extensively as that contained in the main release, although it includ$
^G Get Help ^O WriteOut ^R Read File^Y Prev Page^K Cut Text ^C Cur Pos
^X Exit     ^J Justify  ^W Where Is ^V Next Page^U UnCut Txt^T To Spell
 
 when i used the text editor it just saved nano to a file so i then tried 
terminal i hope that was correct.
 i am very new and a blow by blow description would help :-D

---

### Post by taurus on 2006-10-26
When you run "nano -B" from a terminal/prompt, it will make a backup of your file first before it opens it, in case you need to go back to the original file.  And those two lines at the end of your terminal (in nano) are your commands.  For instead, if you want to exit it, hold down the <Ctrl> while pressing x.  It will ask you if you want to save it so you have to type in "y"...  You can use your arrow keys to nagivate around.

---

### Post by STREETURCHINE on 2006-10-26
thanks for your assistance ,:D  much appreciated

---

### Post by taurus on 2006-10-26
No problem, mate.

---


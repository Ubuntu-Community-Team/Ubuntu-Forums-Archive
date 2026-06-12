---
title: "gksudo problems"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by wildseven on 2006-07-17
hello. i tried gksudo because i read it was better for graphic applications, so when i did 
```
gksudo gedit /etc/apt/sources.list
```
i got this error
```
(gedit:10524): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

it also opens up sources.list, but its blank. when i use sudo instead of gksudo, sources.list has data in it.

does anyone else have this problem?

---

### Post by GuitarHero on 2006-07-17
You don't need to use gksudo for that, just use sudo.

---

### Post by ahaslam on 2006-07-17
The main difference between gksudo & sudo is where you enter your password. Sudo requires it to be entered in the terminal, gksudo brings up a graphical prompt. I also get this message, I believe that it's only because the password isn't being entered in the terminal (though that's an assumption).

I only use gksudo for launchers to programs that require root privileges, sudo seems better (and quicker) for the terminal.

I hope that puts your mind to rest.

Tony.

---

### Post by wildseven on 2006-07-17
heh thank you ^^

---

### Post by crystal on 2006-07-17
> You don't need to use gksudo for that, just use sudo.
The problem is this paragraph from the wiki entry on [RootSudo](https://help.ubuntu.com/community/RootSudo):
"NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username."

---

### Post by aysiu on 2006-07-17
Read this, especially the bottom bit:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by wildseven on 2006-07-17
lol ok, so which do i follow? those guides or the people that replied?

---

### Post by T700 on 2006-07-17
I would follow the guides.  You will often get away with not using gksudo for graphical apps, but one day it will bite you.  Better to be safe.

Paul

---

### Post by wildseven on 2006-07-17
okie dokie,

well then what about the error i get when using gksudo?
in my first post, i said that i get an error and my sources.list opens with nothing in it. how do i go about fixing that?

---

### Post by avtolle on 2006-07-17
As I understand it, gedit is not a graphical application (as thought of by the other posters); thus, sudo should be used for this purpose. With that said, gedit is truly a graphical app; and, as is pointed out in the guide linked in Aysiu's post, the error message you received is the result of a reported bug.

---

### Post by wildseven on 2006-07-17
so should i use sudo instead of gksudo when it comes to /etc/apt/sources.list ?

---

### Post by aysiu on 2006-07-17
> **wildseven said:**
> so should i use sudo instead of gksudo when it comes to /etc/apt/sources.list ?
No. You should use *sudo* for terminal applications and *gksudo* for graphical applications.

For example, ```
sudo nano /etc/apt/sources.list
``` because *nano* is a terminal application ```
gksudo gedit /etc/apt/sources.list
``` because Gedit is a graphical application.

---

### Post by wildseven on 2006-07-17
ok cool, so i should just use nano instead of gedit until they find a fix for the gksudo bug i guess, right?

---

### Post by aysiu on 2006-07-17
> **wildseven said:**
> ok cool, so i should just use nano instead of gedit until they find a fix for the gksudo bug i guess, right?
No, you can use *gksudo gedit*--the bug is only that you get a warning when nothing is really wrong. As long as you ignore the warning, you'll be fine.

---

### Post by wildseven on 2006-07-17
i did gksudo gedit and i got the warning, the difference was, when i did 
```
gksudo gedit /etc/apt/sources.list
```
sources.list pops open, but there is nothing in it.

```
 sudo gedit /etc/apt/sources.list
```

sources.list opens with all the info of my repositories ( pretty much everything thats supposed to be in there )

---

### Post by aysiu on 2006-07-17
Wow. I've never heard of that before. You're absolutely certain you typed the exact same path? ```
/etc/apt/sources.list
```

---

### Post by wildseven on 2006-07-18
yes i am exactly sure. when gedit opens, it says on the bottom left hand,
created file /home/wildseven/'/etc/apt/sources.list'

i just tested it. i made a file Example on my desktop and i wrote in it.

i did
```
gksudo gedit /home/wildseven/Desktop/Example
```
it gave me the error and it opened up gedit. again, nothing inside of it, and it said it created a file.

---

### Post by aysiu on 2006-07-18
That's really weird. It shouldn't create that file in your home directory. It should be creating it in /etc/apt.

I guess I'll have to take your word for it that you're getting that strange behavior, because I've never seen it--either on my computer or in a thread on these forums.

File a bug report about it:
[https://launchpad.net/distros/ubuntu](https://launchpad.net/distros/ubuntu)

---


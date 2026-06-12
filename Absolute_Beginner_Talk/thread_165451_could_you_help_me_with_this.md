---
title: "could you help me with this?"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by gpw1 on 2006-04-24
I downloade a program from Icewalkers web site call checkbook tracker a Linux program.
I have it opened on my desktop and I'm suppose to follow these directions:

This is the ELF executable (that means, you run the program "cbtracker" 
from the command prompt or make an icon for it with the included icon 
file in your desktop environment.)

The folder contains the following items:
Folder named HELP this for the program.
File cbt_icon.xpm
file: cbtracker
license and readme file

I have a terminal window open pointed to this cbtracker folder...:confused: 
Tried different commands with no success...

Gpw1

---

### Post by kaamos on 2006-04-24
Hello!

Try
```

chmod +x cbtracker
./cbtracker
```
The first line sets the permission to execute and the second line executes the file.

---

### Post by Iowan on 2006-04-24
This is waaay out of my league, but (at the risk of learning something myself) what commands have you tried?

OOPS... whilst I was out checking up on ELF format, kaamos sneaked in a response...

---

### Post by gpw1 on 2006-04-24
[QUOTE=kaamos]Hello!

Try
```

chmod +x cbtracker
./cbtracker
```
The first line sets the permission to execute and the second line executes the file.[/QUOTE]
THANKS,

This what happened-
george@igpw:~/Desktop/cbtracker$ chmod +x cbtracker
george@igpw:~/Desktop/cbtracker$ ./cbtracker
./cbtracker: error while loading shared libraries: libgdk_pixbuf.so.2: cannot open shared object file: No such file or directory

gpw1
george@igpw:~/Desktop/cbtracker$

---

### Post by kaamos on 2006-04-24
This is because you are using software outside the repository. So the package manager does not know you need this library.

Steps to take:
1) go to [http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/)
2) insert libgdk_pixbuf.so.2 to the "Search the contents of packages" field
3) press search and it gives you the package you need (this time it is libgdk-pixbuf2)
4) use [synaptic](https://wiki.ubuntu.com/SynapticHowto) to install the package (libgdk-pixbuf2)

---

### Post by gpw1 on 2006-04-24
[QUOTE=kaamos]This is because you are using software outside the repository. So the package manager does not know you need this library.

Steps to take:
1) go to [http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/)
2) insert libgdk_pixbuf.so.2 to the "Search the contents of packages" field
3) press search and it gives you the package you need (this time it is libgdk-pixbuf2)
4) use [synaptic](https://wiki.ubuntu.com/SynapticHowto) to install the package (libgdk-pixbuf2)[/QUOTE]

THANKS-
All set, file open just like it was suppose to. Now they include an icon in my original post can you help me with that also??? please. WOW this is sure different then M$ but more fun tooooo:-D 

gpw1

---

### Post by pbaehr on 2006-04-24
As long as you're having fun. ;)

I found installing software to be the biggest difference from Windows. Then I got a handle on apt-get and I can't believe I ever lived without it.

---

### Post by gpw1 on 2006-04-24
Are there any Tutural's for "apt -get"? I realize I got a long ways to go... One step at a time... there are other "apt's" also to remove programs, correct?

gpw1

---

### Post by cstudent on 2006-04-24
I was checking out the screenshot for this software. The guy must be a poor starving programmer. Once he paid his rent, utilities and bought food he was overdrawn by $85. :o

---

### Post by pbaehr on 2006-04-24
[QUOTE=gpw1]Are there any Tutural's for "apt -get"? I realize I got a long ways to go... One step at a time... there are other "apt's" also to remove programs, correct?

gpw1[/QUOTE]

Well, "apt-get install" installs stuff and "apt-get remove" removes stuff.

I'm pretty sure this is where I got started: [http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html](http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html)

---

### Post by gpw1 on 2006-04-24
[QUOTE=pbaehr]Well, "apt-get install" installs stuff and "apt-get remove" removes stuff.

I'm pretty sure this is where I got started: [http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html](http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html)[/QUOTE]
Thanks, I thought there was another one, will start hitting the books... As far as the poor guy in the screen shots, if all he is over drawn is 85 bucks I going to use his records...

thanks again for the help...

gpw1

---

### Post by adamkane on 2006-04-24
[http://tony.maro.net/mod.php?mod=forum&op=threadview&topicid=49&forumid=2]("http://tony.maro.net/mod.php?mod=forum&op=threadview&topicid=49&forumid=2")

---


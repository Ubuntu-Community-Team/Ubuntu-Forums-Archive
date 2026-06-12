---
title: "Make command"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by itm545 on 2006-05-31
Hi, 

Is it possible to use the "make" command on Ubuntu?  I have a file called "Makefile" and was under the impression that I could run this file by entering directory and type "make" or "Make" at the command line, however I receive a command not found message.  

There also does not seem to be a man page for make.

Cheers, 

Iain

---

### Post by deja2004 on 2006-05-31
Try this:
```
sudo apt-get install build-essential
```

cheers m8:cool:

---

### Post by itm545 on 2006-05-31
Hi, cheers for that but it asks me to enter a cd and I don't have any for ubuntu as I downloaded it for VMware...

---

### Post by kh4nh on 2006-05-31
[QUOTE=itm545]Hi, cheers for that but it asks me to enter a cd and I don't have any for ubuntu as I downloaded it for VMware...[/QUOTE]
open Terminal and type:

- sudo nano /etc/apt/sources.list

put a # infront of  "deb cdrom:..... " (right at the beginning)

remember to save it before exit

---

### Post by itm545 on 2006-05-31
HI, thanks for your help and patience.  I've added the # now but now when I run "sudo apt-get install build-essential" I get a list of errors that all start with "w: could start souce package list" followed by a URL. 

It then suggests I run "apt-get update" to fix the errors but that command just produces a similar list of errors.

---

### Post by deja2004 on 2006-05-31
Try an additional # (therefore having 2 ##s) within the sources.list file.

---

### Post by catlett on 2006-05-31
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)  Follow this guide and replace your entire /etc/apt/resources.list with this one. These are definately good. Just make sure you add Breezy repos if you are running 5.10 and Dapper repos if you're running 6.04 or 6.06.
If you're not comfortable with nano you can open a seperate window with the text editor gedit. Just take out nano and replace with gedit in the earlier command.

---

### Post by deja2004 on 2006-05-31
@catlett

nice buddy icon. you've inspired me :-) is there a place that hosts a full set of these type of avatars?

---

### Post by catlett on 2006-05-31
[http://tux.crystalxp.net/](http://tux.crystalxp.net/) Just go by the factory and pick one up. The good peopl over at crystalXP have all kinds already made and waiting for download. The only problem is deciding which one.:-D

---

### Post by deja2004 on 2006-05-31
LOL Awesome, thanks man!

---


---
title: "Server Edition"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by razor7 on 2006-06-29
Hello Guys.

Does The 6.06 Ubuntu Server Edition have a graphical desktop enabled like Ubuntu Desktop?


Thanks.

---

### Post by ajgreeny on 2006-06-29
No I don't think it does.  You will need to be good with the cli to use the server edition, or add GNOME or ubuntu-desktop to the server.

---

### Post by bruenig on 2006-06-29
server does not come with graphical desktop, but once you boot it doing this command will get you one
```
sudo apt-get install ubuntu-desktop
``` 
or if you want kubuntu or xubuntu, substitude accordingly

---

### Post by az on 2006-06-29
[QUOTE=bruenig]server does not come with graphical desktop, but once you boot it doing this command will get you one
```
sudo apt-get install ubuntu-desktop
``` 
or if you want kubuntu or xubuntu, substitude accordingly[/QUOTE]
I suggest you also install the linux-386 package, too.  Some desktop hardware (funky mice and keyboards...) does not work with the server kernel.

Usually, you don't run a graphical system on a server.  You install it and then adminster it remotely.  You don't even need a screen.

---

### Post by mavr on 2006-06-29
i am trying to get xubuntu-desktop out of a xubuntu live cd, but it doesn't seem to be in there. Don't have internet and don't know how to get it then.

---

### Post by ajgreeny on 2006-06-30
Sorry, but you can't use the live CDs as a local repository, only the alternative install CD works that way.  It's a great shame but for most people without a broadband connection it could be a near disaster.

---


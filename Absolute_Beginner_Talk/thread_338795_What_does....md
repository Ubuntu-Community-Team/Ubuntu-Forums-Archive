---
title: "What does..."
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by uuu on 2007-01-14
Dependency not satisfiable: libc6 mean? I got this message trying to install an application...I had no trouble installing it in edgy, but in Dapper Drake I'm getting this message. The app came with an installer, is it incompatible with Dapper Drake?

---

### Post by ajmorris on 2007-01-14
This means you do not have the "libc6" installed. Just go to your package manager and find libc6 and install it. Then try installing the application again.:D

---

### Post by uuu on 2007-01-14
If you're still there...I googled the application and downloaded it, I got another error that a newer version was already installed...and to be frank :(  I'm not sure what the package manager is...I just started with this:(

---

### Post by rabid9797 on 2007-01-14
> **uuu said:**
> If you're still there...I googled the application and downloaded it, I got another error that a newer version was already installed...and to be frank :(  I'm not sure what the package manager is...I just started with this:(

got to applications -> accesories -> terminal

then copy and paste:
```

sudo apt-get install libc6

```

and hit enter.

---

### Post by ajmorris on 2007-01-14
Package manager is an application to download software from the net. It comes with your linux and i think you will find it very helpful. If you have ubuntu with gnome go to "system > administration > Synaptic Package Manger" once in there i suggest searching for the application it says you already have installed. (you can just start typing when in the window with a package selected to search) :)

---

### Post by Sef on 2007-01-14
Read [Psychocat's]("http://www.psychocats.net/ubuntu/installingsoftware") installing software.

---

### Post by uuu on 2007-01-14
> **ajmorris said:**
> Package manager is an application to download software from the net. It comes with your linux and i think you will find it very helpful. If you have ubuntu with gnome go to "system > administration > Synaptic Package Manger" once in there i suggest searching for the application it says you already have installed. (you can just start typing when in the window with a package selected to search) :)

you're right, that is very useful, thanks

do any of you know of an index of commands and terms, perhaps one of fundamental commands and terms?

---

### Post by ajmorris on 2007-01-15
this is a page for linux bash commands

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by blackened on 2007-01-15
I've always had problems with libc6, especially when installing stuff from Debian repositories, as we're almost never in synch with Debian where that library is concerned.
The problem is that if you install a better version of libc6 from some other source, then you run the risk of breaking a whole lot more junk on your system, and then, in the end, having to force downgrade back to your original version of libc6.

---

### Post by ubuntu27 on 2007-01-15
> **uuu said:**
> you're right, that is very useful, thanks

do any of you know of an index of commands and terms, perhaps one of fundamental commands and terms?

Read this thread:

[TERMINAL TUTORIAL FOR BEGINNERS: ]("http://ubuntuforums.org/showthread.php?t=73885")

[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---


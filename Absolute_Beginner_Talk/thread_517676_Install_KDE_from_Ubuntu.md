---
title: "Install KDE from Ubuntu???"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2007-08-04
I would like to install a KDE (and maybe even an XFCE session) on my already installed ubuntu system.

But I **don't** want to replace the bootscreen or the login window to "kubuntu" or "xubuntu"

I only want the pure, fresh session.


Is this possible?

---

### Post by alex-desktop79 on 2007-08-04
bump.

---

### Post by Carbon Tiger on 2007-08-04
> **alex-desktop79 said:**
> I would like to install a KDE (and maybe even an XFCE session) on my already installed ubuntu system.

But I **don't** want to replace the bootscreen or the login window to "kubuntu" or "xubuntu"

I only want the pure, fresh session.


Is this possible?

Sure is (if I understand you correctly) open terminal and type

sudo aptitude update && sudo aptitude install kubuntu-desktop

Next time you log on it'll go to your normal boot process and log on screen click on the sessions button and select Kubuntu and you'll go right into KDE 

For XFCE you can do this:

sudo aptitude update && sudo aptitude install xubuntu-desktop

And change to it on the session screen on log in.

I will warn you you may end up with a few un needed programs doing this method but you can remove them because everything will be built on top of your base Ubuntu. I use Fluxbox sometimes and it carries over all the program defauts in Gnome.

---

### Post by Aurdal on 2007-08-04
Open up a terminal and enter "sudo apt-get install kubuntu-desktop".

---

### Post by alex-desktop79 on 2007-08-04
I did that on 6.10, I think, and it replaced my boot screen with the kubuntu one, any way to avoid this or has it been fixed?

---

### Post by Aurdal on 2007-08-04
If that happens just run "sudo apt-get remove kubuntu-artwork-usplash"

---

### Post by meierfra on 2007-08-04
You can choose your  login manager (kdm or  gdm) anytime via

```
 sudo dpkg-reconfigure gdm
```

---

### Post by UK-Wobbie on 2007-08-04
> **alex-desktop79 said:**
> I would like to install a KDE (and maybe even an XFCE session) on my already installed ubuntu system.

But I **don't** want to replace the bootscreen or the login window to "kubuntu" or "xubuntu"

I only want the pure, fresh session.


Is this possible?

Hey look here! [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

I look there if i was you lol I did it be for 1st go and i fu*ked up my ubuntu :(
so now i use the website to help out on codeing :)

---


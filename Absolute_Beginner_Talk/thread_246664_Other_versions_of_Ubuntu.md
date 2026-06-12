---
title: "Other versions of Ubuntu"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by jtbjustin on 2006-08-29
Hello,
I have installed Ubuntu Version 6.06, and I love it, although I would like to experiment with some of the other distributions. I have read that I can get the other destructions by using apt-get but I am curious how that would work.. If I use apt-get and install Kubuntu would I be able to choose at startup to launch Gnome(Ubuntu) or KDE(Kubuntu)?
Also, I was wondering if there is a way to use apt-get or something of a similar nature to get the server version of Ubuntu added into the desktop version I am currently using.

Thank You in advance,
Justin B.

---

### Post by Klaidas on 2006-08-29
You can install them on a seperate partition, or, you can add xfce/kde/gnome to your existing installation of ubuntu. That way you could choose which to use not on boot, but on logging-in.

Here are some links:
[http://www.psychocats.net/ubuntu/gnome.html](http://www.psychocats.net/ubuntu/gnome.html) to isntall gnome
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html) to install kde
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu) to install xfce

:)

---

### Post by ewl1217 on 2006-08-29
I'm not sure about the server, but if you want to try Kubuntu, type the following code at the terminal (in 2 seperate lines):
```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` 
You'll be able to choose KDE or GNOME from the sessions menu at te login screen. If you want to remove Kubuntu, type this at the terminal:
```
sudo aptitude remove kubuntu-desktop
```

Grr... too late...

---

### Post by Paul133 on 2006-08-29
I'm pretty sure Ubuntu already has the server ediiton built in. I'm pretty sure the server edition is just a very very stripped down version of Ubuntu (no Window Managers)!

---

### Post by PPAAUULL on 2006-08-29
I have both Kubuntu and Ubuntu. I only diffrents it the Desktop enviroment, and that can be changed when ever you like on login. I switch back and forth depending on what I feel like. Kinda silly I know but it is nice to have choice.
I hope that helps.

Paul

---

### Post by jtbjustin on 2006-08-30
Thanks everyone, you all answered my questions. Im going to install Kubuntu in my Ubuntu so I can choose which one I want at login - perfect. 

Thanks Again!

---

### Post by Jerome36 on 2006-08-30
The main difference between the regular Ubuntu distro, and the Server Edition, is that the Server Edition doesn't come with a graphical desktop enviornment, and other packages included with the Desktop Version.  It does however have various packages like Apache, PHP and mySQL already installed.

You can just add the proper packages, incuded with the Server Edition, to the Desktop version after installation, which is what I did.  [Click here](https://help.ubuntu.com/community/ApacheMySQLPHP) for instructions on how to setup and install a LAMP server.

---


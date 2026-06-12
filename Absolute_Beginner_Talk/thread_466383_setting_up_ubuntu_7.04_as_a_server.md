---
title: "setting up ubuntu 7.04 as a server"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by FourZeroFour on 2007-06-06
hi all, I am kinda new to ubuntu .. ive used it in the past, but.. I just installed the latest version of ubuntu the alternate version. I want to know if there is some kind of tutorial or something showing me to how to set up pretty much a LAMP server maybe even with a FTP server. any help is appreciated

---

### Post by Ek0nomik on 2007-06-06
You can install the Ubuntu Server edition which comes with it all built in.  It's part of the actual Ubuntu install process.

(Note:  The server edition doesn't come with a graphical environment, but you can install one with one simple command.)

Otherwise if you want Apache, PHP, and mySQL, you can do it from the terminal.

```
sudo aptitude search <name>
sudo aptitude install <name>
```

For an FTP server, you have a few options, but here is one of them:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server)

---

### Post by FourZeroFour on 2007-06-06
yeah I wanted the GUI with the server features too.. I would like to use it as a learning machine as well as a simple server getting experience setting up stuff and configuring it

---

### Post by Ek0nomik on 2007-06-06
> **FourZeroFour said:**
> yeah I wanted the GUI with the server features too.. I would like to use it as a learning machine as well as a simple server getting experience setting up stuff and configuring it

```
sudo aptitude install apache2
```

```
sudo aptitude install php5
```

Could way to get started is by typing that in a terminal.  :)

After you have installed Apache, try opening Firefox and typing:

[http://localhost](http://localhost)

If you get something, you have succeeded.

I believe the files are by default installed in /var/www, but I might be mistaken.

If you have more questions just ask.

---

### Post by esavato on 2007-06-06
howtoforge.net has a "perfect server setup" for Ubuntu.
[http://www.howtoforge.net/taxonomy_menu/1/1/50](http://www.howtoforge.net/taxonomy_menu/1/1/50)
 It may be the LTS version of Ubuntu, but most of the config is the same. 

 Also, I would suggest tuning into the Linux Reality podcast.  Chess just went over server setups.
[http://www.linuxreality.com](http://www.linuxreality.com)

---


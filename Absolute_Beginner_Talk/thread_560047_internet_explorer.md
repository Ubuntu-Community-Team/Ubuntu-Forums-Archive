---
title: "internet explorer"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by mr2v6 on 2007-09-25
Hello,
I tried using wine for internet explorer, when I go to  the wine folder and click the internet explorer icon, I get a blank white screen with Wine internet explore on the top portion (middle).  But all white screen.  Any help would be appreciated.
thanks,
Raymond

---

### Post by aktiwers on 2007-09-25
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by russell.h on 2007-09-25
[http://www.howtoforge.com/ubuntu_internet_explorer](http://www.howtoforge.com/ubuntu_internet_explorer)

If you want it for something other than some sort of development theres something wrong in your head though. Also, I don't think it works with IE 7 since you have to pass WGA.

---

### Post by LowSky on 2007-09-25
IE 7 doesn't work... try IE6 or 5

---

### Post by SOULRiDER on 2007-09-25
I second what Russel said, unless you need it for something really specific like development... stay away from it :P

---

### Post by asmoore82 on 2007-09-25
> **mr2v6 said:**
> Hello,
I tried using wine for internet explorer, when I go to  the wine folder and click the internet explorer icon, I get a blank white screen with Wine internet explore on the top portion (middle).  But all white screen.  Any help would be appreciated.
thanks,
Raymond

the stock "Internet Explorer" that comes with Wine is only there for compatibility reasons
and has no "user interface" to speak of (no back/forward/refresh or address bar).
you only need to run it just once to make it load the wine_gecko rendering engine
(which is actually Mozilla UNIX code ported to Windows and then adapted for use
in Wine's Windows environment on UNIX systems).
To do this, run it from the command line and tell it where to go;
you don't have to worry about your working directory or telling wine
the path to find the program in; it knows, so just run it like:
```
~$ wine iexplore "http://www.google.com/"
```

---

### Post by alienexplorers on 2007-09-26
Why would you want to run internet explorer.  Just another piece of junk from M$.  Stick with Firefox or Opera.

---

### Post by aysiu on 2007-09-26
> **alienexplorers said:**
> Why would you want to run internet explorer.  Just another piece of junk from M$.  Stick with Firefox or Opera.
Any number of reasons:
1. IE-only websites that even User Agent Switcher can't get around
2. Testing for web designs (yes, some people have to design websites for more than just 25% of the web browsing population)

---

### Post by perljohn on 2007-09-26
Hi


Please find this .. in the terminal.

 Stepps to install wine and IE      


       1)   sudo apt-get install wine
       2)   sudo apt-get install cabextract
       3)   wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
      4)     tar zxvf ies4linux-latest.tar.gz
   5)       cd ies4linux-*
      6)    ./ies4linux 

THis needs internet access, 

this must work ,..

Regards
Varghese
chennai
India
:guitar:

---


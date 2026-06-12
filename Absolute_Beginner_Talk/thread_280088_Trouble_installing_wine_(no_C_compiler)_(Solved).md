---
title: "Trouble installing wine (no C compiler) (Solved)"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by mdubs on 2006-10-18
I am having a really hard time understanding my problem here. I have downloaded wine from their website and I am attempting to install it. The response that I get is:
```
WINE Installer v0.75

Running configure...

configure: creating cache config.cache
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Configure failed, aborting install.

```

I saw the line about gcc so I went through synaptic and added gcc 4.0 and tried the install again. I got the exact same response. I could include the config.log file on this post but it would get rather lengthy.

I would really appreciate some help on this problem as I switched from Windows because I couldn't get anything to work right but I need several of the apps that only run on windows.

I really like linux so far but I am beating my head against the wall trying to figure out how to get things to work out. 

HELP ME PLEASE!!!!!

---

### Post by jordanmthomas on 2006-10-18
try this:
```
sudo aptitude install build-essential
```

Also, unless you want to compile it yourself, why not use wine from the repositories?

---

### Post by mdubs on 2006-10-18
P.S. I placed the wine folder that I downloaded in my home folder. I don't know if that will make a difference but I figured I would give you all of the info that I have.

---

### Post by aysiu on 2006-10-18
Why not just install Wine through Synaptic?
[http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

---

### Post by barkej on 2006-10-19
Number 9 on this list may be helpful to you.
[http://tips.linux.com/article.pl?sid=06/06/08/1651225&tid=50](http://tips.linux.com/article.pl?sid=06/06/08/1651225&tid=50)

---

### Post by mdubs on 2006-10-19
Wow, that first response came before I could even get my P.S. in. You all are great.

wine is now installed! Thank you all for your help. Now that it is installed, I will have to figure out how to use it to get all the stuff that I need installed and running, but at least I have wine!

---


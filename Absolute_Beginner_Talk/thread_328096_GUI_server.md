---
title: "GUI server?"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by dwhitten on 2006-12-30
I have used SUSE before as a server and really liked the graphical interface. When I loaded Ubuntu just now, it has a command-line interface. Is there a graphical interface available for the server side?

---

### Post by taurus on 2006-12-30
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by brendnat on 2007-01-08
I am totally new to the Lixux world but I have loaded Ubuntu Server 6.10 and that went great.  Then I wanted a GUI interface so I did the sudo commands that were posted previously in this thread.  The first two commands went fine.  It  downloaded all of the files.  The last command below doesn't seem to work and after rebooting I still have now GUI.  I'm sure I am or have done something wrong but I don't know what.

sudo /etc/init.d/gdm start

Thanks in advance for your help

---

### Post by frostie on 2007-01-08
Type startx at the prompt, ie:

$ startx


and hit enter.

---

### Post by Titus A Duxass on 2007-01-08
If you are looking for a server install with a gui and not a desktop install then the suggestion:
> sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start

Is completely over the top:

Do a search for a minimal install.

You will need to install the following as a minimum:

x-window-system-core
gdm
xterm
openbox (or similar WM)
menu

---

### Post by truman11 on 2007-01-08
After I try to update the Aptitude package I get the following error 

" could not get lock /var/lib/dpkg/lock-open (11 resource temporaily unavaliable)
Unable to locl the asmin directory (/var/lib/dpkg/)"

Any thoughts?

~T

---

### Post by brendnat on 2007-01-08
Update.

I re-ran the commands

sudo aptitude update and sudo aptitude install ubuntu-desktop and there must have been a problem with the first download because I was able to run sudo /etc/init.d/gdm start and it works perfectly now.

---

### Post by null0 on 2007-01-08
are you sure the server distro is what you want? 
You know, you can install a clean desktop setup and install the server packages you need later. it's much easier.

---

### Post by truman11 on 2007-01-08
Hi,

thanks, I suspected as much. Just to be clear

1.) install desktop, update
2.) insert server image CD
3.) open server image, install Apache, PHP, mySQL
Configure apache setting, php, mySQL

Correct?

---

### Post by Cathead Fred on 2007-01-08
Hi dwhitten, 

 Check out this website called linuxloader: [http://www.linuxloader.com/index.php](http://www.linuxloader.com/index.php)

This guy has a pictorial step-by-step guide on Building Servers with Kubuntu. 

[http://www.linuxloader.com/modules.php?name=Content&pa=showpage&pid=29](http://www.linuxloader.com/modules.php?name=Content&pa=showpage&pid=29)

You may be able to incorporate what you have now into it.

Good Luck,

Cathead Fred

---

### Post by null0 on 2007-01-09
> **truman11 said:**
> Hi,

thanks, I suspected as much. Just to be clear

1.) install desktop, update
2.) insert server image CD
3.) open server image, install Apache, PHP, mySQL
Configure apache setting, php, mySQL

Correct?
If i'm getting it right, you don't want to setup a server, you want to play around with apache, sql and php in a desktop setup. If that's the case proceed as you're saying. i usually use apt-get/aptitude/synaptic to get Apache,mySQL,php,etc , but i guess getting it from the server cd will do same thing.
and if you're just playing around locally with apache for learning and stuff, don't forget to block all the incoming trafic ;)

---

### Post by Toxicity999 on 2007-01-09
Just install the default GUI Ubuntu and LAMP or whatever it is people call it.

Pretty easy. I mean theres nothign special about a server install other than no ubuntu-desktop and the server debs right there.

---

### Post by dwhitten on 2007-04-14
How can I do this if I can't get an Internet connection on that computer?

---

### Post by Toxicity999 on 2007-04-14
If you don't mind me asking... Why did you install server if you don't have an internet connection?

---

### Post by dwhitten on 2007-04-14
I am trying to figure this out at home before I think about loading it at work. For some reason, my computer here at home isn't connecting to the Internet right now. That is my problem.

---


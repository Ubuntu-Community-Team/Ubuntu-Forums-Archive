---
title: "How can I create my own installation disc"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by ahorriblemess on 2008-02-15
OK, I've got Gutsy running just how I want it right now on my HP Pavilian 6704nr laptop (except for some sound issues). So, what I'd like to do is create an installation (recovery) disc with all of my settings, driver configuration, files and plugins. So, if I need to reinstall, I could just reinstall Ubuntu and have it come back the exact same way I had it without having to go through all the steps to get it to recognize my graphics card, sound card, wireless card, monitor, etc. 

Is that possible?


I found some instructions ([http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)) but I'd like some opinions on that method.

---

### Post by oedha on 2008-02-15
you can go to [http://help.ubuntu.com](http://help.ubuntu.com)
and find about remastersys
for me....the original cd + my own repo and also the backup of all my confs
:)

---

### Post by ahorriblemess on 2008-02-15
yeah that link is actually for remastersys, I was asking if anyone has used it. 

I have simple backup, but what directories should I back up to include configuration, and how would I load it when I reinstall Gutsy?

---

### Post by polmir on 2008-02-15
```
sudo apt-get aptoncd
```
and read this:
[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")
[https://wiki.ubuntu.com/APTonCD]("https://wiki.ubuntu.com/APTonCD")
[https://launchpad.net/aptoncd]("https://launchpad.net/aptoncd")

---

### Post by ahorriblemess on 2008-02-15
That code didn't work, but I did look up AptonCD on google and installed it. It's not ecactly what I waned, but I think that will work alright. Thanks. 

But, what I really wanted was to make a Live CD of sorts... or even my own version of the text-based installer.

---

### Post by uberlube on 2008-02-15
I know that DreamLinux has a program preinstalled that will do that and Dream is a Debianchyld so that will probobly be a good place to start.

---

### Post by Yoke &amp; Chung on 2008-02-15
Alternatively, a simpler way is to back up your whole hard disk (or just the Ubuntu partition) to an external hard disk, and a restoration will restore all your configuration and settings.

Personally I use Partimage and Clonezilla for this purpose.

---

### Post by ahorriblemess on 2008-02-15
Ah, I see. Thank you both.

---


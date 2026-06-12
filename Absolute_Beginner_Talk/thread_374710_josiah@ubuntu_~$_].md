---
title: "josiah@ubuntu: ~$ ]?????????"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Josiah87 on 2007-03-02
ok thanks for the already provided help! it was quick and awesome!

now I have what I hope to be the last question...

I did a base install (was that right?) so it ran and installed everything and now it says this

[COLOR="Red"][I]ubuntu login: josiah
password:
]
Linu ubutu 2.2.15-26-amd-server #1 SMP Thu Aug 3 03:32:26 UTC 2006 x86_64 G
NU.Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted y
applicable law.
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

josiah@ubuntu: ~$ ] "[/I][/COLOR]

then it gives me a space to type..what in the world is this?

---

### Post by taurus on 2007-03-02
Looks like you installed the server version so you have that nice and simple prompt!  Are you planning to use Gnome, KDE, or XFce4?

```
sudo aptitude update
sudo aptitude install ubuntu-desktop  <-- for Gnome
sudo aptitude install kubuntu-desktop  <-- for KDE
sudo aptitude install xubuntu-desktop  <-- for XFce4
startx
```

---

### Post by Josiah87 on 2007-03-02
I really have no idea what those are, I'm very new to the linux OS

here is what a friend recommended

Linux (Apache) 

if that helps any.

and if this helps to, the only thing I plan on useing if for, is to learn linux (just for fun) and to hose low traffic websites.

---

### Post by punx45 on 2007-03-03
awesome!

Apache would be the webserver software.  and it takes a bit to learn, but its well worth it.   check out [http://httpd.apache.org](http://httpd.apache.org) for tons of good info on setting it up and whatnot.

but probably first, you should look up some guides on "bash" which is the command shell that you have found yourself in.   take some time to get familiar with working with the command line.   make files, move files, edit files with vi or nano, and so on.   if you are just using this computer to learn and mess around with apache, dont even bother installing a graphic desktop.   you wont use it.

---

### Post by ubuntu27 on 2007-03-03
> **Josiah87 said:**
> I really have no idea what those are, I'm very new to the linux OS

here is what a friend recommended

Linux (Apache) 

if that helps any.

and if this helps to, the only thing I plan on useing if for, is to learn linux (just for fun) and to hose low traffic websites.


See this page for GNOME VS KDE Comparison:

[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

XFCE:

[http://www.xfce.org/about/tour](http://www.xfce.org/about/tour)

---

### Post by punx45 on 2007-03-03
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

---

### Post by Scorpuk on 2007-03-03
Learning with the command line is a great way to go.

One of the reasons I ended up doing this is that I am away from my linux box for extended periods of time and if I want to do anything to it I can log on with putty (ssh) and start controling it from almost anywhere. 

OK this can be done with the graphic front end, but think of the bandwidth required to repeat the desktop on the remote terminal compared to just a few bits of text.


I also control my box with webmin, which is an https front end allowing me to do all sorts with it. Again it has a very simple command line control where i can send single non interactive commands, ie I cant say yes/no or select options.


THE most frustrating part of the desktop, at the beginning, I found was browsing with nautilus and not being able to edit a file outside my home folder. I didnt realise until much later that I needed to run nautilus as the root user and that the only way to do it was to execute a command at the command line. :-)


Anywho, back on track, I would recommend at least knowing the basics to the command line. :D

---


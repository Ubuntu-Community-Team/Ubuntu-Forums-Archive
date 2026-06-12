---
title: "Install successful!  Now what?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by antihero on 2007-01-06
I just got a Dell Inspiron E1405 laptop and decided to install Linux for my first time ever.  I am dual booting with Windows XP MCE.

The Ubuntu 6.06 alternate install went surprisingly well using some great instructions and advice from this forum.  The only hitch I encountered was my screen resolution was initially stuck at 640x480.  I installed the 915resolution package (which is well-documented) and I was good to go.  I then installed the 686 SMP kernal to get dual core working and successfully removed the old kernals.

Now that I'm up and running, what should a first time Linux user be doing? 

I really want to learn the ins and outs of Ubuntu (and Linux as a whole).  Should I buy a book on Linux?  Use an online guide?  Just mess around by myself?

I was actually thinking about wiping out both my Windows and Ubuntu installs and starting from scratch again.  This way I could rethink my partitions and actually try to understand what I was doing when I installed Ubuntu (and maybe create a guide specific for the e1405).

Any suggestions are greatly appreciated!

---

### Post by CroEragon on 2007-01-06
My advice would be to back everything important up and than mess around. I wish you can see my first Ubuntu installation. in matter of 3weeks i trashed it trying things out. I did lot of stupid things but i learned something. Then i wiped it and installed it properly and no ti is my main OS, tweaked how i want it and im very happy with it. Still there are few issues (damn freezing) but my (now) Kubuntu works pretty well. And you should read books but not buy them. For practical tips how to do something see HOWTO sections and [www.ubuntuguide.com](www.ubuntuguide.com) and for basics about ubuntu and Linux Google is your frend. At least was/is main when it comest to computer books. There are tons of (non)GPL books about Linux/Ubuntu.

---

### Post by jvc26 on 2007-01-06
Well the first main question to ask is - what are you going to use your Ubuntu partition for - and then find your favourite apps to do things with. Open Office, and most of the best apps in my opinion are already there, but theres a few you may consider adding, including k3b which is a really good cd/dvd burning app.

As to guidance of what to do next, I'd check out ubuntu guide, as thats really helpful on this:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
Installing things other than those in the repositories is explained pretty well here:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)
And should you want read-write support for NTFS you can have a look here:
[http://ubuntuforums.org/showthread.php?&t=217009](http://ubuntuforums.org/showthread.php?&t=217009)
In terms of unix and commands and the like:
[http://www.indiana.edu/~uitspubs/b017/](http://www.indiana.edu/~uitspubs/b017/)
was a simple guide, and there are better ones out there. A simple
```

man *app name/command name*

```
In terminal will tell you about the commands available for that app.

Welcome to linux,
Il

---

### Post by sailor2001 on 2007-01-06
and as for resizing your partitions, you already have qtparted in your pc to do that (applications/sytem tools)

---

### Post by teaker1s on 2007-01-06
automatix a quick solution-search forums for details.
secondly in terminal
[COLOR="Red"]gksudo synaptic [/COLOR]
preferences-general, tick recommended packages as dependencies
and install whatever takes your fancy

---

### Post by antihero on 2007-01-06
Thanks for the tips so far!  Very helpful.

My main reasons for installing Ubuntu:

1. To get become familiar with Linux (I like to be well-rounded)
1. To see whether Ubuntu **can **replace Windows as my default o/s (in terms of what I use my PC for on a daily basis - which is generally pretty basic stuff)
2. To see whether I like Ubuntu enough to make the switch

---

### Post by saadakhtar on 2007-01-06
i would personally suggest that you should look around this forum for a bit before you can decide what goals you want to achieve using ubuntu.
i started using ubuntu about 2 months back, i started out as a beginner but thanks to this forum i have learned a whole lot about this awsome OS.
i even implemented ubuntu in my cooperate environment. I have noticed that a lot of beginners have problems using or finding applications that in other case would be easily available for WIN32 OS. You can look around this forum and find ubuntu compatible software. If using another operating system is your absolute need than you can start thinking about virtual machines.
e.g. i have a ubuntu dapper server running in my office that handles my file server and runs our webserver but we needed to use another operating system (MS OS) so i used VMware to install a virtual OS. Now i can run windows as a virtual OS with in my linux OS.

There are numerous reasons to cross over to ubuntu so just look around and work with what suites you.

---


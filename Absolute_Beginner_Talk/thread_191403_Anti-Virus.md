---
title: "Anti-Virus?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by linux_student_user on 2006-06-07
I was wondering if someone could give me instructions on how to install and run some anti-virus software on my ubuntu machine, I GUI would be nice because im abit new to linux. 

Thanks :KS

---

### Post by _simon_ on 2006-06-07
You do know that you don't *need* antivirus under linux don't you?

---

### Post by kaamos on 2006-06-07
If you really want, use synaptic to install the package "clamtk". Note that linux antivirus programs primarily scan for Windows viruses (for example on an email-server) due to the fact that there are very few Linux viruses.

---

### Post by mostwanted on 2006-06-07
There are currently no active viruses for Linux and actually creating viruses for Linux is a lot harder because of the permissions system (unless you log in as root all the time, which Ubuntu cannot even do by default). The fact the viruses for Windows are so common is probably because most Windows users run as a root (in Windows called administrator) by default, but of course it's also because Windows is used by 95% of personal computers and that "market" is a lot more fun to program viruses for.

---

### Post by glotz on 2006-06-07
Besides that, ClamAV's the one we keep hearing about
[https://wiki.ubuntu.com/ClamAV](https://wiki.ubuntu.com/ClamAV)

---

### Post by ramcosca on 2006-06-07
This thread is one of those which just say "**Linux >>> Windows**".

---

### Post by henry95 on 2006-06-07
ClamAV is a nice ant-virus program, you might also want to check out avast!  I don't know if you can 'apt-get install avast' but you can download it for free from their webpage [http://www.avast.com]("http://www.avast.com")

It is always a good idea to run an anti-virus/firewall on any OS you run.  I'd rather be safe then sorry.  One day a nasty virus will hit the linux community and many people will be caught with their pants down.

---

### Post by Jason_25 on 2006-06-07
.

---

### Post by Jason_25 on 2006-06-07
[QUOTE=henry95]
It is always a good idea to run an anti-virus/firewall on any OS you run.  I'd rather be safe then sorry.  One day a nasty virus will hit the linux community and many people will be caught with their pants down.[/QUOTE]
And how will that be?  Will it come through the repos which are reviewed, signed with a gpg key and compiled from source?  Or will it come as a worm through ubuntu's totally closed firewall with no ports open?  Or as an exploit that happens to work on one of the tens of different browsers linux users use?

---

### Post by r3st on 2006-06-07
havent tried it myself but...

[http://free.grisoft.com/doc/20/lng/us/tpl/v5](http://free.grisoft.com/doc/20/lng/us/tpl/v5)

btw linux has built anti-virus
its called "linux"

---

### Post by henry95 on 2006-06-07
[QUOTE=Jason_25]And how will that be?  Will it come through the repos which are reviewed, signed with a gpg key and compiled from source?  Or will it come as a worm through ubuntu's totally closed firewall with no ports open?  Or as an exploit that happens to work on one of the tens of different browsers linux users use?[/QUOTE]

You can do a search for "linux" here
[http://vil.nai.com/vil/default.aspx]("http://vil.nai.com/vil/default.aspx")
and you can see a current list of some.

Linux virus's are rare yes, but windows ones are not.  You can easily spread virus's through e-mail attachments and infect other users, even if your machine is not directly affected.

Javascript malware can affect all machines, FireFox is not 100% secure, and I'm sure that is the browser of choice for the majority of Ubuntu (and other distros), I don't even think pine is 100% safe..  It only takes one untrusted piece of software run as root to cause some damage.

There is no harm running an anti-virus on linux, this topic has been debated many times over and I don't feel like starting another.  

Back to the main topic...

[QUOTE=linux_student_user]... GUI would be nice because im abit new to linux. 

Thanks :KS[/QUOTE]

avast! has a simple GUI that you can use to run updates and scans.

Cheers!

---

### Post by xyz on 2006-06-07
[QUOTE=linux_student_user]I was wondering if someone could give me instructions on how to install and run some anti-virus software on my ubuntu machine, I GUI would be nice because im abit new to linux. 

Thanks :KS[/QUOTE]
I don't know whether you are 'DAPPERing' or 'BREEZYing' but just in case:

[http://www.ubuntuforums.org/showthread.php?t=136064&highlight=antivirus](http://www.ubuntuforums.org/showthread.php?t=136064&highlight=antivirus)
[http://www.ubuntuforums.org/showthread.php?t=88357&highlight=antivirus](http://www.ubuntuforums.org/showthread.php?t=88357&highlight=antivirus)
Don't catch a cold...:wink:

---

### Post by az on 2006-06-07
[QUOTE=linux_student_user]I was wondering if someone could give me instructions on how to install and run some anti-virus software on my ubuntu machine, I GUI would be nice because im abit new to linux. 

Thanks :KS[/QUOTE]
[https://wiki.ubuntu.com/Security](https://wiki.ubuntu.com/Security)

Although that kind of software is pretty much useless.

---


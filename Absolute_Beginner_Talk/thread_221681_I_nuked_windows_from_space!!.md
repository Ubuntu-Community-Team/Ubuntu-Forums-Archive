---
title: "I nuked windows from space!!"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by denfoote on 2006-07-23
Now I have a bunch of questions.

I've only been at this for a couple of hours so bear with me.

Do I need a software firewall?? In windows I was using Zone Alarm. What's available in the Linux world??

What about anti virus software?? I was using AVG. Is there something I can download??

Thanks in advance.

BTW, the OS seems pretty stable so far!!

---

### Post by T700 on 2006-07-23
> **denfoote said:**
> Now I have a bunch of questions.

I've only been at this for a couple of hours so bear with me.

Do I need a software firewall?? In windows I was using Zone Alarm. What's available in the Linux world??

What about anti virus software?? I was using AVG. Is there something I can download??


If you are behind a NAT enabled router, a firewall is optional, but always a good idea.  Just open up terminal (the "command line") and type

```
gksudo firestarter
``` 
and hit Enter.  Put in the password you log on with.  Follow the simple wizard to set it up.  Note:  The interface does not have to running for the firewall to be working.

You do not need antivirus programs unless you are running a mail server.  Then it is only to prevent you passing on infected emails to Windows machines.  Your Linux box does not need an antivirus program.

Please check out the links in my sig.  They will give you a good introduction to Ubuntu.  Welcome to the forums!

Paul

---

### Post by kinematic on 2006-07-23
uhmmm....it might be a good idea if he installed firestarter first ;)

---

### Post by T700 on 2006-07-23
> **kinematic said:**
> uhmmm....it might be a good idea if he installed firestarter first ;)

Oops...thought it was there by default.

Paul

---

### Post by GuitarHero on 2006-07-23
You dont really need antivirus but i think AVG is available for linux.  There really arent any linux viri that pose any threat.  Firestarter is a good firewall.

---

### Post by Sef on 2006-07-23
> You dont really need antivirus

You need an anti-virus, if you have a mail client.  As T700 said, "You do not need antivirus programs unless you are running a mail server. Then it is only to prevent you passing on infected emails to Windows machines."  (see above post.)

---

### Post by JoWilly on 2006-07-23
There are a few antiviruses in the repos (aegis is one).

The excellent Avast has also released a linux version (avast.com).

---

### Post by Uncle Spellbinder on 2006-07-24
> **JoWilly said:**
> There are a few antiviruses in the repos (aegis is one).

The excellent Avast has also released a linux version (avast.com).

I might try this. RPM or TAR GZ available here: [**avast! Linux Home Edition**]("http://www.avast.com/eng/download-avast-for-linux-edition.html")

---

### Post by jrev on 2006-07-24
this is a windower reflex : an anti-virus.

2 years with linux and I am still waiting for a good reason to install an anti-virus or firewall

---

### Post by risbac on 2006-07-24
Even firewall is optionnal for Ubuntu; As said before, if you have a router, you are already partially protected. Then  by default, all ports are closed on Ubuntu. So unless you have some specific needs, both antivirus and firewall are not necessary.

---

### Post by andrew_stoned on 2006-07-24
what if your dual booting with windows? Would an Anti-Virus program be a good idea then (so you don't get windows infected?)

---

### Post by T700 on 2006-07-24
> **Sef said:**
> You need an anti-virus, if you have a mail client.  As T700 said, "You do not need antivirus programs unless you are running a mail server. Then it is only to prevent you passing on infected emails to Windows machines."  (see above post.)

Not being in politics, I seldom have the honor of being misquoted, but this may be such a case.

I suggested that he needs an antivirus program only if he runs a mail *server,* not if he is running a mail *client.*  A server would be Sendmail or the like--something that handles distributing mail to others.  A client would be Evolution, Kmail, etc. and only allows him to read/write email for himself.

Paul

---


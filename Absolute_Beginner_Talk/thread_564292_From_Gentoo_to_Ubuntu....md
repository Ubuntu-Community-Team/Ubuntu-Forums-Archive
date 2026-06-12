---
title: "From Gentoo to Ubuntu..."
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by ninja1990 on 2007-09-30
I guess I'm not a beginner, coming from Gentoo, but I'm not all that comfortable with Ubuntu yet.  Actually, I'm running Kubuntu.  I just thought I'd drop in and say hi!  I'm pretty happy with Kubuntu, right now.  In comparison to Gentoo, Kubuntu is a real charm.  After two years with Gentoo, when my fourth install broke, I thought that I'd had enough.  I looked at Debian, then I came to Kubuntu.  Apparently, the compromise between efficiency and power is astounding.  Good work!

You didn't that I wouldn't ask any questions, did you: is there a good starter guide?  I want to get some programs installed.  Does Ubuntu have the same conservative release policy that Debian does?  I don't like that about Debian.  The stable branch is just too far behind.

---

### Post by ramjet_1953 on 2007-09-30
Welcome!

This link may help you with any issues that arise:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Regards,
Roger :cool:

---

### Post by bodhi.zazen on 2007-09-30
Welcome to Ubuntu, love the avatar ...

Follow the links in my sig, ask if you run into a specific question/issue

---

### Post by ninja1990 on 2007-10-01
Thanks, I haven't tried any of this yet, but I will soon enough.

---

### Post by Perfect Storm on 2007-10-01
A good place to start is setting up the source list so you get alot of applications/libs/etc. available; You can make your source list here; [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

```
sudo nano /etc/apt/sources.list
```

Please reading the stuff about KEY (safty device).

```
sudo aptitude update && sudo aptitude upgrade
```

Other goodies you can add (from my source list);

[b]### Compiz Fusion ###
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

## Cinelerra for Pentium4 ###
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/) ./

## Games from VieWizard -- [http://www.viewizard.com](http://www.viewizard.com)
deb [http://viewizard.com/linux](http://viewizard.com/linux) debian/ 
[/b]

---

### Post by hyper_ch on 2007-10-01
Well, Ubuntu doesn't use the newest releases itself. However having an Ubuntu release cycle every 6 months you will not stay too far behind.

I noticed this for rtorrent. In the repos you currently have v 0.6.x, in Gutsy there will be 0.7.4 while the current SVN (unstable) release is 0.7.8.

In each release the software might not be bleeding edge but as said above, getting a new release every 6 months isn't too bad.

---

### Post by tdrusk on 2007-10-01
Welcome. Glad to hear a Gentoo user likes Ubuntu. It makes me feel better about not attempting Gentoo.

Personally I think the best feature of Ubuntu is community support. This is one of the fastest forums I have ever been on. All the people are great too.

---


---
title: "Configuration for Web Development"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by ceestand on 2006-12-07
I plan on installing Ubuntu on a secondary box to primarily run as a LAMP development server. I want to learn Apache, MySQL, and PHP; so why not go all the way and learn about Linux at the same time. I will be developing on my primary WinXP box using Dreamweaver. While my number one concern is becoming proficient in the LAMP technologies, I also wouldn't mind exploring Ubuntu as a desktop, or more accurately, the applications that run on Linux (e.g. Pixel). My understanding is that Ubuntu server doesn't have a graphical interface and as such wouldn't be able to run these programs. This is my first time with Linux, and I want to keep things as simple as possible to make problem solving easier. I am currently an ASP.NET developer.

My questions are: If I choose to run LAMP off of the Desktop version, will it negatively affect my understanding of common administration of a LAMP server?

and: Will I be missing out if I install Apache, PHP, & MySQL via a package as opposed to manually?

---

### Post by pmasiar on 2006-12-07
> **ceestand said:**
> My understanding is that Ubuntu server doesn't have a graphical interface and as such wouldn't be able to run these programs.

Not exactly true. Many purists insist of **not installing** any GUI stuff on server, because running it uses (1) resources (RAM) and (2) lowers security (more programs = more possibilities for security breach). But you can certainly install GUI management tools or any other programs you want and use them on computer which runs as server, if you decide above concerns not relevant.

Or you can dual-boot your Windows box to get another Linux computer to play with: install Ubuntu desktop, and then install LAMP to make your own learning LAMP "server". You have the Freedom. :-)

> This is my first time with Linux, and I want to keep things as simple as possible to make problem solving easier. 

So I assume your "server" is for learning Linux now, not to run production services? Be prepared that you  will break things while learning, **don't learn on production server** which needs be 100% up and running. 

> If I choose to run LAMP off of the Desktop version, will it negatively affect my understanding of common administration of a LAMP server?

There are many ways to administer a server. L33t admins use headless server (no monitor attached) and remote terminal commandline, but you don't have to. :-) One tool what helps me a lot is **Midnight commander:** it is non-gui, character-based appplication, but is very visual. I use mc for everything :-)

> Will I be missing out if I install Apache, PHP, & MySQL via a package as opposed to manually?

Yup, you will miss a lot! :-) For me **that's whole point for using debian/ubuntu:** let smart folks (packagers) resolve all libary versions, dependencies, placing files in proper places, set correct defaults, so security updates can find them and upgrade them, and I don't have to remember, or even know it! Enough for me is to learn where configs files are, and what options I want.

If server is configured as Ubuntu makes easier to ask for help (on ubuntu forums). Use RedHat forums for redhat server, etc.

Use either synaptic GUI (couple mouseclicks) or apt-get (copule commandlines) to install LAMP, but use ubuntu packages, not raw sources!

You **will** break it couple times, and learn many things while fixing it. It is part of the fun. Good luck!

---

### Post by ragnar_123 on 2006-12-07
you can easily install lamp.

```

sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server

```
pretty simple, eh?

---

### Post by ceestand on 2006-12-07
Thanks for the replies!

I guess my only question now is how likely is another LAMP server that I might run into later on going to be "headless"?

I'm leaning towards installing (L)AMP on the Ubuntu desktop under the assumption that even though it's there, I can ignore the GUI and run things from the command line anyway.

---


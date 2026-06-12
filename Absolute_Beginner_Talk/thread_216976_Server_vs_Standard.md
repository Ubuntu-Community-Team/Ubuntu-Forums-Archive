---
title: "Server vs Standard"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by asmith3006 on 2006-07-16
Hi.

What is the difference between the server and the standard version? I work on making websites quite a bit and have looked at the standard version, but can't see any easy way to install mySQL, php apache etc.

So, first of all, is the server as user friendly as the standard version and secondly do I need the server version rather than the standard version?

Loving Linux, haven't used it for 4 years and it's come on a LOT since then!!

Thanks.
Andrew.

---

### Post by Albi on 2006-07-16
The name is a bit misleading, server install is basically a bare-bones install of ubuntu, with no gui or anything.  And you would probably install those programs via apt-get

---

### Post by taurus on 2006-07-16
Sounds to me like you will be using your machine too so I would go with the desktop version, having Gnome as your window manager.  Then, if you decide to run sshd, ftpd, httpd, etc., just install them with apt-get/aptitude/synaptic...

---

### Post by jordilin on 2006-07-16
If I'm not wrong the Server edition comes bundled with apache, mysql and all the necessary tools to run a server. In the Desktop edition you have to install these tools by your own

---

### Post by Albi on 2006-07-16
Hmm if that's true then from a server install do sudo aptitude ubuntu-desktop
for the gui

---

### Post by taurus on 2006-07-16
> **Albi said:**
> Hmm if that's true then from a server install do sudo aptitude ubuntu-desktop
for the gui

Yes.  You may have to configure your video card and your monitor with

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by asmith3006 on 2006-07-17
Ok, I think I'll go with the desktop version and then install php/apache/mysql. Apparently apt-get does it all for you if you ask it nicely. I've never even heard of it before, but it sounds sweet!

Now have to deal with the challenge of dual screens! Plus I may be getting a third soon, does anyone know how it handles three screens? Also, if I have dual screen can I select different desktops for the different screens?

---

### Post by az on 2006-07-17
> **taurus said:**
> Yes.  You may have to configure your video card and your monitor with

```

sudo dpkg-reconfigure xserver-xorg

```

No.  When the xorg packages are istalled, it gets configured.  That's why the command is called dpkg-REconfigure....

---

### Post by az on 2006-07-17
> **asmith3006 said:**
> Ok, I think I'll go with the desktop version and then install php/apache/mysql. Apparently apt-get does it all for you if you ask it nicely. I've never even heard of it before, but it sounds sweet!


sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

All of those packages are in main.

See:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

and

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by mcduck on 2006-07-18
I've understood that the Server install CD has option to also install LAMP server during the system installation. It might be the easiest way to do that and then just 'sudo apt-get install ubuntu-desktop'.. Much less work this way than if you install desktop and then all server staff by hand. :)

---

### Post by jordilin on 2006-07-18
> **mcduck said:**
> It might be the easiest way to do that and then just 'sudo apt-get install ubuntu-desktop'..
The server edition, does not install ubuntu-desktop by default? It has only a terminal to do admin tasks?

---

### Post by mcduck on 2006-07-18
> **jordilin said:**
> The server edition, does not install ubuntu-desktop by default? It has only a terminal to do admin tasks?
yes, as you don't need GUI to run a server and it's easier to install if needed than remove when not needed ;)

---

### Post by 3rdalbum on 2006-07-18
> **jordilin said:**
> The server edition, does not install ubuntu-desktop by default? It has only a terminal to do admin tasks?

Exactly. After all, how many rack-mounted servers have you seen with monitors attached?

---

### Post by asmith3006 on 2006-07-18
So if I do the apt-get ubuntu-desktop then it'll be back to the standard desktop? It even sorts out my graphics and optical mouse drivers etc?

Sweeeeeeeeeeet.

Thanks all :)

Andrew.

---

### Post by az on 2006-07-18
> **asmith3006 said:**
> So if I do the apt-get ubuntu-desktop then it'll be back to the standard desktop? It even sorts out my graphics and optical mouse drivers etc?

Sweeeeeeeeeeet.

Thanks all :)

Andrew.


Install linux-386, too.  The server kernel does not play nice with all desktop hardware.

Linux-386 is the kernel package for 386 machines.  You may want 686, k7, smp or other.

---


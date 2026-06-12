---
title: "Adding server install"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by mbrang00 on 2006-07-24
Durring install i notice an otion to install text, GUI, and server,

Can I install server ontop of text to get both?

---

### Post by Kilz on 2006-07-24
> **mbrang00 said:**
> Durring install i notice an otion to install text, GUI, and server,

Can I install server ontop of text to get both?

Gui or Desktop is the live cd.
Text or Alternate is just an installer, it works in a lot of places the live cd dose not.(My favorite)
Server installs without a operating system without a desktop. This is for machines that will be used as a server.

They all install the operating system, installing one on the other erases the previous install. If you want a server, but would like a desktop. You can go one of 2 ways.
1) Install the server, then once it is installed use the command ```
sudo aptitude install ubuntu-desktop
```for Gnome or 
```
sudo aptitude install xubuntu-desktop
``` for Xfce or
```
sudo aptitude install kubuntu-desktop
``` for kde

2) Install the standerd install and then [follow this howto]("https://help.ubuntu.com/community/ApacheMySQLPHP")
I would go with method 1 as its not as hard.

---

### Post by kinematic on 2006-07-24
> **Kilz said:**
> 
installing one on the other erases the previous install.


no it doesn't.
never ever ever do an install over a previous one or install 1 distro over another.
it completely messes up your file system!
only formatting or deleting erases a previous install.

---

### Post by az on 2006-07-24
> **kinematic said:**
> no it doesn't.


Yes it does by default.  You have to select manual partitioning and then select to keep existing data to do what I think you describe.

See here what packages you need to install to bring in the LAMP stack on top of the desktop.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

But a server install will not install any server packages.  It is just a base system on which you can.

---

### Post by Kilz on 2006-07-24
> **azz said:**
> Yes it does by default.  You have to select manual partitioning and then select to keep existing data to do what I think you describe.

See here what packages you need to install to bring in the LAMP stack on top of the desktop.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

But a server install will not install any server packages.  It is just a base system on which you can.

But the server CD has a lamp install that will setup lamp. Then adding the desktop is one command. That may be easier than the howto.

---

### Post by kinematic on 2006-07-24
i always go for manual partitioning and the alternate cd so i don't know how the live cd works.....me and my gf are the only ones qualified to partition our hdd's ;) 
but if the live cd formats by default it's a great feature for n00bs ;)
and what i said still applies...never install over another distro or previous install.

---

### Post by Kilz on 2006-07-24
> **kinematic said:**
> i always go for manual partitioning and the alternate cd so i don't know how the live cd works.....me and my gf are the only ones qualified to partition our hdd's ;) 
but if the live cd formats by default it's a great feature for n00bs ;)
I agree on the alternate/manual partition. After having numerous partitions deleted with automatic partitioning, ill never do it that way again.

---

### Post by az on 2006-07-24
> **Kilz said:**
> But the server CD has a lamp install that will setup lamp. Then adding the desktop is one command. That may be easier than the howto.

Either install the desktop (takes 15 minutes) and then run

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server (takes four more minutes)

or install a server (takes forty minutes) and then run

sudo apt-get install ubuntu-desktop (takes another forty minutes)

Both are just as simple.  Using the Desktop cd is faster, though.

---

### Post by Kilz on 2006-07-25
> **azz said:**
> Either install the desktop (takes 15 minutes) and then run

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server (takes four more minutes)

or install a server (takes forty minutes) and then run

sudo apt-get install ubuntu-desktop (takes another forty minutes)

Both are just as simple.  Using the Desktop cd is faster, though.

Why is the server install so much longer? Since it doesnt install a desktop shouldnt it be shorter?

---

### Post by az on 2006-07-25
> **Kilz said:**
> Why is the server install so much longer? Since it doesnt install a desktop shouldnt it be shorter?

Just like the alternate cd install is much longer.  Because each package is unpacked and configured.  The live cd just dumps an already up-and-running system onto your hard drive and does a little tweaking.  It takes only a few minutes longer than just copying files.

Installing each package individually is a lot of disk I/O and running setup scripts.

---

### Post by Kilz on 2006-07-25
> **azz said:**
> Just like the alternate cd install is much longer.  Because each package is unpacked and configured.  The live cd just dumps an already up-and-running system onto your hard drive and does a little tweaking.  It takes only a few minutes longer than just copying files.

Installing each package individually is a lot of disk I/O and running setup scripts.

Thanks, no wonder I didnt notice any difference. The Dapper 64 live cd didnt work on my computer. So I use the alternate.

---


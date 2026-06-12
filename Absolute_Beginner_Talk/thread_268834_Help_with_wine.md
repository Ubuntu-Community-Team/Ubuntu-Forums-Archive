---
title: "Help with wine"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2006-09-30
Ok I have downloaded wine. I have also fiqured out how to extract it. But how do I install it?

Need help. Does anyone have a step by step instuction. Link maybe?

---

### Post by searayman on 2006-09-30
isnt wine in the repos? hold on i will check, and get back to you

---

### Post by aysiu on 2006-09-30
Some basics on how to install and use it:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

Further instructions on use with a specific example and screenshots:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

[quote=searayman]isnt wine in the repos? hold on i will check, and get back to you[/quote] Yes, it's in the Universe repositories.

---

### Post by searayman on 2006-09-30
yea it is so do a "sudo apt-get install wine" type that in a terminal window without the quotes

---

### Post by aysiu on 2006-09-30
> **searayman said:**
> yea it is so do a "sudo apt-get install wine" type that in a terminal window without the quotes
Won't work unless ProjectWhat has the Universe repositories enabled.

ProjectWhat, Ubuntu uses a package manager to install and remove software. If you're unfamiliar with that, read these two links:

**Long, point-and-click-focused explanation with screenshots**:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

**Short, terminal-focused explanation**:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by ProjectWhat on 2006-09-30
It says this when I try to install it:

> admin@admin-desktop:~$ sudo aptitude update
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 4B in 1s (3B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
E: Couldn't rebuild package cache
admin@admin-desktop:~$ sudo aptitude update
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 4B in 1s (3B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
E: Couldn't rebuild package cache
admin@admin-desktop:~$ sudo aptitude install wine
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
admin@admin-desktop:~$


what am I doing wrong? I think I am confused. What post should I go by?

---

### Post by aysiu on 2006-09-30
Sounds as if you have Adept or Synaptic open when you're trying to run *aptitude*.

Only one program at a time can access the *dpkg* package manager.

---

### Post by ProjectWhat on 2006-09-30
ok i think I just installed it using Synaptic. But how where do I get access to wine. Or when I try to install a windows program will it automatically use wine?

---

### Post by aysiu on 2006-09-30
Read these links. I promise you won't regret it.

[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Kilz on 2006-09-30
> **ProjectWhat said:**
> ok i think I just installed it using Synaptic. But how where do I get access to wine. Or when I try to install a windows program will it automatically use wine?

I [wrote a page]("http://www.tghc.org/staticpages/index.php/wine") that may help you understand wine and how to use it.


Edit:Im way to slow posting.

---

### Post by ProjectWhat on 2006-09-30
Ok I got WINE to work. Come to find out I was using it wrong. oops.

---

### Post by ProjectWhat on 2006-09-30
Dreamweaver wont install right. It says something like C:/windows/programs/macromedia/dreamweaver 8 is already installed do you wish to overwrite?

---

### Post by newbie8 on 2006-09-30
I too can't get my Wine to work. What I want is IE6 only. How do I do this.

The winecfg panel pops-up already but when I choose the .EXE files, nothing happens.

what are the steps from the winecfg panel to set up IE6?

Thanks!

---

### Post by newbie8 on 2006-09-30
Is there a specific command line to get IE6 via Wine?

---

### Post by IusedTObeSOMEONEelse on 2006-09-30
I don't know where it is but I used a thing called "wine tools" one time and it set up IE & outlook but I can't recall

---

### Post by kauf on 2006-10-01
Why would you want to run IE?  Blasphemy! Just chill and relax with firefox, spark a doobie if you are so inclined.

---

